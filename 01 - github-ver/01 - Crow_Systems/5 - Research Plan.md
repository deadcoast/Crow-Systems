# Research Plan #

## Problem Sizing & Survivability Window (Why Seconds Matter) ##

**Goal**: Quantify the incident scale and the medical urgency your drone addresses.
    - Global cruise MOB frequency and rescue rates (baseline risk)
    - Cold-water / immersion survival drivers that make fast location critical

Supporting Evidence:
    - Extract incident counts and rescue outcomes from CLIA’s operational incident reports; cross-check with independent summaries. ([Cruise Lines International Association][1])
    - Summarize peer-reviewed work on **cold shock** and early immersion phases to tie TTFV directly to survivability. ([ScienceDirect][2])

Outputs:
    - One-pager: “Incidents per year, % rescued, survival curve vs minutes to aid.”
    - Figure: histogram of MOB incidents (2009-2019) and **rescue rate (~28%)**—your baseline to beat. ([Cruise Lines International Association][1])

---

## Standards & Buyer Environment (What “Good” Must Align To) ##

**Goal**: Prove you’re building to the framework buyers/regulators already use.
    - **ISO 21195:2020** requirements for non-wearable overboard **detection** systems (so we show complementarity).
    - **SOLAS/LSA** expectations for rescue and launch (to position drone as **auxiliary**, not a replacement).
    - Class society practices (DNV/ABS/LR) and insurer expectations for “reasonable available technology.”

Supporting Evidence:
    - Extract the ISO 21195 technical requirement themes and any implied performance bars (e.g., detection probability targets cited by trade press). ([Iteh][3])
    - Map where SOLAS/LSA governs boats/launch and where a **drone slot** naturally fits (auxiliary find/mark). (Cite SOLAS III/LSA in the dossier; ISO pages shown here demonstrate the context cruise buyers recognize.) ([ISO][4])

Outputs:
    - “Standards map” slide: ISO 21195 (detect) ➜ **`CROW` (locate/mark)** ➜ SOLAS/LSA (rescue), with clauses and acceptance language buyers understand. ([ISO][4])

---

## State of Practice & Competitive Landscape (What Ships Buy Today) ##

**Goal:** show that the industry is already investing in detection—and that you’re the missing **rapid find/mark** link.
    - Cruise deployments of **camera/IR/radar + AI** overboard detection (who, where, what signals).
    - Vendor progress on ISO 21195 conformance.

Supporting Evidence:
    - Document **Zelim ZOE**’s 2025 installation on Ambassador’s *Ambition* (detection/tracking). ([Cruise Industry News | Cruise News][5])
    - Document **MARSS MOBtronic** and its ISO 21195 certification progress (buyers will recognize it). ([MARSS][6])

Outputs:
    - Landscape grid: vendor, tech (IR/radar/AI), status (ISO 21195), **what they don’t do** (aerial locate/mark) → your wedge.

---

## Technical Feasibility Evidence (Can a Small Drone Do the Job?) ##

**Goal:** bring external, neutral proof that **airborne IR + manual pilot** can locate/mark a person in water.
    - Documented **MOB drone trials** and their capabilities (find → drop aid → hover beacon).
    - Best-practice **search theory** you’ll adopt (probability-guided).

Supporting Evidence:
    - Cite **Royal Navy (NavyX)** trials: remotely-piloted systems located personnel, **dropped life-saving equipment**, and **hovered as a beacon** until recovery. Multiple independent reports corroborate this. ([Royal Navy][7])
    - Anchor your **probability-weighted search** to **SAROPS** (USCG Monte-Carlo model) to show your method mirrors recognized SAR practice. ([U.S. Coast Guard][8])

Outputs:

- 2 slides: “External proof” (RN trial quotes) and “Search math we adopt” (SAROPS diagram).

---

## Primary Research You Run **Before** Customer Trials (Low-Cost, Persuasive) ##

**Goal:** de-risk the product and arm sales with data without needing a cruise partner yet.

- **Harbor mannequin study v0**:
    - Place Ruth Lee “Oscar” at 50–200 m, day/night; measure **TTFV** with your prototype vs human lookouts; record **Pdet** and **FPR**. (This creates your first ROC curves and video reels.) ([MARSS][6])
    - **Altitude vs thermal separability** bench + basin work: derive altitude bands where IR yields ≥10–15 px head/shoulders; publish **w(h)** table for pilot guidance.
    - **Drop accuracy tests** from low hover: CEP versus drift (prove you can place flotation within ≤10 m up-drift).
    - **Latency audits** (glass-to-glass video): prove <150–220 ms end-to-end for pilot control.

Supporting Evidence:
    - Methods borrowed from maritime standards and MIL/IEC test methods already recognized (salt-fog/IP/EMC covered in your bench plan; you only show the summaries to buyers). ([Navcen][9])

Outputs:
    - Short **tech brief** (ROC curves, TTFV boxplots, buoy CEP), plus a 60-second **demo reel**.

---

## Stakeholder & Economic Validation (Why They’ll Buy) ##

**Goal:** quantify decision criteria for Safety VPs, class societies, and insurers; model ROI.

- Buyer interviews: 5–10 **Safety/Marine Ops** leaders on acceptance criteria (what proof unlocks pilots).
- **Class society** pre-reads: what evidence language they want in a dossier (witness days, logs).
- **Insurer** discussions: how improved TTFV/Pdet translate to risk adjustments.

Supporting Evidence:
    - Triangulate with public records and reputable industry coverage showing **growing installs** of overboard detection (ZOE/MOBtronic) and the incident scale (CLIA). ([Cruise Industry News | Cruise News][5])

Outputs:
    - “Buyer Requirements” one-pager (acceptance thresholds + data formats).
    - A simple **EV model**: expected loss reduction vs system cost → fleet ROI.

---

## Research Outputs ##

- **Evidence Landscape Brief** (sources above).
- **Standards Map** (ISO 21195 / SOLAS fit). ([ISO][4])
- **Competitive Landscape** (ZOE/MOBtronic) with gaps your drone fills. ([Cruise Industry News | Cruise News][5])
- **Feasibility Proof Pack** (RN trials + your harbor results + ROC/CEP/latency). ([Royal Navy][7])
- **Buyer Requirements & ROI** memo.

From there, CROW will be ready to approach a line with a **pilot proposal**.

[1]: https://cruising.org/sites/default/files/2025-03/report_operational_incidents_2019-v-1.pdf "Report on Operational Incidents 2009 to 2019 For CLIA ..."
[2]: https://www.sciencedirect.com/science/article/pii/S0306456523003169 "Habituation of the cold shock response: A systematic ..."
[3]: https://cdn.standards.iteh.ai/samples/76051/c3ad63c1e50e4901911cca54874631d9/ISO-21195-2020.pdf "INTERNATIONAL STANDARD ISO 21195"
[4]: https://www.iso.org/obp/ui/en/ "ISO 21195:2020(en), Ships and marine technology"
[5]: https://cruiseindustrynews.com/cruise-news/2025/03/ambassador-first-cruise-line-to-install-zelims-mob-system/ "Ambassador: First Cruise Line to Install Zelim's MOB System"
[6]: https://marss.com/products/mobtronic/ "MOBtronic - Man Overboard Detection System"
[7]: https://www.royalnavy.mod.uk/news/2021/july/02/210702-drone-trials-mob "Navy tests drones in man overboard trials"
[8]: https://www.uscg.mil/Our-Organization/Assistant-Commandant-for-Acquisitions-CG-9/International-Acquisition/SAROPS/ "Search and Rescue Optimal Planning System (SAROPS)"
[9]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf "The Theory of Search - A Simplified Explanation - navcen"
