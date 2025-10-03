# Evidence Pack — UAV First-Response for Man-Overboard (MOB) Detection & Marking #

## Executive summary ##

- Commercial drones carrying thermal + RGB sensors can **materially cut time-to-first-visual** of a person in the water compared with ship-only search. A conservative analytic model (using DJI H20T thermal DFOV 40.6°, 640×512, and a 15 m/s search speed) shows one UAV can sweep a 600 m radius sector in ~22 min at 120 m AGL; two UAVs halve that. Calculations and assumptions are detailed below with camera and airframe specs cited. ([DJI Download Center][1])
- **Thermal detection performance** for waterborne persons has peer-reviewed support: a 2024 study achieved **85.49% accuracy at 23.51 FPS** for nighttime detection of people in water using thermal imagery and deep learning, demonstrating real-time feasibility on embedded platforms.
- **Real-world SAR use** is corroborated by operational trials: the **Royal Navy** tested drones that locate a MOB, **drop life-saving kit and hover to mark the position**, explicitly for man-overboard scenarios.
- MOB events are not rare: among 2009–2019 oceangoing cruise operations, **212 overboard incidents** were recorded, with **48 rescues** (≈28%). Faster localization has obvious survival implications.

---

## 1) Baseline: incidence, physiology, and search planning ##

**Incidence on cruise vessels.** The CLIA-commissioned independent review (G.P. Wild) documents **212 overboards and 48 rescues** over 2009–2019. This establishes the problem scale and the value of minutes saved in initial location.

**Cold-shock window.** Within the **first 1–5 min** of sudden cold-water immersion, involuntary gasping, hyperventilation and arrhythmias elevate drowning risk; later stages include swimming failure and hypothermia. These timelines underscore why time-to-first-visual (TTFV) is critical. ([U.S. Coast Guard][2])

**Search doctrine.** U.S. Coast Guard SAR planning uses **SAROPS**, a Monte-Carlo particle model to generate drift probability maps and allocate search effort—framework compatible with drone-led rapid localization and marking. ([U.S. Coast Guard][3])

---

## 2) What ships already have (detection & rescue context) ##

**Onboard overboard-detection standardization.** **ISO 21195:2020** defines **performance requirements for *non-wearable* person-overboard detection systems** (e.g., thermal/radar gates). Solutions such as **MARSS MOBtronic** are built to this standard.

**Rescue craft.** Passenger ships are **required to carry rescue boats** (e.g., 46 CFR §199.202 requires at least one rescue boat per side for ≥500 GT), so rapid drone localization/marking directly accelerates the *subsequent* pickup by mandated assets. ([eCFR][4])

---

## 3) Evidence that drones help find and stabilize a person in water ##

- **Armed-forces trials.** Royal Navy (NavyX) conducted **MOB trials** where drones *locate*, **drop life-saving equipment**, and **hover to mark** the survivor until retrieval.
- **Public-safety deployments.** Police and lifeguard programs have **dropped PFDs/life rings** to swimmers, demonstrating rapid delivery of buoyancy while a boat/helicopter closes. ([UAV Coach][5])
- **Documented rescues.** The “Little Ripper” program performed a **real drone surf rescue**, dropping an inflatable pod to two swimmers in ≈1–2 min—proof of concept for flotation delivery. ([TIME][6])

---

## 4) Sensors suited to maritime MOB detection ##

**Thermal core options and FOV.** Maritime UAV payloads commonly use **640×512 VOx microbolometer** sensors. The DJI **H20T** thermal lists **DFOV 40.6°**, 30 Hz, ≤50 mK NETD. Teledyne FLIR **Boson 640** modules offer lens sets including **24° HFOV** for narrower, longer-range search. ([DJI][7])

**Johnson criteria (pixels-on-target).** For human-target *detection*, ~**1–2 line-pairs** (≈**2–3 px**) across the critical dimension yields ~50% detection probability under favorable contrast, a standard widely used to estimate admissible altitude/FOV trade-offs. ([Ascendent Group][8])

**Peer-reviewed detection in waves/night.** A 2024 study reports **85.49% accuracy** and **23.51 FPS** for nighttime **water-person detection** using thermal video and deep learning—evidence that modern onboard models can run in real time and tolerate sea clutter.

---

## 5) Quantitative model — time-to-first-visual & coverage ##

**Assumptions (cited hardware figures; conservative flight parameters):**

- **Sensor:** H20T thermal **DFOV 40.6°**, 640×512 at 30 Hz. For a 4:3 array, this maps to ≈**HFOV 33.0°** (derived from DFOV). ([DJI Download Center][9])
- **Aircraft:** DJI Matrice 300 class, **max horizontal speed 23 m/s**; search speed modeled at **15 m/s** to reflect maritime winds and operator workload. **Max wind resistance ~15 m/s** (Beaufort 7) and **IP45** weather resistance constrain operations in heavy spray/squalls. ([RS Components][10])
- **Overlap:** 20% lane overlap for robust coverage.
- **Initial search cell:** circle of **r = 600 m** centered on last known point (≈1.13 km²), compatible with initial SAROPS priors before drift broadening. ([U.S. Coast Guard][3])

**Geometry & ground-sample distance (GSD).**
Using HFOV ≈33.0°, the instantaneous swath width at altitude *H* is
    **W = 2 H tan(HFOV/2)**.
At **H = 120 m (≈400 ft)** → **W ≈ 71.0 m**; effective lane width with 20% overlap → **Wₑ ≈ 56.8 m**. The **GSD** at 120 m is **W / 640 ≈ 0.111 m/px**, giving **2–4 px** across a 0.25–0.5 m target (head/shoulders cluster), consistent with Johnson detection thresholds, especially with thermal contrast and wake dilation. ([DJI Download Center][9])

**Coverage-rate and sweep time.**
Area-coverage rate **ACR = v × Wₑ**. With **v = 15 m/s**, **ACR ≈ 15 × 56.8 = 852 m²/s**.
To sweep **A = πr² ≈ 1,130,973 m²**, **T ≈ A / ACR ≈ 1,327 s ≈ 22.1 min** for **one** UAV. Two UAVs in coordinated lanes: **≈11 min**. Median **time-to-first-visual** (TTFV) will be ~½ the full sweep assuming uniform target distribution and constant POD per pass (classical “theory of search” approximation). ([Navcen][11])

**Altitude sensitivity.**
At **H = 200 m**, W ≈118 m → Wₑ ≈94.7 m; **T ≈ 13.3 min** for one UAV, but **GSD degrades to ~0.184 m/px**; operators must ensure pixels-on-target remain within Johnson detection limits given sea state and thermal contrast. ([HGH Infrared Systems][12])

**Implication.** A **drone-first locate-and-mark** paradigm can deliver **TTFV in ~6–12 min** (two aircraft) from last-seen point in the immediate post-fall window—well inside the cold-shock and swimming-failure phases—then hand off to rescue boats mandated under SOLAS/46 CFR for physical recovery. ([eCFR][4])

---

## 6) Marking & tracking of the survivor (drop payloads + e-beacons) ##

**Flotation & visual marking.** Trials and deployments show drones delivering **inflatable pods or life jackets**, buying buoyancy and visibility until pickup. A hovering UAV also serves as a **high-contrast visual/IR “pointer”** for boats/helicopters. ([TIME][6])

**Electronic homing.** **AIS-SART/MOB beacons** are standardized under **IEC 61097-14** and broadcast position/alerts to all nearby AIS receivers; many personal MOB units auto-activate within seconds on lifejacket inflation. A drone-dropped “MOB tag” can add an additional electronic track for the pickup craft. ([Iteh][13])

---

## 7) Operational constraints to engineer around (non-financial) ##

- **Wind/spray limitations.** Typical enterprise multirotors tolerate **≈15 m/s wind** and are **IP45**—operations degrade in gale-force winds, heavy rain or salt-spray ingestion. Maritime hardening (coatings, conformal-coated PCBs, hydrophobic optics) is advisable. ([RS Components][10])
- **Sea-surface false alarms.** Breaking waves, birds and glare are documented **nuisance sources** in MOB detection—affects automated triggers and human interpretation; fused thermal+RGB and temporal filters mitigate.
- **Pixels-on-target.** Maintain altitude/FOV ensuring ≥2–3 px across the visible target; **Johnson** thresholds provide the engineering yardstick; thermal contrast varies with time of day, sea temp and emissivity. ([HGH Infrared Systems][12])

---

## 8) Replicable calculation sheet (traceable to citations) ##

**Given:** H20T DFOV 40.6° (spec) → HFOV ≈ 33.0° (derived); M300 class speed ≤23 m/s (spec); search v = 15 m/s; overlap = 20%; r = 600 m. ([DJI Download Center][9])
**Compute:**

1. HFOV from DFOV for 4:3 sensor: **tan(H/2) = (4/5)·tan(D/2)** → HFOV ≈ 33.0°.
2. Swath **W = 2H·tan(HFOV/2)**: at **H=120 m**, **W ≈ 71.0 m**.
3. Effective lane: **Wₑ = 0.8·W ≈ 56.8 m**.
4. Area coverage rate: **ACR = v·Wₑ ≈ 852 m²/s**.
5. Sweep time: **T = (π·600²)/ACR ≈ 22.1 min** (one UAV) → **≈11.0 min** (two UAVs).
6. GSD: **W/640 ≈ 0.111 m/px** (H=120 m) → **2–4 px** across a 0.25–0.5 m target, in line with **Johnson** detection thresholds. ([HGH Infrared Systems][12])

---

## 9) Key sources (selected) ##

- **Nighttime water-person detection** with thermal + deep learning, **85.49% accuracy @ 23.51 FPS** (MDPI, 2024).
- **Royal Navy** MOB drone trials: locate, **drop kit**, hover.
- **ISO 21195:2020** — performance requirements for **non-wearable** overboard detection.
- **CLIA/G.P. Wild** incident dataset **2009–2019** (212 overboards, 48 rescues).
- **USCG SAROPS** drift/effort planning (Monte-Carlo). ([U.S. Coast Guard][3])
- **Johnson criteria** (pixels-on-target for detection/recognition/ID). ([Ascendent Group][8])
- **H20T** thermal specs (DFOV 40.6°, 640×512 @ 30 Hz, ≤50 mK). **M300** airframe speed/resistance (max 23 m/s; wind ≈15 m/s; IP45). ([DJI Download Center][9])
- **AIS-SART/MOB** standard **IEC 61097-14** and device behavior. ([Iteh][13])
- **Cold-shock**/immersion stages and early cardiac/resp responses. ([U.S. Coast Guard][2])

---

### Conclusion ###

Peer-reviewed detection performance, military/police trials, established MOB-detection standards, and a transparent coverage model jointly support a **drone-first locate-and-mark** approach: autonomous **auto-launch to first grid**, then **human-piloted** search, electronic/visual **marking**, and **handover to required rescue boats**. This data directly targets the high-risk first minutes after entry into cold water. ([eCFR][4])

[1]: https://dl.djicdn.com/downloads/matrice-300/20200529/M300_RTK_User_Manual_EN_0604.pdf "MATRICE 300 RTK"
[2]: https://www.dco.uscg.mil/Portals/9/DCO%20Documents/5p/CG-5PC/CG-CVC/CVC3/notice/flyers/Cold_Water_Survival_Hypothermia.pdf "Cold Water Survival & Hypothermia"
[3]: https://www.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/ "Search and Rescue Optimal Planning System (SAROPS)"
[4]: https://www.ecfr.gov/current/title-46/chapter-I/subchapter-W/part-199/subpart-C "Subpart C—Additional Requirements for Passenger Vessels"
[5]: https://uavcoach.com/drone-lifeguards/ "San Mateo Sheriff's Office Tests the Use of Drones as ..."
[6]: https://time.com/5109269/surf-drone-rescue-worlds-first-australia/ "Watch the World's First Ever Drone Surf Rescue"
[7]: https://enterprise.dji.com/zenmuse-h20-series/specs "Specs - Zenmuse H20 Series"
[8]: https://www.ascendentgroup.com/uploads/files/Johnson_Criteria_Thermal_DRI_Performance_and_Range_Explained.pdf "White Paper"
[9]: https://dl.djicdn.com/downloads/Zenmuse_H20_Series/Zenmuse_H20_Series_User_Manual-EN.pdf "ZENMUSE H20 SERIES"
[10]: https://docs.rs-online.com/c8cb/A700000008264601.pdf "Matrice 300 RTK - RS Online"
[11]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf "The Theory of Search - A Simplified Explanation - navcen"
[12]: https://hgh-infrared.com/detection-recognition-identification-ranges-faq/ "Detection Recognition Identification I HGH Infrared Systems"
[13]: https://cdn.standards.iteh.ai/samples/16694/7bf752a5752548be8abe3a3b90f71445/IEC-61097-14-2010.pdf "IEC 61097-14"
