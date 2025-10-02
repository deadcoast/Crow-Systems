# Evidence Block — Multi-UAV Cooperative Search & Allocation (probability-guided, standards-consistent)

## 1) Search theory foundations that govern asset allocation

* **Sweep width (W)**, **track spacing (S)**, **coverage (C=W/S)**, **Probability of Detection (POD)**, **Probability of Containment (POC)**, and **Probability of Success (POS = POC × POD)** are the controlling quantities in maritime SAR; they drive where to search and how tightly to space tracks. ([navcen.uscg.gov][1])
* Formal search theory (Stone) treats **lateral range curves**, derives **sweep width**, and proves that allocating effort to maximize **POS** is optimal under standard assumptions. ([JSTOR][2])
* **IAMSAR** codifies these constructs for maritime/air SAR and explains the operational search patterns (parallel track, sector, expanding square) with explicit dependence on (W) and (S). ([Maritime Safety Innovation Lab LLC][3])
* 2025 **IAMSAR amendments (MSC.1/Circ.1686)** explicitly write **coverage factor (C = W/S)** for parallel sweeps and define effort factors tied to position error (E); this is current normative language. ([IRI | International Registries, Inc.][4])

**Allocation rule used in practice:** search next where ( \frac{p_i a_i}{c_i} ) is largest (cell prior (p_i); single-pass detection (a_i) from (W,S); cost (c_i) to cover), a direct corollary of Stone’s POS-maximizing framework and the USCG “Theory of Search.” ([JSTOR][2])

---

## 2) Probability maps that drive cooperative coverage (near-ship adaptation)

* Operational planners (USCG **SAROPS**) generate **Monte-Carlo particle probability maps** for drifted positions and allocate search to maximize **POS**; the same logic applies on short horizons around a last-known position. ([navcen.uscg.gov][1])
* Recent multi-UAV research implements **probability-weighted tasking**:

  * **POC-based area division & trajectories** (probability-of-containment maps → partition + tracks). ([MDPI][5])
  * **POS-weighted deep RL for maritime SAR** (assets learn to prioritize high-probability cells, avoid overlap). ([MDPI][6])
  * **Cooperative coverage with differential-evolution optimization** (multi-UAV coverage under heterogeneous regions). ([PMC][7])

**Conclusion:** probability-map–aware partitioning and routing is state-of-the-art in the academic SAR and coverage literature and mirrors SAROPS doctrine. ([MDPI][6])

---

## 3) Proven partitioning methods to avoid duplication and minimize time

* **DARP (Divide Areas Algorithm)** guarantees **non-overlapping, fully covered** sub-areas per robot with balanced workload; widely cited for multi-robot coverage. ([SpringerLink][8])
* Variants and recent surveys confirm DARP-style partitioning minimizes **total coverage time** under heterogeneous regions/agents when paired with local lawnmower/parallel tracks within each sub-area. ([MDPI][9])

**Direct implication:** partition the probability map into sub-areas whose **integrated probability mass** (or expected POS gain) per sub-area is balanced across UAVs, then apply parallel-track or expanding-square within each sub-area to achieve high **coverage factor (C=W/S)** with **zero overlap**. ([IRI | International Registries, Inc.][4])

---

## 4) Multi-UAV coverage math (citable, binder-ready)

### 4.1 Coverage & POS for one sub-area

For a rectangular sub-area ($A_k$) assigned to UAV (k) with parallel-track spacing ($S_k$) and sweep width ($W_k$):
$$
C_k = \frac{W_k}{S_k}, \qquad POD_k = f(C_k,,\text{visibility/sea state}), \qquad POS_k = \underbrace{\int_{A_k} p(\mathbf{x}),d\mathbf{x}}_{\text{POC}_k} \times POD_k.
$$
(IAMSAR uses ($C=W/S$); USCG theory provides ($POD=f(C)$) tables/curves.) ([IRI | International Registries, Inc.][4])

### 4.2 Time to cover and duplication constraint

Let effective lane width be ($W_e$) (from camera HFOV/altitude and overlap). With groundspeed ($v_k$), the **area-rate** ($R_k = v_k W_{e,k}$). Time to sweep ($A_k$) once: ($T_k = A_k/R_k$). **No-overlap** is enforced by partitioning (e.g., DARP), guaranteeing ($\sum_k A_k = A$) and eliminating redundant passes. ([SpringerLink][8])

### 4.3 Optimal partition objective (POS-balanced workload)

Choose ($A_k$) to solve
$$
\max_{ {A_k},, {S_k} } \sum_{k=1}^m POS_k \quad \text{s.t.} \quad T_k \le T^*, ; A_i \cap A_j = \varnothing.
$$
A practical surrogate: equalize **expected POS gain per minute** across UAVs (greedy Stone-style index ($p_i a_i/c_i)$) and set ($S_k$) so ($C_k$) meets target **POD** from IAMSAR/USCG tables. ([JSTOR][2])

---

## 5) Current, citable guidance for (W,S,C) and corrections

* **IAMSAR/USCG** provide **POD vs. coverage** tables and sweep-width estimation methods; updated guidance includes **correction factors** for night/visibility and target types. ([United States Coast Guard][10])
* 2020 validation work (Koester) details **new sweep widths** and **condition corrections** for visual SAR, which can be adapted to EO/IR by calibration. ([Journal of Search and Rescue][11])
* **2025 IAMSAR amendments** (MSC.1/Circ.1686) clarify **coverage factor** usage and **effort factor** for point/line datums; directly quotable for methods sections. ([IRI | International Registries, Inc.][4])

---

## 6) Evidence that multi-asset probability-guided SAR outperforms uniform search

* **Maritime SAR (vessels)**: recent path-planning frameworks for multiple PIWs show **reduced total search time** vs. parallel-line baselines when probability maps inform allocation. ([ScienceDirect][12])
* **USVs for maritime SAR**: **POS-weighted RL** prioritizes high-probability regions first and reduces **repeated coverage**, improving efficiency in simulations and field-style trials. ([MDPI][6])
* **UAV swarms**: MAPPO-based cooperative search and DE-based cooperative coverage show **higher coverage rate** and **lower time-to-detection** on dynamic targets vs. naive patterns. ([MDPI][13])

---

## 7) What belongs in a research binder (standards-aligned, with citations)

* **Method statement:** “A **probability-map–guided multi-UAV search** was executed. The search area was partitioned by a DARP-class algorithm to eliminate duplication, then each UAV flew **IAMSAR-compliant parallel tracks** with track spacing (S) set to achieve coverage ($C = W/S$) meeting the desired **POD**. Allocation followed a Stone-style index ($p_i a_i / c_i$) to maximize **POS** under time constraints.” ([SpringerLink][8])
* **Parameter sourcing:** “Sweep width (W) and **POD vs C** curves were taken from **USCG/IAMSAR tables** with condition corrections (night/visibility) per Koester (2020).” ([United States Coast Guard][10])
* **Rationale:** “Probability-guided allocation is consistent with **SAROPS** and recent **multi-asset SAR** literature demonstrating efficiency and earlier detections vs uniform coverage.” ([navcen.uscg.gov][1])

---

## 8) Sources (high-signal)

* **IAMSAR Manual, Vol III (Mobile Facilities)** — sweep width, track spacing, patterns. ([Maritime Safety Innovation Lab LLC][3])
* **MSC.1/Circ.1686 (2025 IAMSAR amendments)** — current formulae for **coverage (C=W/S)** and effort factors. ([IRI | International Registries, Inc.][4])
* **USCG “Theory of Search”** — POD/POC/POS definitions, Bayes updates. ([navcen.uscg.gov][1])
* **Stone (1977; book-length compendium)** — mathematical optimization of search, lateral range curves, sweep width. ([JSTOR][2])
* **POS-weighted maritime SAR planning (USVs)** — MDPI 2024 (POS-DQN). ([MDPI][6])
* **Multi-UAV cooperative coverage (DE algorithm)** — MDPI 2024 (open access). ([PMC][7])
* **DARP algorithm** — multi-robot non-overlapping area division, time minimization. ([SpringerLink][8])
* **Sweep-width corrections/validation** — Journal of Search & Rescue (2020). ([Journal of Search and Rescue][11])

---

[1]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf?utm_source=chatgpt.com "The Theory of Search - A Simplified Explanation - navcen"
[2]: https://www.jstor.org/stable/2689530?utm_source=chatgpt.com "A Mathematical Theory for Finding Lost Objects"
[3]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2021/02/Doc.9731-EN-IAMSAR-Manual-International-Aeronautical-and-Maritime-Search-and-Rescue-Manual-Volume-III-Mobile-Facilities.pdf?utm_source=chatgpt.com "IAMSAR MANUAL"
[4]: https://www.register-iri.com/wp-content/uploads/MSC.1-Circ.1686.pdf?utm_source=chatgpt.com "MSC.1/Circ.1686 27 January 2025 AMENDMENTS TO THE INTERNATIONAL AERONAUTICAL AND MARITIME SEARCH AND RESCUE (IAMSAR) MANUAL 1 Th"
[5]: https://www.mdpi.com/2504-446X/8/4/132?utm_source=chatgpt.com "UAV Swarm Search Path Planning Method Based on ..."
[6]: https://www.mdpi.com/2077-1312/12/7/1158?utm_source=chatgpt.com "USVs Path Planning for Maritime Search and Rescue ..."
[7]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11274647/?utm_source=chatgpt.com "Multi-UAV Cooperative Coverage Search for Various ..."
[8]: https://link.springer.com/article/10.1007/s10846-016-0461-x?utm_source=chatgpt.com "DARP: Divide Areas Algorithm for Optimal Multi-Robot ..."
[9]: https://www.mdpi.com/2076-3417/13/14/8207?utm_source=chatgpt.com "Area Division Using Affinity Propagation for Multi-Robot ..."
[10]: https://www.dco.uscg.mil/Portals/9/CG-5R/nsarc/DetExpReport_2004_final_s.pdf?utm_source=chatgpt.com "Sweep Width Estimation for Ground Search and Rescue - dco.uscg.mil"
[11]: https://journalofsar.com/wp-content/uploads/2020/04/v4-7-Koester-POD-Syrotuck.pdf.pdf?utm_source=chatgpt.com "New sweep widths values, correction factors, models, and ..."
[12]: https://www.sciencedirect.com/science/article/abs/pii/S0029801823027877?utm_source=chatgpt.com "An autonomous coverage path planning algorithm for ..."
[13]: https://www.mdpi.com/2504-446X/8/6/214?utm_source=chatgpt.com "UAV Swarm Cooperative Dynamic Target Search"
