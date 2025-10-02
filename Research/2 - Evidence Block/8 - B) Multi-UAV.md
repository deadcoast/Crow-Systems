# Worked Example — Probability-Guided Multi-UAV Search (IAMSAR/USCG-consistent)

## 1) Problem setup (numbers fixed for calculation)

* **Search datum:** last-known position ($LKP$) at ($t_0$); initial **search area** ($A=\pi r^2$) with ($r=600\ \text{m}$) ⇒ ($A = 1{,}130{,}973\ \text{m}^2$).
* **Sensor/platform:** LWIR payload ($640×512$) on a maritime multirotor flying **($v=15\ \text{m/s}$)** at **($H=120\ \text{m}$)**. Horizontal FOV ≈ ($33^\circ$) (from DFOV $40.6°$ H20T spec), giving geometric swath ($W_{\text{geom}} \approx 71.1\ \text{m}$). For conservative **sweep width** in search-theory terms (IAMSAR: *“measure of sensor effectiveness”*), take ($W=57\ \text{m}$) ($≈ 80$% of geometric swath to reflect detection fall-off) at night. ([Maritime Safety Innovation Lab LLC][1])
* **Coverage factor:** IAMSAR defines **($C=\dfrac{W}{S}$)** for parallel-track searches (sweep width (W), track spacing (S)). ([Maritime Safety Innovation Lab LLC][1])
* **POD at ($C=1$):** RNLI/MCA planning note cites **POD $≈ 79$%** when ($W=S$) (i.e., ($C=1$)). (Used here as the operating point.) ([Cranston Inquiry][2])
* **Assets:** two identical UAVs (UAV-A, UAV-B) flying **disjoint** sub-areas (no overlap), partitioned by a coverage algorithm (e.g., **DARP**) to eliminate duplication and balance workload. ([SpringerLink][3])
* **Probability map:** short-horizon Monte-Carlo drift (SAROPS-style) yields a unimodal probability density centered down-wind; assume **right half contains 60%** of total probability mass and **left half 40%** (quantified example of a PDM). ([DCO USCG][4])

---

## 2) Time to cover once at (C=1) (IAMSAR geometry)

For parallel tracks, the **track length** needed to cover area ($A$) at spacing ($S$) is ($L = \dfrac{A}{S}$). Flight **time** for one UAV at ground speed ($v$):
$$
T ;=; \frac{L}{v} ;=; \frac{A}{v,S}.
$$
At **($C=1$)**, set ($S=W=57\ \text{m}$). For **one UAV**:
$$
T_{1} ;=; \frac{1{,}130{,}973}{15 \times 57};=;1{,}322\ \text{s};\approx;22.0\ \text{min}.
$$
With **two UAVs** covering **disjoint halves** (each ($A/2$)):
$$
T_{2} ;=; \frac{A/2}{v,W};=;\frac{1{,}130{,}973/2}{15 \times 57};=;661\ \text{s};\approx;11.0\ \text{min}.
$$
(Definitions: **coverage factor ($C=W/S$)** and parallel-track geometry per IAMSAR Vol III & 2025 amendment; **sweep width** definition per IAMSAR.) ([Maritime Safety Innovation Lab LLC][1])

---

## 3) Expected Probability of Success (POS) after one full sweep

USCG search theory uses **$POS = POC × POD$**, where **POC** is the integrated probability mass in the searched region and **POD** is the single-pass probability of detection at the chosen **coverage ($C$)**. ([Navigation Center][5])

* With **($C=1$)** (i.e., ($S=W$)), take **($POD \approx 0.79$)** (RNLI/MCA empirical operating point). ([Cranston Inquiry][2])
* **Full-area single sweep** (two UAVs in $~11 min$): ($POC = 1.0 \Rightarrow POS \approx 0.79$).

If **only the high-probability half** (right side) is swept first (workload balanced by **probability mass** using DARP-style partitioning), then after **$~5.5 min$**:

* ($POC \approx 0.60$) (since that sub-area holds 60% of the PDM), so ($POS \approx 0.60 \times 0.79 = 0.474$), **before** any search of the remaining half.
  This **front-loads POS** into the highest-probability region, following SAROPS/Stone guidance to search where ( $\tfrac{p_i a_i}{c_i}$) is largest. ([DCO USCG][4])

---

## 4) Within a fixed time budget (T^*) (e.g., 6 minutes): probability-weighted allocation

Available **time** ($T^*=360\ \text{s}$). With ($S=W$) and **two UAVs**, total area covered is:
$$
A_{\text{cov}} ;=; (v S) \times T^* \times 2 ;=; (15\times 57)\times 360 \times 2 ;=; 615{,}600\ \text{m}^2.
$$
This is **$54.4$%** of ($A$). Assign **all coverage** to the **highest-probability region** first (probability-weighted partition). If the right half contains **$60$%** of probability but only **$50$%** of area, the first **($0.5A$)** swept yields ($POC=0.60$). The remaining **($0.044A$)** must come from the left half (probability density $≈ 0.8×$ the right by construction), contributing **($0.8 \times 0.044 = 0.035$)** probability.
**Total ($POC \approx 0.60 + 0.035 = 0.635$)** in **6 minutes**, giving
$$
POS ;\approx; 0.635 \times 0.79 ;=; 0.502.
$$
Thus, **half the final one-sweep POS** is achieved in **$~27$%** of the full-sweep time by **searching the PDM peak first**. (Methodological basis: SAROPS Monte-Carlo PDM → POS maximization; IAMSAR geometry; USCG “Theory of Search”.) ([DCO USCG][4])

---

## 5) Sensitivity to track spacing (changing (C))

Track spacing ($S$) trades **time vs POD**:

* **Tighter spacing** ($S=0.8W \Rightarrow C=1.25$). Using standard **POD vs ($C$)** curves (USCG/IAMSAR), POD increases (empirical curves; RNLI note gives $79$% at ($C=1$) as a reference point). Time increases inversely with ($S$): ($T \propto \tfrac{1}{S}$).
* **Looser spacing** ($S=1.25W \Rightarrow C=0.8$). Time falls by $20$%, but POD drops per the curve.
  Quantitative ($POD(C)$) is table/curve-driven in IAMSAR/USCG materials; planners select ($S$) to meet target $POD$ for conditions, then compute ($T$) from (A/(vS)). ([Maritime Safety Innovation Lab LLC][1])

Example (one UAV, ($A=1.131\ \text{km}^2), (v=15\ \text{m/s}), (W=57\ \text{m})$):

* $(S=W) → (T=22.0\ \text{min}), POD ≈ 0.79$.
* $(S=0.8W) → (T=27.5\ \text{min}), POD > 0.79$ (per tables).
* $(S=1.25W) → (T=17.6\ \text{min}), POD < 0.79$.

---

## 6) No-overlap partitioning (why multi-UAV efficiency holds)

Coverage duplication wastes time and reduces POS gain per minute. **DARP** (Divide Areas Algorithm) provides **non-overlapping** partitions with balanced workload even in irregular regions/obstacles; it is widely cited for multi-robot coverage optimality. Applying DARP to the **probability map** (rather than area alone) equalizes **expected POS gain per minute** across UAVs and prevents re-searching the same lanes. ([SpringerLink][3])

---

## 7) Standards and doctrine ties (verbatim anchors for reports)

* **Coverage factor definition:** “**Coverage factor ($C$) … For parallel track searches, it may be computed as the ratio of sweep width ($W$) to track spacing ($S$). $C = W / S$.**” (IAMSAR Vol III; 2025 amendment MSC.1/Circ.1686.) ([Maritime Safety Innovation Lab LLC][1])
* **POS identity and search logic:** USCG **“Theory of Search – A Simplified Explanation”** (POD/POC/POS, lateral range, sweep width). ([Navigation Center][5])
* **Probability-map planning:** **SAROPS** is the USCG’s **Monte-Carlo** drift and POS-maximizing planner (probability maps, multiple scenarios, asset assignment). ([DCO USCG][4])

---

## 8) What the worked example demonstrates (numerical conclusions)

1. **Full one-pass coverage at ($C=1$)** requires **$≈22 min$** (one UAV) or **$≈11 min$** (two UAVs) for a 600 m-radius cell, given ($v=15\ \text{m/s}$) and ($W=57\ \text{m}$). (IAMSAR geometry.) ([Maritime Safety Innovation Lab LLC][1])
2. **Expected ($POS$) after one pass** at ($C=1$) is **$≈0.79$**, using the RNLI/MCA empirical $POD$ at ($C=1$). ([Cranston Inquiry][2])
3. **Probability-weighted first coverage** (PDM peak first) yields **($POS \approx 0.50$)** in **6 min** with two UAVs, by concentrating early effort where **($p_i$)** is largest—formal SAROPS/Stone doctrine. ([DCO USCG][4])
4. **Track-spacing ($S$)** is the primary lever: decreasing ($S$) (raising ($C$)) increases **$POD$** but increases **time**; loosening it does the reverse—trade studies are done with IAMSAR ($POD(C)$) tables, then executed via DARP-style partitioning to avoid duplication. ([Maritime Safety Innovation Lab LLC][1])

---

## Sources

* **IAMSAR Manual, Vol III (Mobile Facilities)** — definitions; **($C=W/S$)**; search-pattern geometry. ([Maritime Safety Innovation Lab LLC][1])
* **MSC.1/Circ.1686 (2025 IAMSAR amendments)** — current coverage-factor wording and related definitions. ([IRI | International Registries, Inc.][6])
* **USCG – “Theory of Search: A Simplified Explanation”** — $POD/POC/POS$, sweep width, lateral-range concepts. ([Navigation Center][5])
* **USCG SAROPS (info sheet & technical review)** — Monte-Carlo particle probability maps and POS maximization for asset tasking. ([DCO USCG][4])
* **DARP – Divide Areas Algorithm** — non-overlapping multi-robot coverage with balanced workload. ([SpringerLink][3])
* **RNLI/MCA planning note** — empirical **$POD ≈ 79$% at ($C=1$)** used as a planning anchor. ([Cranston Inquiry][2])

[1]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2021/02/Doc.9731-EN-IAMSAR-Manual-International-Aeronautical-and-Maritime-Search-and-Rescue-Manual-Volume-III-Mobile-Facilities.pdf?utm_source=chatgpt.com "IAMSAR MANUAL"
[2]: https://cranston.independent-inquiry.uk/wp-content/uploads/cranston-evidence/INQ000655_RNLI_MCA_agreement_on_search_and_rescue__SAR__operations_and_planning_provided_by_RNLI_01_11_2010.pdf?utm_source=chatgpt.com "INQ000655/1 - The Cranston Inquiry"
[3]: https://link.springer.com/article/10.1007/s10846-016-0461-x?utm_source=chatgpt.com "DARP: Divide Areas Algorithm for Optimal Multi-Robot ..."
[4]: https://www.dco.uscg.mil/Portals/9/CG-5R/SARfactsInfo/SAROPSInforSheet.pdf?utm_source=chatgpt.com "Search and Rescue Optimal Planning System (SAROPS)"
[5]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf?utm_source=chatgpt.com "The Theory of Search - A Simplified Explanation - navcen"
[6]: https://www.register-iri.com/wp-content/uploads/MSC.1-Circ.1686.pdf?utm_source=chatgpt.com "MSC.1/Circ.1686 27 January 2025 AMENDMENTS TO ..."
