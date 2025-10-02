# Step 1 — Desk Research: Evidence Landscape Brief (claims → what we’ll prove → initial sources)

## A. Regulatory & standards landscape (what “good” must align to)

- **SOLAS Chapter III sets life-saving expectations for passenger ships**, including survival craft and *rescue boats* with rapid launch/embarkation provisions. This is the baseline environment your system plugs into (auxiliary to, not replacing, SOLAS gear). ([International Maritime Organization][1])
- **LSA Code & related guidance require launch/operation with the ship making headway (~5 kn in calm water)**; U.S. regs mirror this (eCFR §108.570). This is relevant to coordinated drone/boat operations during the first minutes of an MOB. ([racingyachtmanagement.com][2])
- **ISO 21195:2020** defines technical requirements for *overboard detection systems* (camera/radar/analytics—non-wearable). Several cruise deployments are working to/claim conformance; we’ll reference this in our trial acceptance criteria. ([ISO][3])

**Implication for trials:** the evidence package should show that `CROW` improves *detection & localization* and integrates cleanly with SOLAS/LSA/ISO-21195 workflows (as auxiliary equipment), not that it replaces any mandated asset.

---

## B. Current shipboard detection tech (state of practice we must beat/supplement)

- Cruise lines are beginning to **fit AI/IR/radar overboard detection** that alarms the bridge instantly (e.g., MARSS *MOBtronic*; Zelim *ZOE* now on Ambassador’s *Ambition*; reported million-dollar installs). These systems address *“know immediately”*—not *“find & mark at distance.”* ([Marine Log][4])
- Trade and mainstream coverage confirms **thermal cameras + micro-radar + AI analytics** are the norm for detection pods today (and are being ISO-tested / LR type-tested). This is the baseline we’ll complement with a rapid aerial response. ([USA Today][5])

**Implication for product/claims:** the “delta” must prove is **faster reacquisition at sea** (TTFV) and **better localization/beaconing** beyond the hull—*after* the detection alarm.

---

## C. Survivability constraints (why seconds matter)

- **Cold shock** and early immersion phases drive mortality in the *first minutes*; guidance stresses very short windows to meaningful aid. Recent pieces and reviews summarize the four immersion phases and the criticality of the first ~10–15 min. ([PMC][6])

**Implication for metrics:** the primary endpoint (**Time-to-First-Visual**, TTFV) and **time-to-buoy-within-reach** are the most clinically relevant levers we control.

---

## D. Search theory & drift modeling (how to search smarter)

- **USCG SAROPS** is a Monte-Carlo particle model that builds a probability map (PDM) from wind/current & uncertainty; it’s the *de facto* standard for maritime SAR planning. We’ll mirror the approach (scaled for near-ship). ([Deputy Commandant for Mission Support][7])

**Implication for software:** the BIU can generate a lightweight SAROPS-style PDM to guide the pilot’s manual patterns—evidence should show PDM-weighted patterns reduce TTFV vs. uniform sweeps.

---

## E. Sensors & detection science (why IR-first from the air)

- **Nighttime/person-in-water detection with thermal imagery + YOLO-class models** has been demonstrated in peer-reviewed/archived literature; fusion with RGB (and even LiDAR/mmWave) improves robustness in clutter. ([PMC][8])
- **Aerial thermal human detection** literature (broader than maritime) supports our IR-first pipeline and informs minimum pixel footprints vs. altitude for reliable inference (we’ll calibrate these in harbor trials). ([ResearchGate][9])

**Implication for trials:** pre-register ROC/AUC targets and altitude/swath guidance derived from these works, then verify with our own labeled maritime dataset.

---

## F. Drones as MOB “find/mark” tools (external validation that the concept is workable)

- **Royal Navy trials** (NavyX) publicly tested remotely-piloted drones that **locate personnel in water, drop life-saving packages, and hover as a beacon**—exactly our intended role. Multiple outlets and the RN site carry the results. ([Royal Navy][10])
- **Academic/industrial R&D** (DTU/OSAR) is actively building *autonomous* MOB UAVs with IR/RGB/LiDAR payloads and buoy drops. We’re choosing a *human-in-the-loop* doctrine, but these programs show technical feasibility and sensor suites. ([electro.dtu.dk][11])

**Implication for positioning:** the differentiation is **auto-launch + bounded diagnostic**, then **pilot in command**—aligned with conservative maritime operations while leveraging proven drone capabilities.

---

## G. What the claim is (need to prove in trials)

1. **TTFV reduction** vs. baseline MOB drills on cruise vessels (minutes → seconds). We’ll run paired A/B drills with and without `CROW`. ([Deputy Commandant for Mission Support][7])
2. **High detection probability** (Pdet) and **manageable false positives** (FPR) using IR-first detection and fusion. Literature guides thresholding; we’ll generate ROC curves from our dataset. ([PMC][8])
3. **Reliable auto-launch + bounded IRD** with **human take-over ≤ 60 s p95**, satisfying operational culture & risk appetite reflected in SOLAS/LSA drill regimes. ([Maritime Safety Innovation Lab LLC][12])
4. **Effective marking/aid**: buoy drop CEP ≤ 10 m and beacon CEP ≤ 10 m in Beaufort 5—directly supporting recovery while rescue boats maneuver under existing LSA/launch constraints. ([racingyachtmanagement.com][2])
5. **Compliance posture**: auxiliary to SOLAS; interoperable with ISO 21195-class detection systems the industry is already buying. ([ISO][3])

---

## H. Evidence package to produce (and who it convinces)

- **Standards mapping** (SOLAS/LSA/ISO 21195) → for class societies & flag states. ([International Maritime Organization][1])
- **Harbor + open-sea trial reports** with stats (paired tests for TTFV; ROC/AUC; CEP; FPR) → for safety officers & insurers. ([Metron][13])
- **Witness statements** (class/insurer presence on select drills) + **immutable logs** (hashed video/telemetry).
- **Peer-style whitepaper** with methods & limitations + **operator SOPs** aligned to weekly drill culture under SOLAS. ([Maritime Safety Innovation Lab LLC][12])

---

## I. Known open questions (resolve in trials)

- **Wind/sea-state envelope** for dependable hovering & visual/IR performance near the hull’s turbulent flow—benchmarks to be documented.
- **Nighttime clutter/whitecap false positives** rate at varying altitudes—handled via fusion + pilot verification; quantified in ROC/FPR. ([PMC][8])
- **Coordination with rescue-boat launch** while ship still has headway (5 kn in calm water)—coordinate SOP timing & radio choreography. ([racingyachtmanagement.com][2])

---

### Deliverables from Step 1

1. **Citable standards pack:** SOLAS III summary; LSA Code extracts; §108.570 eCFR; ISO 21195 summary. ([International Maritime Organization][1])
2. **State-of-practice brief:** MARSS *MOBtronic* & Zelim *ZOE* cruise deployments + tech mix (IR + micro-radar + AI). ([Marine Log][4])
3. **Survivability memo:** cold shock & first-minutes emphasis (literature excerpts). ([PMC][6])
4. **Search-theory note:** Monte-Carlo PDM rationale (SAROPS). ([Deputy Commandant for Mission Support][7])
5. **Sensor science note:** IR/RGB fusion for nighttime maritime detection; initial ROC targets. ([PMC][8])
6. **External feasibility note:** Royal Navy & DTU MOB drone efforts. ([Royal Navy][10])

---

[1]: https://www.imo.org/en/OurWork/Safety/Pages/SummaryOfSOLASchapter-3-default.aspx?utm_source=chatgpt.com "Summary of SOLAS chapter III"
[2]: https://www.racingyachtmanagement.com/misc/lsa_code.pdf?utm_source=chatgpt.com "LSA CODE"
[3]: https://www.iso.org/standard/76051.html?utm_source=chatgpt.com "ISO 21195:2020 - Ships and marine technology"
[4]: https://www.marinelog.com/news/new-cruise-ship-will-have-1-million-mobtronic-man-overboard-detection-system/?utm_source=chatgpt.com "New cruise ship will have $1 million MOBtronic man- ..."
[5]: https://www.usatoday.com/story/travel/cruises/2023/02/22/cruise-ship-overboard-detection-system/11172790002/?utm_source=chatgpt.com "Cruise ship overboard detection systems: What are they?"
[6]: https://pmc.ncbi.nlm.nih.gov/articles/PMC6706340/?utm_source=chatgpt.com "Lost at sea: the medicine, physiology and psychology of ..."
[7]: https://www.dcms.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"
[8]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11175020/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."
[9]: https://www.researchgate.net/publication/352097911_Human_detection_in_Aerial_Thermal_imaging_using_a_Fully_Convolutional_Regression_Network?utm_source=chatgpt.com "Human detection in Aerial Thermal imaging using a Fully ..."
[10]: https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob?utm_source=chatgpt.com "Navy tests drones in man overboard trials"
[11]: https://electro.dtu.dk/newsarchive/2024/06/man-overboard-autonomous-drones-will-save-lives-at-sea?utm_source=chatgpt.com "Man overboard: Autonomous drones will save lives at sea"
[12]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2018/06/he01195.pdf?utm_source=chatgpt.com "SOLAS onboard drill requirements"
[13]: https://www.metsci.com/wp-content/uploads/2019/08/Search-and-Rescue-Optimal-Planning-System.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"
