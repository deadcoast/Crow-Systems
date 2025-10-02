# Step 4 — Open-Sea Trial Protocols (official ship drills)

Purpose: prove—in real conditions at sea—that `CROW` (auto-launch IRD ➜ pilot control) **cuts time-to-first-visual**, maintains **high detection probability** with **manageable false positives**, and **improves localization/marking** compared to baseline MOB procedures. Protocol aligns with SOLAS/LSA practice and the emerging ISO 21195 environment for overboard detection systems. ([International Maritime Organization](https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"))

---

## 4.1 Trial design (A/B, witnessed)

- **Design:** randomized, **paired A/B drills**:
    
    - **$A$ = Baseline** (ship runs its standard MOB drill; no drone).
    - **$B$ = `CROW`** (auto-launch IRD capped at $90s/≤200 m$, then pilot in command).  
        Each “$A$” has a matched “$B$” under similar light/sea state; order randomized per day to limit bias.
        
- **Witnessing:** At least **one class society/insurer witness day**; witness signs time-stamped drill sheets and receives immutable logs (hashes). Use class/insurer because they recognize SOLAS/LSA practice and ISO 21195 context for overboard systems. ([TÜV SÜD](https://www.tuvsud.com/en-us/services/testing/iec-60945?utm_source=chatgpt.com "IEC 60945 Testing & Certification"))
    
- **SAR-consistent drift modeling:** BIU runs a lightweight **Monte-Carlo drift (SAROPS-style)** to feed a probability map overlay for the pilot; we will report it explicitly because SAROPS is the USCG’s operational search planner and sets expectations for probability-guided effort. ([U.S. Coast Guard](https://www.dco.uscg.mil/Portals/9/CG-5R/SARfactsInfo/SAROPSInforSheet.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System (SAROPS)"))
    

---

## 4.2 Test area & safety

- **Area:** coastal route with room for controlled turns and boat launch; radio coordination with VTS/Port Authority; exclusion zone declared.    
- **Ship condition:** typical cruise speed before drill (10–15 kt) to ensure realistic wake; drills run during scheduled windows.
- **Rescue craft:** ship’s designated rescue boat(s) on immediate standby per SOLAS/LSA procedures (we measure when they actually deploy—baseline vs with drone guidance). ([International Maritime Organization](https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"))
- **Targets:** 2–3 **Ruth Lee “Oscar” MOB manikins**—adult & youth variants—to simulate 45° head/shoulders float posture; reflective tape and optional strobe mounts used at night. ([ruthlee.com](https://www.ruthlee.com/manikin/man-overboard-training-manikins-dummies?utm_source=chatgpt.com "Man Overboard Training Manikins | Ruth Lee Ltd"))
    

---

## 4.3 Scenarios & conditions matrix

Run ≥ 20 paired drills across these axes:

- **Light:** day / nautical-night (no twilight bias).    
- **Sea state:** 2–5 (record wind & wave height); include **moving-ship launches** (3–5 kt headway) to reflect LSA/real practice. ([International Maritime Organization](https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"))
- **Placement:** 150 m, 300 m, **600 m down-drift** from LKP (safety boat silently deploys); headings upwind, downwind, cross-wind.
- **Clothing/contrast:** dark vs light; reflective strips; partially submerged orientation.
- **Aids:** with/without buoy/dye/strobe (pilot-commanded) to quantify aid benefit.

---

## 4.4 Run-of-show per drill

1. **Pre-brief** (bridge, pilot, rescue crew, witness): objectives, comms, abort criteria.
2. **Target deploy:** safety boat places manikin silently at pre-set vector/range; logs GPS.
3. **MOB alarm (T=0):** bridge hits alarm; BIU time-stamps LKP; deck spotters begin standard procedures.
4. **A or B path executes** (randomized):
    - **A (Baseline):** ship maneuvers as per SOP; rescue boat sequence per normal timing; bridge records “first visual” by any means.
    - **B (`CROW`):** dock auto-launch; **IRD** (≤ 90 s/≤ 200 m cap); **pilot takeover ≤ 60 s p95** goal; probability map overlay visible on pilot HUD (SAROPS-style drift). If verified detection, pilot **LOCKs** and may **drop buoy/dye** per card, then beacon/mark until boat arrives. ([U.S. Coast Guard](https://www.dco.uscg.mil/Portals/9/CG-5R/SARfactsInfo/SAROPSInforSheet.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System (SAROPS)"))
5. **Recovery:** safety boat recovers manikin; record exact time/position.
6. **Debrief:** pilot notes, bridge/witness notes; export hashed logs.

---

## 4.5 Measurements (primary/secondary/exploratory)

- **Primary endpoints**
    
    - **TTFV (s):** alarm → first **verified** drone/crew visual (paired A vs B).
    - **Pdet:** probability of detection within **first sortie radius** (≤ 600 m).
        
- **Secondary**
    - **FPR (min⁻¹):** false positives at VERIFY threshold (night/day, by sea state).
    - **Pilot takeover latency:** alarm → “pilot-in-command” on BIU (p95 ≤ 60 s).
    - **Buoy drop accuracy (CEP):** distance drift-corrected to casualty (≤ 10 m, 95%).
    - **Beacon CEP:** hover position error over target in Beaufort 5 (≤ 10 m, 95%).
    - **Rescue boat vectoring:** time from TTFV to boat on-scene at casualty fix (informational; shows interoperability with LSA practice). ([International Maritime Organization](https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"))
        
- **Exploratory**
    
    - **ROC/AUC** of IR-first, RGB-verify detector at sea (builds on harbor ROC).
    - **Probability-guided search benefit:** TTFV with vs without PDM overlay (subset).

Themetrics reflect survivability drivers (minutes matter), recognized SAR planning practice (probability-guided search), and integration with SOLAS/LSA procedures and ISO 21195-type systems (detection + response). ([Metron](https://www.metsci.com/wp-content/uploads/2019/08/Search-and-Rescue-Optimal-Planning-System.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"))

---

## 4.6 Instrumentation & data integrity

- **Timing:** all systems NTP/GNSS synchronized; independent stopwatch by witness.
- **Telemetry/video:** thermal + RGB streams, GPS, HUD events, control link stats; **hash-chained** after each drill and given to witness (read-only).
- **Env sensors:** true/apparent wind, SOG/COG, wave observations; currents if available.
- **Rescue logs:** boat launch time, on-scene time, position.
- **Standards posture:** bridge-adjacent electronics staged to **IEC 60945** environmental/EMC expectations; this reassures class/insurer on integration while acknowledging `CROW` is auxiliary equipment. ([IEC Webstore](https://webstore.iec.ch/en/publication/3959?utm_source=chatgpt.com "IEC 60945:2002"))

---

## 4.7 Acceptance thresholds (open-sea)

- **Median TTFV reduction ≥ 50% overall; ≥ 60% at night** (B vs A).
- **Pdet ≥ 0.8** within the first-sortie footprint (≤ 600 m) across sea states 2–5.
- **FPR ≤ 0.2/min** at VERIFY threshold (pilot-confirmed).
- **Pilot takeover p95 ≤ 60 s;** command preempt < 300 ms (lab-verified earlier).
- **Buoy CEP ≤ 10 m (95%);** **Beacon CEP ≤ 10 m (95%)** in Beaufort 5.
- **Launch reliability ≥ 99%** across all B-drills (ties back to bench cycle testing).

Stat plan: paired A/B **Wilcoxon signed-rank** for TTFV; bootstrap CIs for Pdet/FPR/CEPs; pre-registered to avoid post-hoc bias; SAROPS-style overlays documented in methods for reproducibility. ([Metron](https://www.metsci.com/wp-content/uploads/2019/08/Search-and-Rescue-Optimal-Planning-System.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"))

---

## 4.8 Risk controls & aborts

- **Abort if:** wind beyond pilot envelope, RF margin < safe threshold, traffic conflict, deck safety call.
- **IRD hard caps enforced** (time/radius); **buoy/smoke/dye = pilot-only** gated actions; no autonomy beyond IRD (documented for witness).
- **Passenger separation:** roped-off deck arcs; PA notice.
- **MOB manikins** only; no live swimmers.

---

## 4.9 Documentation to produce

- **Open-Sea Trial Report:**
    - Methods with **SOLAS/LSA & ISO 21195** alignment notes; sea-state tables; scenario matrix; stats results; limitations.
    - **TTFV distribution plots**, **ROC curves**, **CEP plots**, and **case studies** (night find with buoy drop).
- **Witness packets:** signed drill sheets, hash manifests, copy of raw logs.
- **Operator SOP updates:** tweaks to launch corridor, pilot control points, radio brevity.
- **Class/insurer cover memo:** highlights auxiliary role, IEC 60945 environmental posture, ISO 21195 context, and quantitative benefit vs baseline. ([IEC Webstore](https://webstore.iec.ch/en/publication/3959?utm_source=chatgpt.com "IEC 60945:2002"))

---

## 4.10 Source backbone (for reviewers)

- **SOLAS Chapter III** (life-saving appliances; rescue-boat & launch expectations). ([International Maritime Organization](https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"))
- **ISO 21195:2020** (technical requirements for overboard detection systems; non-wearable). ([ISO](https://www.iso.org/standard/76051.html?utm_source=chatgpt.com "ISO 21195:2020 - Ships and marine technology"))
- **USCG SAROPS** (Monte-Carlo/particle model for probability-guided search). ([U.S. Coast Guard](https://www.dco.uscg.mil/Portals/9/CG-5R/SARfactsInfo/SAROPSInforSheet.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System (SAROPS)"))
- **Ruth Lee “Oscar” MOB manikins** (45° head/shoulders float posture; training standard). ([ruthlee.com](https://www.ruthlee.com/manikin/man-overboard-training-manikins-dummies?utm_source=chatgpt.com "Man Overboard Training Manikins | Ruth Lee Ltd"))
- **IEC 60945** (marine environmental/EMC expectations for bridge-adjacent equipment). ([IEC Webstore](https://webstore.iec.ch/en/publication/3959?utm_source=chatgpt.com "IEC 60945:2002"))

---