# Drift Modeling & Probability-Guided Search for Man-Overboard (MOB): Source-Backed Technical Basis

## 1) Operational foundation: SAROPS (U.S. Coast Guard)

**Search and Rescue Optimal Planning System (SAROPS)** is the U.S. Coast Guard’s operational planner for almost all maritime SAR cases. It:

* Runs **Monte-Carlo particle simulations** to project survivor drift under wind/current and uncertainty,
* Produces **probability density maps** for the search area,
* Allocates search effort to **maximize probability of success (POS)** and accounts for the effects of prior unsuccessful searches,
* Ingests **environmental data** (winds, currents, waves, temperature) via an **Environmental Data Server (EDS)**. ([U.S. Coast Guard][1])

**Environmental inputs** used in SAROPS include NOAA/Navy models (e.g., **HYCOM**, **NCOM**), **GFS/NAM winds**, buoy and CODAR surface currents; uncertainty of these inputs is explicitly considered. ([cdn.ioos.noaa.gov][2])

**Older search-theory primers** used in USCG training define **Probability of Containment (POC)**, **Probability of Detection (POD)**, and **POS = POC × POD**, and describe the Bayesian update of location probabilities after each unsuccessful search—core ideas that SAROPS implements computationally. ([Navcen][3])

**Academic descriptions** of SAROPS confirm the **Monte-Carlo particle** approach, Bayesian updating, and optimization for search-asset allocation. ([ResearchGate][4])

---

## 2) Math essentials for near-ship adaptation (MOB focus)

### 2.1 Drift propagation (short-horizon, surface object)

Position of a casualty at time (t) from last-known position (\mathbf{x}*0):
$$
\mathbf{x}(t)=\mathbf{x}*0+\int_0^t \Big(\mathbf{V}*{\text{current}}(\tau)+\alpha,\mathbf{V}*{\text{wind}}(\tau)\Big),d\tau+\boldsymbol{\epsilon}(t),
$$
where ($\alpha$) is **windage** (fractional leeway of a person at the surface), and ($\boldsymbol{\epsilon}(t)$) is a random-walk term modeling unresolved turbulence and model error. In SAROPS, thousands of particles are propagated with these terms; the resulting cloud forms a **probability density map (PDM)**. ([U.S. Coast Guard][1])

**Environmental sources** (for ($\mathbf{V}*{\text{current}}, \mathbf{V}*{\text{wind}})$) are typically NOAA/Navy models and in-situ observations; EDS catalogs these feeds and their uncertainties. ([cdn.ioos.noaa.gov][2])

### 2.2 Probability & effort (POS, POD, sweep width)

Search effectiveness follows classic maritime search theory (Koopman/Stone). For a search leg with **sweep width (W)**, **track spacing (S)**, and sensor/condition-dependent (POD), the **Probability of Success (POS)** over a sub-area is:

$$
\mathrm{POS} = \mathrm{POC}\times \mathrm{POD},
$$

where **POC** is the integrated probability mass (from the PDM) inside the leg footprints; **POD** depends on sensor performance and how tightly tracks are spaced (often parameterized by ($W/S)$). After an unsuccessful search, **Bayesian updates** reduce posterior probability in searched cells and renormalize the remainder—formalized in USCG “Theory of Search.” ([Navcen][3])

### 2.3 Asset allocation (greedy index rule)

Bayesian search theory yields the policy “search next where ($p_i a_i / c_i$) is maximized,” where ($p_i$) is prior probability for cell ($i$), ($a_i$) the single-pass detection probability, and ($c_i$) the cost to search that cell—foundation for **probability-weighted** rather than uniform patterns. ([Wikipedia][5])

---

## 3) Direct application to a first-response UAV around a cruise ship

**Immediate datum**: use the MOB alarm’s **Last-Known Position (LKP)** and ship motion to seed a **short-horizon** particle cloud (minutes scale) with wind/current vectors. This yields a **compact PDM** suited to a UAV’s first sortie. (Identical method; compressed time/space window.) ([U.S. Coast Guard][1])

**Grid selection**: center the initial expanding square or sector on the **PDM centroid**, not the raw LKP. Prioritize legs aligned with the **resultant drift vector** (down-wind/current) to maximize early **POS**. This is consistent with the “search highest probability first” guidance in USCG primers and SAROPS wizards. ([Navcen][3])

**Updating in real time**: each unsuccessful leg reduces the local posterior by factor ($(1-\mathrm{POD})$) and renormalizes the rest; a **verified sighting** collapses the posterior to a tight covariance around the fix. This is the textbook Bayesian update used in maritime search. ([Navcen][3])

**Environmental interop**: where ship connectivity allows, query the same **HYCOM/NCOM winds/currents** used by SAROPS; otherwise ingest **bridge anemometer** and **estimated surface set/drift** from the OOW and inflate diffusion to reflect uncertainty—both approaches are contemplated in SAROPS (manual “sketch” winds/currents). ([U.S. Coast Guard][1])

---

## 4) Parameter ranges and citations suitable for specifications

* **Windage ((\alpha))** for a person at the surface: treated as a small fraction of wind speed (typical SAROPS practice; specific values tuned in calibration). SAROPS documentation describes **leeway** modeling and divergence terms in the Monte-Carlo simulator. ([Wikipedia][6])
* **Particle count/time step**: SAROPS cites up to **10,000 particles per scenario**, updating every ~20 min of drift on long searches; a near-ship UAV planner can use **1–5 s** steps and thousands of particles for a **0–20 min horizon** to reflect rapid early drift. ([Wikipedia][6])
* **Environmental models**: **GFS/NAM winds; HYCOM/NCOM currents; CODAR** where available; uncertainties are explicitly listed by NOAA for SAROPS EDS. ([cdn.ioos.noaa.gov][2])
* **Optimization objective**: **maximize POS** subject to time/fuel, exactly as SAROPS and Stone/Koopman theory prescribe. ([Metron][7])

---

## 5) Reviewer-ready phrasing (citable in a methods section)

* “A **Monte-Carlo drift model** was implemented following the U.S. Coast Guard’s **SAROPS** approach, in which thousands of particles are advected by surface currents plus a windage component with stochastic diffusion; the particle ensemble defines a **probability density map** (PDM) used for **probability-weighted** search planning.” ([U.S. Coast Guard][1])
* “Search legs were prioritized to maximize **$POS = POC × POD$**, per U.S. Coast Guard **Theory of Search** and Stone’s mathematical theory; posterior probabilities were updated by **Bayes’ rule** after each unsuccessful leg.” ([Navcen][3])
* “Environmental inputs (winds/currents) were sourced from the same model families enumerated for SAROPS’ **Environmental Data Server** (GFS/NAM, HYCOM/NCOM, CODAR) or, when unavailable, from bridge instruments with inflated diffusion terms to reflect higher uncertainty.” ([cdn.ioos.noaa.gov][2])

---

## 6) Sources (primary, high-signal)

* **USCG SAROPS info sheet & acquisition page** — Monte-Carlo drift; POS maximization; manual wind/current sketching; ArcGIS integration. ([U.S. Coast Guard][1])
* **Metron SAROPS overview (PDF)** — inputs (winds/currents, visibility, sea state), detectability, survival modeling, and optimization. ([Metron][8])
* **USCG “Theory of Search” primer** — POC, POD, POS; Bayes updates; sweep width concepts. ([Navcen][3])
* **SAROPS components (Wikipedia summary with citations)** — 10,000-particle simulator; probability map outputs; references to Breivik/Allen drift equations. ([Wikipedia][6])
* **NOAA SAROPS environmental data & uncertainties** — HYCOM/NCOM/GFS/NAM/CODAR data sources. ([cdn.ioos.noaa.gov][2])
* **Stone, *Search Theory: A Mathematical Theory for Finding Lost Objects*** — formal treatment of POS maximization and sweep-width search allocation. ([Metron][7])

---

[1]: https://www.dco.uscg.mil/Portals/9/CG-5R/SARfactsInfo/SAROPSInforSheet.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System (SAROPS)"
[2]: https://cdn.ioos.noaa.gov/media/2017/12/sarops_data_sources_uncert_nov2006.pdf?utm_source=chatgpt.com "SAROPS Environmental Data Sources Their Uncertainties"
[3]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf?utm_source=chatgpt.com "The Theory of Search - A Simplified Explanation - navcen"
[4]: https://www.researchgate.net/publication/224218783_Search_and_Rescue_Optimal_Planning_System?utm_source=chatgpt.com "(PDF) Search and Rescue Optimal Planning System"
[5]: https://en.wikipedia.org/wiki/Bayesian_search_theory?utm_source=chatgpt.com "Bayesian search theory"
[6]: https://en.wikipedia.org/wiki/Search_and_Rescue_Optimal_Planning_System?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"
[7]: https://www.metsci.com/wp-content/uploads/2019/08/Search-Theory-A-Mathematical-Theory-for-Finding-Lost-Objects.pdf?utm_source=chatgpt.com "Search Theory"
[8]: https://www.metsci.com/wp-content/uploads/2019/08/Search-and-Rescue-Optimal-Planning-System.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System"
