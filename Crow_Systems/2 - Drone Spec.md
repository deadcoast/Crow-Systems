
# Drone Specifications

## B1. System goals

* **T1: Time-to-first-visual (TTFV)** ≤ 90 s from MOB alarm in benign conditions (Sea State ≤ 3).
* **Pdet: Detection probability** ≥ 0.8 inside the first sortie’s search area.
* **FPR: False positive rate** ≤ 0.2/min with human-in-loop verification.
* **CEP (beaconing):** ≤ 10 m 95% while hovering over the target in Beaufort 5.
* **Latency:** Video/HUD < 150 ms; detector→HUD marker < 250 ms.

---

## B2. Core dataflow

MOB Alarm → BIU → Dock/Drone → Pilot (HUD)

1. **MOB alarm** (bridge): BIU captures `LKP` (lat/lon/time), ship heading/speed, wind (AWS/AWA), and nearest current estimate.
2. **Auto-launch + IRD:** Drone takes off, flies to LKP, runs a **strictly bounded micro-grid** (60–120 s and ≤ 200 m radius).
3. **BIU Drift Model** runs in parallel (see B3) and yields a **probability density map (PDM)** around LKP.
4. **Pilot takes control** (preempts IRD).
5. **HUD overlays**: PDM heatmap, expanding square/sector arcs, “windage arrow,” candidate detections (IR/RGB), and “drop-point” guides.
6. **Pilot flies the pattern** (assisted stabilization only); detections escalate to “VERIFY” with a two-stage confirm.

---

## B3. Drift & probability model (SAR-style, Monte Carlo)

MOB as a drifting object driven by surface current + a fraction of wind (windage), plus random dispersion:

$$
\mathbf{x}(t)=\mathbf{x}*0+\int_0^t \left(\mathbf{V}*{\text{current}}(\tau)+\alpha,\mathbf{V}_{\text{wind}}(\tau)\right),d\tau + \mathbf{\epsilon}(t)
$$

* $(\mathbf{x}_0)$: LKP (from MOB trigger)
* $(alpha)$: **windage coefficient** (typ. 0.02–0.04 for a head/upper torso at surface; configurable).
* $(mathbf{\epsilon}(t))$: random walk term modeling turbulence and uncertainty (Gaussian with covariance growing with time; add heavier tails in rough seas).

**Monte Carlo ($N$ particles):**

* Initialize $N$ particles at LKP with small spatial jitter (e.g., $σ = 10–30 m$).
* For each time step $Δt$ (e.g., $1–2 s$), propagate particles with current + $α·wind$ + random diffusion ($σ_drift$ per axis).
* After T minutes, histogram particle positions → **$PDM$** (probability density map).
* **Confidence ellipses** (e.g., 50/80/95%) and **centroid vector** are computed for the HUD.

**Inputs:**

* Ship’s anemometer for wind; onboard or forecast currents (fallback: default surface current = 0.3–0.5 m/s in open water; configurable).
* If no current data: inflate diffusion to avoid overconfidence.

**What the Pilot Sees:** a heatmap “blob” drifting downwind/down-current with overlaid confidence rings and an “arrow tail” showing expected displacement over the next 2–5 minutes.

---

## B4. Search pattern math

### B4.1 Initial patterns (IRD auto segment)

* **Expanding square** centered on LKP with leg length (L) and growth (\Delta L).

  * Choose (L) so that sensor **swath** (w) overlaps ~30–50% (for thermal + RGB).
  * Example: If (w=20) m, set (\Delta L=10)–15 m to keep coverage tight.
* **Time cap:** hard stop at 60–120 s or radius cap (≤ 200 m).

### B4.2 Pilot patterns (manual)

* **Probability-weighted expanding square:** same geometry, **centered on PDM centroid**, not the raw LKP.
* **Sector sweep:** center on centroid, span the **down-wind/down-current sector** first (e.g., ±45° around resultant vector), then fill remaining sectors.
* **Lawnmower (lateral sweep):** if the confidence ellipse is elongated, align lanes with the major axis.

**Coverage math (to size the lanes):**
Coverage rate (C = v \cdot w) (area per second).

* (v): pilot airspeed over ground (m/s).
* (w): effective detection swath at the chosen altitude.
* **Lane spacing** (s = k \cdot w), where (k \in [0.5, 0.8]) for desired overlap.

  * Tighter (k=0.5) in rough seas/night; looser (k=0.8) in calm daylight.
* **Altitude trade:** higher altitude ↑w but ↓thermal resolution; HUD suggests an altitude band that maximizes (C) without degrading IR detection confidence (see B7).

---

## B5. Detection stack (IR-first, RGB-verify; pilot always confirms)

**Sensors:** LWIR 640×512 @ 30–60 Hz + RGB 1080p/60 (live) / 4K record.

**Pipeline:**

1. **Thermal pre-processing:** local contrast normalize (AGC), temporal median filter to dampen foam flicker.
2. **IR detector:** lightweight, thermally trained CNN/YOLO-variant; threshold low (recall-biased).
3. **Candidate gating:** eliminate blobs by **area**, **aspect**, **temperature delta** vs. local background, and **motion continuity** across frames.
4. **RGB verify:** crop ROI in RGB stream; run a tiny classifier (yes/no “head/shoulders in water”) + color heuristics (skin tones ± clothing bright elements).
5. **mmWave fusion (optional):** if radar pod present, require **co-located return** within 3–5 m for “strong” flag in heavy spray.
6. **Confidence score** (S\in[0,1]) from weighted fusion (IR>RGB>mmWave).
7. **Escalation states:**

   * **PING** (S≥0.4): HUD shows small yellow marker; muted chirp.
   * **ALERT** (S≥0.6): orange marker + on-screen arrow cue to turn; BIU logs.
   * **VERIFY** (S≥0.75): red marker + “HOLD/BEACON?” prompt for pilot; requires **pilot tap-confirm**.
   * **LOCK** (pilot confirmed): Drone enters assisted hover mode (pilot can still fly), beacons enabled; **buoy drop** becomes available (two-stage confirm).

---

## B6. Tracking: keeping the target “in frame” while the pilot flies

**Problem:** water clutter causes intermittent detections; we need robust state estimation.

**Solution:** **Interacting Multiple Model (IMM) Kalman Filter** or **Particle Filter** for short-horizon surface target tracking.

* **State:** 2D position ((x,y)), velocity ((\dot{x},\dot{y})).
* **Process model:** constant-velocity perturbed by drift (small random acceleration; tune Q).
* **Measurement:** pixel/geo coordinates from IR/RGB detections; include per-measurement covariance from detector confidence.
* **IMM modes:** (1) nearly-stationary (treading water), (2) drift with current, (3) brief occlusion. The filter blends modes by likelihood.
* **Output:** **best-estimate position + velocity + covariance ellipse** @ 10–30 Hz → drives:

  * HUD **lead-box** (a little square ahead of the last detection),
  * **aim-assist gimbal** (keeps ROI centered while pilot flies),
  * **beacon offset** (maintain 10–20 m offset upwind of target when LOCKed).

**Re-acquisition rule:** if detections drop for > (T_{\text{lost}}) (e.g., 3 s), the HUD paints a **search micro-spiral** around last estimate while the filter expands covariance; pilot gets a “suggested turn” chevron.

---

## B7. Altitude & swath guidance

At runtime, suggest an altitude band (h) that maximizes **probability of detection per minute**, not just swath:

* Empirical relation: (w(h)) increases with h (wider view), but **thermal separability** drops beyond a threshold as human pixels get small.
* Maintain a **minimum pixel footprint** (e.g., ≥ 10–15 pixels across the head/shoulders) for the IR detector to remain robust.
* **HUD cue:** “Climb +10 m (↑ coverage)” or “Descend −8 m (↑ IR confidence).” Pilot chooses.

---

## B8. Beaconing, buoy, and markers (pilot-commanded)

* **LOCKed target:**

  * **Assisted hover** engages (pilot override always available).
  * **Strobes:** visual + IR (1–4 Hz).
  * **GPS spam:** 1–2 s updates to BIU; ECDIS waypoint auto-updates.
* **Buoy drop:** two-stage confirm; HUD suggests **drop-point** slightly **upwind/up-current** so the buoy drifts *to* the casualty.
* **Dye/smoke:** pilot-gated; smoke auto-locked out above Beaufort 4.

---

## B9. State machine in YAML

```yaml
[MOB_TRIGGER]
   -> AUTO_LAUNCH
   -> IRD (timer & radius caps)
   -> {Pilot_Takeover anytime} -> PILOT_CTRL

[PILOT_CTRL]
   - SEARCH (patterns with PDM overlay)
   - DETECT (PING/ALERT/VERIFY)
   - LOCK (assisted hover, beacons on)
   - DROP (buoy/dye if commanded)
   - HANDOFF (maintain lock until rescue on-scene)
   - RTB (precision dock)

[FAILSAFE]
   - Link lost -> Hover + climb + BIU alert -> RTB after timeout
```

---

## B10. Python Module Base

### B10.1 Drift Monte Carlo (BIU)

```python
def MC_drift(LKP, wind_vec, current_vec, alpha=0.03, N=5000, dt=1.0, T=600.0):
    # LKP: (lat, lon) -> convert to local ENU (x0, y0)
    particles = jitter_around(LKP_ENU, sigma=20.0, N=N)
    for t in np.arange(0, T, dt):
        V = current_vec(t) + alpha * wind_vec(t)
        noise = np.random.normal(0, sigma_drift(dt), size=(N,2))
        particles += V*dt + noise
    PDM = histogram2D(particles, bins=grid_spec)
    ellipses = confidence_ellipses(particles, levels=[0.5,0.8,0.95])
    centroid = particles.mean(axis=0)
    return PDM, ellipses, centroid
```

### B10.2 Detector fusion (onboard)

```python
def detect_fuse(thermal_frame, rgb_frame):
    ir_cands = ir_detector(thermal_frame)            # boxes + scores
    fused = []
    for b, s_ir in ir_cands:
        roi_rgb = crop(rgb_frame, b.expand(margin=0.3))
        s_rgb = rgb_classifier(roi_rgb)              # 0..1
        s = 0.65*s_ir + 0.35*s_rgb                   # weights tunable
        if passes_shape_temp_filters(b, thermal_frame):
            fused.append((b, s))
    return fused
```

### B10.3 IMM/Tracker update

```python
def tracker_step(fused_dets, tracker):
    if fused_dets:
        z, R = choose_best_measurement(fused_dets)   # by score
        tracker.update(z, R)                         # IMM or PF
    else:
        tracker.predict()
    return tracker.state(), tracker.cov()
```

### B10.4 HUD loop (pilot)

```python
while mission_active:
    PDM, ellipses, centroid = get_PDM()
    draw_heatmap(PDM); draw_ellipses(ellipses)
    dets = detect_fuse(thermal, rgb)
    state, cov = tracker_step(dets, tracker)
    draw_target_markers(dets, state, cov)
    suggest_altitude_band(sensor_model, state)
    if pilot_confirms_lock(): enable_beacons()
    if pilot_confirms_drop(): release_buoy_at(predicted_updrift_point(state))
```

---

## B11. Tuning & defaults

* **IRD:** 90 s, max radius 200 m, leg ΔL = 12 m, speed 10 m/s.
* **Windage α:** 0.03 (raise in strong wind).
* **Dispersion σ_drift:** start 0.4–0.8 m/s equivalent; scale with sea state.
* **Lane spacing k:** 0.6 at night/rough; 0.75 day/calm.
* **Detector thresholds:** PING 0.4, ALERT 0.6, VERIFY 0.75 (adjust by ROC).
* **Lost target timeout (T_{\text{lost}}):** 3 s (night) / 2 s (day).

---

## B12. Edge cases & behaviors

* **Multiple candidates:** show numbered markers; pilot can cycle priorities; tracker can fork hypotheses (MHT) for 3–5 s.
* **Glare/sun angle:** HUD prompts “crab left/right” to move specular off FOV; RGB weight auto-reduced.
* **Heavy rain/spray:** IR weight ↑, RGB weight ↓; if mmWave present, require co-return for VERIFY.
* **Near-hull RF shadow:** predefine **control points** with RF coverage; HUD warns if link margin drops.
* **Extreme winds:** HUD suggests **marker-drop only** then climb to safer hover; keep CEP within envelope.

---

## B13. Test metrics

* **TTFV** (seconds) across day/night and sea states.
* **Pdet vs. range** (0–600 m) and **ROC curves** per sensor mode.
* **FPR** (per minute) by condition.
* **Tracker continuity** (% time with valid estimate) and **reacquisition time**.
* **Pilot workload** (NASA-TLX) to ensure overlays help, not hinder.
* **Beacon CEP** under wind gust profiles.

---

## B14. Deliverables for the build

* **Sensor model tables:** altitude→swath (w(h)), IR pixel footprint vs. range, recommended (k) lane spacing curves.
* **Detector training set:** night/day maritime data (annotated heads/shoulders in waves, with negative examples for foam/kelp).
* **Parameter file (.yaml):** IRD caps, α, σ_drift tables by sea state, thresholds, alerts.
* **HUD spec:** color codes, symbology, annunciations, confirm dialogs (two-stage for drops).
* **Benchmarks:** scripts to compute TTFV/Pdet/FPR on recorded trials for regression over time.

---
