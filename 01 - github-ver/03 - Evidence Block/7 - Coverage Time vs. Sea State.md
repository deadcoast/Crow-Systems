# Evidence Block — Coverage Time vs. Sea State & Platform Envelope #

## 1) Sea state & wind definitions used in modeling ##

- **WMO Sea State Code (Table 3700):** wave height bands: Slight 0.5–1.25 m (SS 3); Moderate 1.25–2.5 m (SS 4); Rough 2.5–4 m (SS 5); Very rough 4–6 m (SS 6). ([NODC][1])
- **Beaufort descriptors:** e.g., Beaufort 5 “Fresh Breeze” $≈ 17–21 kt$; “many white horses (whitecaps)” with some spray. ([Weather.gov][2])
- WMO notes: “Sea state specifies **wave height**; Beaufort specifies **wind speed**.” Use both to parameterize conditions. ([community.wmo.int][3])

## 2) UAV maritime operating envelope (representative, cited) ##

- **DJI Matrice 300 RTK**: **Max wind resistance $~12 m/s$**, **IP45**, manufacturer cautions against heavy rain ($> 100 mm/24 h$). ([DJI Official][4])
- Independent spec summaries list **max wind resistance $≈ 33.5 mph$ (15 m/s)** and $~55 min$ endurance (configuration dependent). ([Dominion Drones www.dominiondrones.com][5])
- Vendor guidance stresses weather resistance yet urges judgment in precipitation and gusts. ([Enterprise Insights][6])
  **Envelope translation:** credible continuous ops up to **Beaufort 6–7** in laminar flow are unlikely; **Beaufort 5–6** with gusts already challenges small multirotors near ship wakes and superstructure.

## 3) Sensor range degradation in rain/fog (thermal) ##

- **LWIR vs weather:** thermal imaging penetrates darkness/light fog, but **range degrades markedly** with increasing droplet density (scattering/absorption); LWIR generally outperforms MWIR in fog, yet **rain reduces range**. ([Flir][7])
- **Absorption physics:** water vapor and CO₂ attenuate IR; MWIR “$5–8 µm$” band is “unusable” due to $H₂O$ absorption; LWIR ($8–12 µm$) is the practical maritime window, still limited by humidity/precipitation. ([Regulations.gov][8])

## 4) Search-theory linkage: sweep width, POD, POS ##

- **USCG search theory:** Probability of Success **$POS = POC × POD$**; **$POD$** depends on **sweep width W** and **track spacing S** (sensor/condition dependent). Bayesian updates reduce probability in searched cells after each leg. ([navcen.uscg.gov][9])
- **IAMSAR & SAR experiments:** decades of Coast Guard experiments underpin **sweep-width tables** used in IAMSAR; detection effectiveness degrades as environment worsens (sea state/visibility). ([United States Coast Guard][10])

## 5) Parametric coverage model (grounded in FOV physics & SAR terms) ##

**Geometry (example: $640×512$ LWIR, DFOV $40.6°$, HFOV$≈33°$):** swath ($W=2H\tan(\frac{\text{HFOV}}{2})$); effective lane ($W_e = k\cdot W$) (overlap ($k≈0.8$)). **Area rate** ($ACR = v\cdot W_e$). (Camera spec basis.) ([NODC][1])

**Condition modifiers:**

- **Wind/Sea-State speed derate:** ($v_{\text{eff}} = v_0 \cdot (1-\delta_v$)), where ($\delta_v$) grows with Beaufort (gust handling). Bound by **max wind resistance** spec. ([DJI Official][4])
- **Thermal range derate in rain/fog:** implement a **POD multiplier** ($m_{\text{wx}}\in(0,1]$) derived from LWIR attenuation guidance (fog/rain → reduced effective sweep width). ([Flir][7])
- **Pixels-on-target constraint:** enforce altitude cap s.t. **GSD** maintains $≥ ~2–3 px$ across the head/shoulders for detection (Johnson), or ≥ ~6 px for robust CNN features. (Use Johnson/IFOV tables from prior block.) ([navcen.uscg.gov][9])

**Illustrative example (calm → SS 5):**

- **Baseline ($SS 3, ~10–12 kt$, dry air):** ($H=120,\text{m}), (v_0=15,\text{m/s}) → (W_e≈56.9,\text{m}) → (ACR≈852,\text{m}^2/\text{s}$). A 600 m radius cell (~1.13 km²) sweeps in **$≈22$ min**; two UAVs: **$≈11$ min**.
- **SS 5, Beaufort 5 (17–21 kt), whitecaps + light spray):** set ($\delta_v≈0.2$) (gust handling) and ($m_{\text{wx}}≈0.8$) (visibility/thermal range hit), yielding **effective $ACR ≈ 852×0.8×0.8 ≈ 546 m²/s$** → sweep **$≈34$ min** (one UAV) / **$≈17 min$** (two). Whitecaps also reduce **per-pass POD**, requiring **tighter spacing** (S) to sustain equivalent **POS**. (Beaufort descriptors; POD dependence per USCG theory.) ([Weather.gov][2])

## 6) Practical thresholds to state in a research binder ##

- **Operate ≤ Beaufort 5** for primary night-search metrics; above this, record **derated speed** and **raised altitude constraints** explicitly; abort criteria aligned to **wind resistance spec**. ([DJI Official][4])
- **Document POD multipliers** for fog/drizzle vs. rain (cite LWIR attenuation guidance) and apply as **sweep-width reductions** in reports. ([Flir][7])
- **Sea state reporting:** log **WMO sea state code** plus **Beaufort** for every sortie to normalize POD comparisons across trials. ([NODC][1])

## 7) Reviewer-facing sentences (ready to drop) ##

- “Operations were limited to conditions not exceeding the platform’s published **wind resistance and IP rating**; sorties executed primarily in **WMO Sea State ≤ 5** (Beaufort ≤ 5–6).” ([DJI Official][4])
- “**Sweep width** and **POD** were adjusted by environment using USCG **Theory of Search** constructs; fog/rain **reduced effective sweep width** in accordance with LWIR attenuation guidance.” ([navcen.uscg.gov][9])
- “Sea state was logged using **WMO Code Table 3700**; wind using **Beaufort**; these jointly parameterized coverage and detection performance.” ([NODC][1])

**Sources:** WMO Code Table 3700; NWS Beaufort page; WMO marine FAQ; DJI M300 RTK support (wind/IP); DJI/M300 weather resistance overview; FLIR LWIR fog/rain note; NOAA/USCG search-theory/IAMSAR materials. ([NODC][1])

[1]: https://www.nodc.noaa.gov/gtspp/document/codetbls/wmocodes/table3700.html "About WMO Code Table 3700"
[2]: https://www.weather.gov/pqr/beaufort "Beaufort Scale"
[3]: https://community.wmo.int/en/activity-areas/Marine/About/FAQs "Marine Frequently Asked Questions"
[4]: https://www.dji.com/support/product/matrice-300 "Support for Matrice 300 RTK"
[5]: https://www.dominiondrones.com/pages/dji-matrice-300-rtk-specifications?srsltid=AfmBOoouVY4rWIDX9LEaKNKUSOC0KBdlYDY6A86Y2NKwNqxNbsIyqess&utm_source=chatgpt.com "DJI Matrice 300 RTK Specifications"
[6]: https://enterprise-insights.dji.com/blog/matrice-300-weather-resistance "Just How Weather Resistant is the Matrice 300 RTK? - Insights"
[7]: https://www.flir.com/discover/rd-science/can-thermal-imaging-see-through-fog-and-rain/?srsltid=AfmBOoqKYXqYP0E0yB-vp0jSLfpyeL_zEv4yXHc0Wzz6w-19VvJO3IaO&utm_source=chatgpt.com "Can Thermal Imaging See Through Fog and Rain?"
[8]: https://downloads.regulations.gov/NOAA-NMFS-2016-0008-0019/attachment_10.pdf "COMPARISON OF MEDIUM AND LONG WAVE ..."
[9]: https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf "The Theory of Search - A Simplified Explanation - navcen"
[10]: https://www.dco.uscg.mil/Portals/9/CG-5R/nsarc/LSA%20-%20Simple%20Design%20Volume%20II%20Appendixes%205-20-06.pdf "A Simple Guide to Conducting Ground Search and Rescue ..."
