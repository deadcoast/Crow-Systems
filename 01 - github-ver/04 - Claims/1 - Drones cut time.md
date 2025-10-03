# CLAIM — “Drones cut time-to-first-visual (TTFV) dramatically.” #

## A. Rationale from independent literature (triangulated) ##

1. **Early-minute medical risk**
   Cold-water immersion triggers the **cold-shock response** within the **first minute** (rapid hyperventilation, arrhythmias, loss of breathing control), creating a narrow survival window before swim-failure and hypothermia phases. Peer-reviewed sources (systematic reviews and foundational texts) identify this early window as the decisive period for rescue. ([ScienceDirect][1])

2. **Doctrine emphasizes rapid *visual* reacquisition**
   IAMSAR (Vol. III) and USCG’s “Theory of Search” frame search effectiveness as **POS = POC × POD** and drive operators to obtain a **first visual** quickly by maximizing coverage where probability is highest. UAVs provide rapid, directed coverage of the near-ship probability plume immediately after the datum is set. ([Maritime Safety Innovation Lab LLC][2])

3. **Real-world demonstrations of aerial “find/mark”**
   The Royal Navy reports **man-overboard trials** where **remotely-piloted systems located personnel in the water, dropped life-saving equipment, and hovered as a beacon** until recovery—direct evidence that pilot-in-the-loop drones achieve rapid visual reacquisition and position hold in MOB scenarios. ([Royal Navy][3])

4. **Rescue assets are mandated but launch takes non-zero time**
   SOLAS Chapter III requires **rescue boats be in continuous readiness and launchable in not more than 5 minutes**; drills and readiness standards are codified, yet those minutes—plus maneuvering—are exactly when aerial visual reacquisition can be achieved and a position marked. ([PUC][4])

**Conclusion (literature):** Aerial, pilot-controlled search placed immediately after an MOB alarm is consistent with SAR doctrine, matches medical urgency, and is demonstrated in practice; this should compress **TTFV** relative to ship-only baselines.

---

## B. Measurement strategy (multi-method, auditable) ##

### B1. Bench & timeline audit (prior to drills) ##

- **Alarm-to-air latency**: log auto-launch time from MOB alarm → wheels-up (target: ≤90 s).
- **Glass-to-glass latency**: end-to-end video delay measured with time-code overlay to bound pilot reaction timing.
- **Geo-mark latency**: time to first valid GPS fix over the search area.

(These establish an upper bound on best-case TTFV before environmental effects; reported as medians with IQR; clocks synchronized via GNSS/NTP.)

### B2. Controlled **A/B shipboard drills** (primary evidence) ##

- **Design**: randomized **paired drills**: **A = baseline** (standard ship MOB response, no UAV); **B = with UAV** (auto-launch IRD ≤90 s/≤200 m then pilot control). Pair each A with a B under similar light/sea state; randomize order each day.
- **Witnessing**: at least one day **witnessed by class society surveyor or maritime test lab**; witness signs time-stamped drill sheets; immutable **hash manifests** of telemetry/video issued.
- **Metrics**:

    - **TTFV** (s): alarm → first verified visual (any source in A; UAV or crew in B).
    - **Time-to-GPS-fix** (s) at casualty position (B).
    - **Time-to-buoy-drop** (s) when specified.
    - **Time-to-handoff** to rescue boat (s).
    - **Context**: WMO **Sea State code** and **Beaufort** for each run (to normalize POD). ([NCAC News][5])

### B3. Controlled **harbor drills** (supporting evidence) ###

- Night/day, varied clothing/contrast; yields ROC curves for detector thresholds and establishes per-altitude **pixels-on-target** bands (per Johnson/IFOV; used to pre-set night altitudes). ([Maritime Safety Innovation Lab LLC][2])

### B4. **Audited data pack** ###

- Synchronized **RGB + LWIR** video, telemetry (GPS/altitude/attitude), alarm timestamps, pilot inputs; SHA-256 hash ledger; signed witness statements.

---

## C. Statistical analysis plan (pre-registered; binder-ready) ##

### Endpoints ###

- **Primary**: Paired difference in **TTFV (seconds)**, B – A, across all drills; day and night strata.
- **Secondary**: Time-to-GPS-fix; Time-to-buoy-drop; Time-to-handoff; effect persistence across sea-state strata (≤SS5 vs >SS5 excluded/flagged).

### Hypotheses ###

- **H1 (Night)**: median TTFV(_B) ≤ **0.40 ×** median TTFV(_A) (≥60% reduction).
- **H2 (Day)**: median TTFV(_B) ≤ **0.60 ×** median TTFV(_A) (≥40% reduction).

### Tests ###

- **Paired non-parametric** (Wilcoxon signed-rank) on TTFV; report **Hodges-Lehmann** median difference with **95% CIs**.
- **Bootstrap (10k resamples)** for ratio-of-medians and CI.
- **Sensitivity**: stratified by light (day/night) and sea state (SS 0–5), with interaction check.

### Multiplicity ###

- Familywise control via pre-specified primary (night) and key secondary (day); others descriptive.

### Missing data ###

- Pre-declared rules: drill aborts (wind > platform envelope, RF loss, traffic) documented and excluded from primary; listed with reasons.

---

## D. Sample size & power (worked example) ##

Assume (conservative) **baseline night TTFV** median = **18 min** (ship-only), **IQR** 12–28; target **60% reduction** → **7.2 min** median with UAV. With **paired-design**, **ρ ≈ 0.4** correlation, **α = 0.05**, **power 0.9**: approximately **n ≈ 20 paired night drills** detect the effect with Wilcoxon-approximation power (plus **n ≈ 20 day pairs** for the 40% target). (Final n refined after pilot day using observed variance/ρ; pre-registration will state this rule.)

---

## E. Data collection instruments (ready to insert) ##

### E1. Drill sheet (extract) ###

- Case ID / Date / Light (Day/Night) / Sea State (WMO) / Beaufort / Wind dir–spd / Current est.
- Alarm (T_0) (UTC) / UAV wheels-up / First UAV visual / First **any** visual / GPS-fix time / Buoy-drop time / Handoff time / Recovery time.
- Notes (detections missed/false-positives; RF margins).
  (Sea-state & Beaufort references standardize environmental fields.) ([NCAC News][5])

### E2. Witness statement (extract) ###

- Organization / Name / Credential / Date & time span observed / Drill IDs witnessed; statement: “Observed synchronization of clocks; verified alarm times; confirmed TTFV adjudication process; reviewed hash manifest of logs; no material deviations from protocol.”

### E3. Pre-registration header (methods language) ###

“Paired A/B randomized MOB drills will be conducted on [vessel]; **Primary endpoint = TTFV (s)**. **B** condition includes auto-launch initial response (≤90 s, ≤200 m) then pilot-controlled search; **A** = ship SOP, no UAV. **Analysis**: paired Wilcoxon, HL median difference, bootstrap 95% CI; **success** if median TTFV reduction ≥60% at night and ≥40% by day across ≥20 pairs. Environmental covariates: WMO Sea State, Beaufort. Abort rules pre-declared.”

---

## F. External anchors cited in the dossier ##

- **Royal Navy MOB drone trials**—“**Remotely-piloted systems which locate personnel in the water, drop life-saving equipment and hover over the location until rescuers arrive**.” (Used as operational precedent for the role measured here.) ([Royal Navy][3])
- **USCG search theory (POD/POC/POS)**—formal basis for prioritizing early visual reacquisition. ([Navigation Center][6])
- **IAMSAR Vol. III**—mobile-facility search patterns, definitions, and usage; cited to justify coverage factor and reporting format. ([Maritime Safety Innovation Lab LLC][2])
- **SOLAS Ch. III / LSA**—**rescue boats launchable ≤5 min**; clarifies why an aerial first-visual during those minutes is safety-relevant. ([PUC][4])
- **Cold-shock literature**—justifies the magnitude-of-benefit bar for earlier visual reacquisition. ([ScienceDirect][1])

---

## G. Reporting templates (drop-in) ##

### G1. Primary results table (night) ###

| Metric                  | Baseline A (median, IQR) | UAV B (median, IQR) | Paired Δ (HL est., 95% CI) | p-value |
| ----------------------- | -----------------------: | ------------------: | -------------------------: | ------: |
| **TTFV (min)**          |                        — |                   — |                          — |       — |
| Time-to-GPS-fix (min)   |                        — |                   — |                          — |       — |
| Time-to-buoy-drop (min) |                        — |                   — |                          — |       — |
| Time-to-handoff (min)   |                        — |                   — |                          — |       — |

### G2. Forest plot elements (pre-specified strata) ###

- Night overall; Day overall; Sea State ≤3 vs 4–5; With/without buoy-drop card. (Same endpoint, paired Δ with 95% CI.)

### G3. Protocol deviations & aborts log ###

- Drill ID / Reason (wind > spec; traffic; RF margin) / Phase / Disposition.

---

## H. Success criteria (pre-declared) ##

- **Night**: median **TTFV reduction ≥60%** (B vs A) across **≥20 pairs**; significance by paired Wilcoxon and bootstrap 95% CI excluding 0.
- **Day**: median **TTFV reduction ≥40%** across **≥20 pairs**; same statistical confirmation.
- Robustness: effect persists when restricted to **Sea State ≤5** and when excluding witnessed-day drills (to check Hawthorne effects).

---

## I. Why this satisfies “multiple independent evidence types” ##

- **Literature**: medical urgency (cold-shock), SAR doctrine (IAMSAR/USCG), operational precedent (Royal Navy) → independent textual evidence. ([ScienceDirect][1])
- **Bench tests**: instrumented latency audits → engineering evidence.
- **Controlled drills (harbor + ship A/B)**: experimental evidence with pre-registration → causal inference on TTFV.
- **Witnessed sea trials**: third-party validation → external credibility.
- **Audited data**: hashed telemetry/video → tamper-evident archival.

---

### Source list (for this claim) ###

- **IAMSAR Manual, Vol. III (Mobile Facilities)**—search patterns; definitions. ([Maritime Safety Innovation Lab LLC][2])
- **USCG, “The Theory of Search — A Simplified Explanation”**—POD/POC/POS. ([Navigation Center][6])
- **Royal Navy** official news: **MOB drone trials** (locate, drop, hover). ([Royal Navy][3])
- **SOLAS Ch. III / LSA** readiness: **rescue boats ≤5 min** to launch. ([PUC][4])
- **Cold-shock/immersion** reviews and studies (risk concentrated in first minutes). ([ScienceDirect][1])

**Ready for insertion** into the business plan and trials binder as the **Claim-1 research section**.

[1]: https://www.sciencedirect.com/science/article/pii/S0306456523003169 "Habituation of the cold shock response: A systematic ..."
[2]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2021/02/Doc.9731-EN-IAMSAR-Manual-International-Aeronautical-and-Maritime-Search-and-Rescue-Manual-Volume-III-Mobile-Facilities.pdf "IAMSAR MANUAL"
[3]: https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"
[4]: https://puc.overheid.nl/nsi/doc/PUC_1346_14/3/ "Chapter III Life-saving appliances and arrangements"
[5]: https://news.ncac.mn/uploads/bookSubject/2022-11/637b02e0c30d7.pdf "VOLUME I"
[6]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf "The Theory of Search - A Simplified Explanation - navcen"
