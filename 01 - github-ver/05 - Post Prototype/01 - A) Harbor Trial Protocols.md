# Step 3 — Harbor Trial Protocols (Controlled Near-Shore Testing)

Now that the bench/environmental stage has validated the hardware, we move to **harbor trials**. Purpose: collect controlled, high-quality data in calm water with known target placements, to tune detectors, validate probability-weighted search overlays, and measure real-world performance under repeatable conditions.

---

## 3.1 Trial Objectives

- Validate **time-to-first-visual (TTFV)** improvements in realistic but controlled conditions.
- Build a **labeled dataset** of thermal + RGB imagery for detector tuning.
- Quantify **probability of detection (Pdet)**, **false positive rate (FPR)**, and **ROC curves**.
- Test **pilot takeover workflow** and HUD overlays.
- Validate **payload release** (buoy, dye, strobe) in calm conditions.
- Confirm **beaconing accuracy** (CEP ≤ 10 m).

---

## 3.2 Site Requirements

- Calm-water basin or harbor with vessel access.
- Safety boat on standby at all times.
- Depth sufficient for MOB manikin drift (~10–30 m).
- Permission from port authority; PA/crew warnings during live drone ops.
- RF-clear environment (avoid Wi-Fi congestion zones if possible).

---

## 3.3 Test Equipment

- **`CROW` drone system** (1–2 units).
- **Dock** with AC supply, weatherproof mount near deck rail.
- **Bridge Interface Unit (BIU)** with logging enabled.
- **Pilot satchel**: remote, video goggles, spare pack.
- **MOB manikins**: Ruth Lee “Oscar” or equivalent (2–3 units, varied clothing).
- **Safety boat** with crew for placement and recovery.
- **Environmental sensors**: handheld anemometer, thermometer, current meter (if available).
- **Data logging**: GoPros on deck, synchronized clocks, pilot screen recorder, telemetry logs.

---

## 3.4 Run-of-Show (Daily Drill Sequence)

1. **Pre-trial checks:** battery health, payload function test, dock diagnostics.
2. **Place MOB manikin:** quietly deployed from safety boat, distance 50–200 m from vessel, GPS marked. Clothing varied (dark, light, reflective).
3. **Trigger MOB alarm:** bridge initiates, BIU logs timestamp T=0.
4. **Auto-launch + IRD:** drone launches, runs 60–90 s micro-grid (≤200 m).
5. **Pilot takeover:** pilot assumes control via satchel kit, continues probability-weighted search guided by BIU drift model.
6. **Detection event:** log TTFV (seconds from T=0 to first verified detection).
7. **Pilot LOCK & Mark:** drone hovers/beacons; optional buoy/dye drop if trial card specifies.
8. **Safety boat recovers manikin.**
9. **Return-to-dock:** precision landing; recharge cycle.
10. **Debrief & log:** pilot notes, bridge notes, any anomalies.

Repeat **5–10 drills/day** with varying conditions.

---

## 3.5 Variables & Conditions to Test

- **Lighting:** day vs. night (with nav lights background).
- **Clothing:** dark clothing, light clothing, reflective strips.
- **Distance:** 50, 100, 200 m from hull.
- **Orientation:** manikin face-up, face-down, half-submerged.
- **Sea State:** calm harbor water; small chop if conditions allow.
- **Payload:** with vs. without buoy/dye drop.

---

## 3.6 Metrics to Capture

- **Primary:**

  - TTFV (s) vs. baseline (human lookouts).
  - Pdet within 200 m.
- **Secondary:**

  - False positives per minute.
  - Pilot takeover latency (alarm→control, target ≤ 60 s p95).
  - Payload drop CEP (≤10 m drift).
  - Beacon CEP (≤10 m hold).
- **Exploratory:**

  - Detector ROC/AUC from labeled frames.
  - Pilot workload (NASA-TLX).
  - HUD usefulness feedback.

---

## 3.7 Test Cards (example format)

**Test Card ID:** HARBOR-03
**Objective:** Night detection, dark clothing, 100 m placement
**Manikin:** Oscar, black coverall
**Placement:** 100 m, starboard beam, GPS logged
**Expected outcome:** TTFV < 60 s; ROC threshold validated
**Result fields:** TTFV (s), detection confidence, FPR, pilot comments

---

## 3.8 Acceptance Thresholds (Harbor Stage)

- Median TTFV < 60 s in calm conditions.
- Pdet ≥ 0.9 within 200 m.
- FPR ≤ 0.2/min at VERIFY threshold.
- Pilot takeover ≤ 60 s (p95).
- Payload release ≥ 95 % success in calm water.
- Beacon hover CEP ≤ 5 m.

---

## 3.9 Records & Deliverables

- **Raw logs:** telemetry, video (thermal + RGB), bridge BIU log.
- **Synced video reels:** side-by-side drone HUD + GoPro deck view.
- **Dataset:** labeled frames for IR/RGB detector training.
- **Harbor Trial Report:** metrics table, ROC curves, plots of TTFV distributions.
- **Lessons learned:** SOP refinements, HUD tweaks.

---

## 3.10 Sources

- Ruth Lee “Oscar” manikin specifications for MOB drills.
- USCG MOB drill guidance and probability-of-detection emphasis.
- Thermal/RGB detection fusion in maritime conditions.
- SOLAS/ISO 21195 expectations for detection integration.

---

✅ With harbor trials, you get controlled, repeatable evidence, ROC curves, and dataset capture before committing to the complexity of open-sea tests.

Do you want me to move next into **Step 4 — Open-Sea Trial Protocols** (full MOB drills with ship maneuvers, sea state variability, and class/insurer witnesses)?
