# CRuise Overboard Watch Drone (CROW): Supporting Research Dossier #

## 1. Purpose and Scope ##

Documented evidence supporting: (a) problem significance on cruise vessels; (b) medical urgency of rapid localization; (c) conformance context with maritime standards; (d) state of current shipboard detection technology; (e) accepted search doctrine; (f) external demonstrations of drone-based “find/mark” capability.

---

## 2. Incident Scale on Cruise Ships ##

Cruise industry incident data compiled for CLIA (Cruise Lines International Association) report **212 overboard events** between 2009–2019 with **48 rescues** (≈ **28%** rescued alive). The primary source is the CLIA-commissioned operational incidents report (G.P. Wild); CLIA hosts the report and an official download page. ([Cruise Lines International Association][1])
Recent journalistic summaries cite the same CLIA figure, underscoring continued relevance. ([The Independent][2])

**Implication:** Baseline rescue rate is poor; any technology that reliably reduces time-to-first-visual (TTFV) and improves localization should be considered material to outcomes.

Cruise Lines International Association’s commissioned “Report on Operational Incidents 2009–2019” (by G.P. Wild) documents **212 overboard events** in that period with **48 rescues** (~**28%** rescued alive). The CLIA resource page and the report PDF provide the primary figures used by industry stakeholders. ([Cruise Lines International Association](https://cruising.org/resources/report-operational-incidents-2009-2019 "Report on Operational Incidents 2009 to 2019"))

Additional public-facing and governmental testimonies cite the same CLIA/G.P. Wild series for trend context, underscoring its use as the sector’s baseline dataset. ([Congress.gov](https://www.congress.gov/116/meeting/house/110181/witnesses/HHRG-116-PW07-Wstate-SalernoB-20191114.pdf "prepared testimony of brian m. salerno"))

**Takeaway:** Baseline rescue rate is low; reducing time-to-first-visual (TTFV) and stabilizing localization are material levers for outcome improvement.

---

## 3. Medical Urgency: Early-Minute Risk in Cold Water ##

Cold-water immersion provokes the **cold shock response** within the **first minute**, including gasping, uncontrolled hyperventilation, sympathetic tachycardia, and arrhythmogenic stress; early minutes are decisive for survival. Medical literature and reviews consistently identify these mechanisms and risks.
A 2024 systematic review on cold-shock habituation reiterates life-threatening cardio-respiratory effects on initial immersion, reinforcing the time-critical nature of early assistance. ([ScienceDirect][3])([PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC9518606/ "Health effects of voluntary exposure to cold water"))

**Implication:** The controlling lever for outcomes is **fast location and marking** to enable timely rescue, particularly at night and in cold/temperate waters.

**Takeaway:** The first minutes after splash are the controlling window; technology that accelerates **finding** and **marking** a casualty addresses the primary physiological constraint.

---

## 4. Standards and Regulatory Context ##

- **ISO 21195:2020** specifies the **technical requirements for non-wearable overboard detection systems**—i.e., systems designed to detect a person going overboard; **wearable-trigger systems are out of scope**. Official ISO abstract and accessible copies confirm the scope and exclusion language. ([ISO][4])
- **SOLAS/LSA** govern survival craft and **rescue-boat** launch/operation; headway provisions and rapid launch expectations shape how recovery assets are used once a victim is located. (Industry and national mirror regulations reference launch capability at low forward speed in calm water.)  ([dieselduck.info][5]), ([IJTMGH](https://www.ijtmgh.com/article_119591_7e5c0accfb1d600877f9bc1bbb542b89.pdf "Death at Sea: Passenger and Crew Mortality on Cruise Ships"))

**Position in framework:** A first-response drone is **auxiliary lifesaving equipment** that acts **after** an ISO-21195-conformant detection alarm to **locate, mark, and support** recovery under SOLAS/LSA procedures. ([ISO](https://www.iso.org/standard/76051.html "ISO 21195:2020 - Ships and marine technology"))

---

## 5. Current State of Shipboard Detection (Industry Practice) ##

Cruise operators are adopting fixed **AI/IR/microwave** detection suites meeting ISO-21195 intent:

- **Zelim “ZOE”**—intelligent detection/tracking—announced for installation on Ambassador Cruise Line’s *Ambition* (first cruise reference). ([Seatrade Cruise News][6])
- **MARSS “MOBtronic”**—man-overboard detection; vendor cites ISO-21195 performance aims and reports certification progress (including references to ≥95% detection probability and ≤1 false alarm/day targets in the standard’s acceptance criteria). ([MARSS][7])

**Gap:** These systems **raise the alarm** and provide near-hull tracking; they do **not** conduct rapid aerial area search, precision marking, or flotation delivery at distance.

---

## 6. Accepted Search Doctrine (Foundation for Method) ##

The U.S. Coast Guard’s **SAROPS** employs **Monte-Carlo drift simulation** and probability mapping to direct search effort toward the highest-likelihood regions, using wind and current inputs and accounting for uncertainty. Official briefs and technical descriptions detail particle-based drift projections and probability-guided search assignment. ([U.S. Coast Guard][8])

**Application:** A near-ship, time-compressed analogue (drift particles around the last-known position) is technically orthodox for guiding a pilot’s manual grid in the initial minutes post-alarm.

---

## 7. External Demonstrations of Drone “Find/Mark” Capability ##

The **Royal Navy (NavyX)** publicly reports trials in which **remotely-piloted systems** (a) **located personnel in the water**, (b) **dropped life-saving equipment**, and (c) **hovered over the location until rescuers arrived**. Navy releases and independent defense outlets cover tests at Horsea Island and at sea, naming heavy-lift Minerva platforms (partners included Malloy Aeronautics and Planck Aerosystems). ([Royal Navy](https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"))

**Relevance:** Confirms the precise operational role proposed for a pilot-controlled first-response drone on large vessels: **find**, **mark/beacon**, **deliver flotation**, and **vector rescuers**.

---

## 8. Technology Basis: Sensors and Performance Targets ##

Literature on thermal imaging in cold/low-light human detection supports **LWIR + RGB fusion** for immersed subject detection when spatial footprint (pixels across head/shoulders) and frame rate are adequate; medical and human-factors reviews also emphasize the first-minute hazards that motivate IR-first detection. ([PMC][3])

**Vendor acceptance bars** cited in ISO-aligned detection programs (e.g., MARSS MOBtronic) report targeting high detection probability (≥95% for fixed systems) and low nuisance activation; while a UAV is not itself an ISO-21195 detector, these reference points inform confidence/verification thresholds once a target is reacquired by air. ([MARSS][8])

- **Thermal (LWIR) + RGB** sensing is supported by literature on human detection in cold/low-light environments; studies document thermal imaging enabling recognition of immersed subjects with appropriate spatial footprint and frame rate. ([ScienceDirect][3])
- Industry ISO-21195 acceptance targets referenced in vendor certification updates note **≥95% detection probability** with low false-alarm rates for **detection systems**; while a drone is not itself an ISO-21195 detector, these benchmarks inform expectations for **verification confidence** once a target is reacquired. ([MARSS][10])

**Operational translation:** From an altitude generating ≥10–15 IR pixels across a head-and-shoulders target, a compact UAV can sweep probability-weighted grids rapidly and cue visual confirmation, then mark the position by hover/beacons and optional flotation drop.

---

## 9. Integration with Rescue Practice ##

SOLAS/LSA provides the rescue framework (boats, launch/headway, painters, towing behavior). A drone does not substitute for required craft; it **shortens the search** and **stabilizes localization** for the rescue boat vector, including at night, in chop, and under drift. ([dieselduck.info][5])

---

## 10. Sensor and detection considerations germane to a compact UAV ##

Literature on thermal imaging in cold/low-light human detection supports **LWIR + RGB fusion** for immersed subject detection when spatial footprint (pixels across head/shoulders) and frame rate are adequate; medical and human-factors reviews also emphasize the first-minute hazards that motivate IR-first detection. ([PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC9518606/ "Health effects of voluntary exposure to cold water"))

**Vendor acceptance bars** cited in ISO-aligned detection programs (e.g., MARSS MOBtronic) report targeting high detection probability (≥95% for fixed systems) and low nuisance activation; while a UAV is not itself an ISO-21195 detector, these reference points inform confidence/verification thresholds once a target is reacquired by air. ([MARSS](https://marss.com/media/gnlohams/marss-mobtronic.pdf "AUTOMATIC MAN-OVERBOARD DETECTION & ..."))

---

## 11. Synthesis for a cruise-sector first-response drone ##

1. **Problem magnitude:** ≥212 overboards in 2009–2019 with ~28% rescues; a material safety/PR risk acknowledged by operators and regulators. ([Cruise Lines International Association][1])
2. **Physiology:** first minutes are decisive due to cold-shock cardio-respiratory effects; rapid location and marking are the only technical levers that directly compress this window. ([PMC][3])
3. **Conformance posture:** fits between **ISO-21195 detection** and **SOLAS/LSA rescue**, as an **auxiliary** system that accelerates find/mark/aid. ([ISO][5])
4. **Method legitimacy:** probability-guided search via SAROPS-style Monte-Carlo mapping is the recognized maritime doctrine for allocating search effort. ([Metron][10])
5. **Feasibility:** Royal Navy trials demonstrate pilot-controlled UAVs performing locate, flotation drop, and hover beaconing in MOB scenarios. ([Royal Navy][11])
6. **Industry trajectory:** fixed ISO-aligned detection (ZOE, MOBtronic) is already being adopted; aerial **reacquisition and marking** remain the open performance gap. ([Naval News][7])

---

## 12. Market Validation Signals ##

- Formal reporting of overboard incidents and low rescue rates establishes **material risk** acknowledged by operators and regulators. ([Cruise Lines International Association][1])
- Announced cruise deployments of ISO-aligned **overboard detection** indicate capital commitment to the **detect** layer; an aerial **find/mark** layer is an adjacent, complementary spend. ([Seatrade Cruise News][6])

---

## 13. Summary of Evidence ##

1. **Problem significance:** ≥212 overboards (2009–2019) with ≈28% rescues; improvement potential is substantial. ([Cruise Lines International Association][1])
2. **Time-critical physiology:** Cold-shock/immersion literature identifies the **first minutes** as decisive for survival. ([The Lancet][11])
3. **Conformance alignment:** ISO-21195 defines **detection**; SOLAS/LSA anchors **rescue**; an MOB drone serves as **auxiliary localization/marking**, compatible with both. ([ISO][4])
4. **Methodological legitimacy:** SAROPS-style probability mapping is the recognized standard for maritime search planning. ([U.S. Coast Guard][8])
5. **Feasibility in practice:** Royal Navy trials demonstrate **pilot-controlled UAV** capability to find, drop aid, and beacon a casualty. ([Royal Navy][9])
6. **Industry trajectory:** Cruise lines are investing in ISO-aligned overboard **detection** (ZOE, MOBtronic), leaving an open need for rapid **aerial reacquisition and marking**. ([Seatrade Cruise News][6])

---

## References (key sources) ##

## 9) References (representative, high-signal) ##

- **CLIA Operational Incidents 2009–2019**—primary incident baseline and outcomes. ([Cruise Lines International Association](https://cruising.org/resources/report-operational-incidents-2009-2019 "Report on Operational Incidents 2009 to 2019"))
- **ISO 21195:2020**—scope and non-wearable detection requirements (official abstract; accessible PDF). ([ISO](https://www.iso.org/standard/76051.html "ISO 21195:2020 - Ships and marine technology"))
- **SOLAS/LSA (context)**—launch/operation framework for rescue boats; rapid headway launch expectations. ([IJTMGH](https://www.ijtmgh.com/article_119591_7e5c0accfb1d600877f9bc1bbb542b89.pdf "Death at Sea: Passenger and Crew Mortality on Cruise Ships"))
- **USCG SAROPS**—Monte-Carlo probability mapping for maritime search; Coast Guard standard. ([U.S. Coast Guard](https://www.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/ "Search and Rescue Optimal Planning System (SAROPS)"))
- **Royal Navy NavyX trials**—remotely-piloted systems locating casualties, dropping aid, and hovering as a beacon. ([Royal Navy](https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"))
- **Zelim ZOE / MARSS MOBtronic**—current cruise-sector detection deployments and ISO-aligned performance claims. ([Naval News](https://www.navalnews.com/naval-news/2021/07/royal-navy-tests-drones-in-man-overboard-trials/ "Royal Navy tests Drones In Man Overboard Trials"))

- CLIA Operational Incidents 2009–2019 (primary). ([Cruise Lines International Association][1])
- ISO 21195:2020 overview and text. ([ISO][4])
- LSA Code notes on headway and boat behavior. ([dieselduck.info][5])
- USCG SAROPS overview and technical description. ([U.S. Coast Guard][8])
- Royal Navy NavyX man-overboard drone trials. ([Royal Navy][9])
- Zelim ZOE cruise installation announcements. ([Seatrade Cruise News][6])
- MARSS MOBtronic product page and ISO-21195 certification update. ([MARSS][7])
- Cold-shock / immersion literature (Lancet review; 2024 systematic review). ([The Lancet][11])

---

### Annex A — Notable quoted language for use in decks and briefs ##

- ISO 21195 abstract: “**This document specifies technical requirements for systems designed to detect a person who has gone overboard from a ship.** This document **does not cover** [MOB] detection systems that require passengers or crew to wear or carry a device…” (ISO official page). ([ISO](https://www.iso.org/standard/76051.html "ISO 21195:2020 - Ships and marine technology"))
- Royal Navy release: “**Remotely-piloted systems which locate personnel in the water, drop life-saving equipment and hover over the location until rescuers arrive** have been tested extensively…” (RN news). ([Royal Navy](https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"))
- SAROPS overview: “**Monte Carlo based system** that uses thousands of simulated particles…” (USCG info sheet). ([U.S. Coast Guard](https://www.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/ "Search and Rescue Optimal Planning System (SAROPS)"))
- MARSS MOBtronic brochure: **“micro radars, thermal cameras with video analytics… high level of accuracy with less than 1 nuisance activation per day”** (vendor datasheet). ([MARSS](https://marss.com/media/gnlohams/marss-mobtronic.pdf "AUTOMATIC MAN-OVERBOARD DETECTION & ..."))

---

### Appendix: Notes on Data Quality ##

- CLIA report is the authoritative industry compilation for the 2009–2019 period; third-party summaries should cite back to CLIA/G.P. Wild. ([Cruise Lines International Association][1])
- ISO-21195 texts (official portal and hosted PDF) provide definitive scope language excluding wearables and specifying technical requirements for **detection** systems. ([ISO][4])
- SAROPS documentation clarifies Monte-Carlo drift foundations for probability-guided search assignment; near-ship adaptations remain methodologically consistent. ([U.S. Coast Guard][8])

---

[1]: https://cruising.org/sites/default/files/2025-03/report_operational_incidents_2019-v-1.pdf "[PDF] Report on Operational Incidents 2009 to 2019 For CLIA Global By ..."
[2]: https://www.the-independent.com/travel/cruise/what-happens-person-overboard-cruise-ship-b2709339.html "What happens when someone goes overboard on a cruise ship?"
[3]: https://www.sciencedirect.com/science/article/pii/S0306456523003169 "Habituation of the cold shock response: A systematic ..."
[4]: https://www.iso.org/standard/76051.html "ISO 21195:2020 - Ships and marine technology"
[5]: https://www.dieselduck.info/library/03%20regulatory/2012-LSA%20code%20basic.pdf "LIFE SAVING APPLIANCES (LSA) CODE:"
[6]: https://www.seatrade-cruise.com/safety-security/ambassador-to-introduce-zelim-s-zoe-man-overboard-technology "Ambassador to introduce Zelim man overboard technology"
[7]: https://marss.com/products/mobtronic/ "MOBtronic - Man Overboard Detection System"
[8]: https://www.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/ "Search and Rescue Optimal Planning System (SAROPS)"
[9]: https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"
[10]: https://marss.com/about/news/marss-mobtronic-man-overboard-technology-achieves-phase-2-iso21195-certification/ "MARSS MOBtronic man overboard technology achieves ..."
[11]: https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(03)15057-X/fulltext "Cold water immersion: sudden death and prolonged survival"
