# Evidence Block — Night/Low-Light Person-in-Water Detection: Sensor ROC, Pixel-Footprint vs Altitude, False-Positive Modes (with sources)

## 1) Peer-reviewed nighttime detection performance (thermal video, people in water)

* **Enhanced YOLOv5s on thermal imagery (2024):** “Personnel Detection in Dark Aquatic Environments” reports **accuracy 85.49% at 23.51 FPS** for nighttime **water-person** detection using infrared thermal video and a lightweight CNN; includes precision/recall/ROC analyses on aquatic scenes (immersed subjects, waves). ([PMC][1])

**Direct use:** establishes that **real-time (~20–30 FPS) thermal detection of immersed humans at night** is feasible on embedded hardware, and provides ROC operating points suitable for threshold selection in specs and trials. ([PMC][1])

---

## 2) Pixels-on-target requirements (Johnson/IFOV) to set altitude limits

* **Johnson’s criteria** (empirical thresholds) state that, for **50% detection probability**, observers need roughly **~1 line pair** across the target (≈ **2 pixels**), with higher pixel counts needed for recognition/ID; criteria are widely used to bound detection vs. range/altitude. ([Wikipedia][2])
* **IFOV/GSD relationships** from thermal-imaging notes (FLIR/Leonardo DRS) tie **field of view, distance, and pixel pitch** to **ground sample distance (GSD)**; industry guidance often maps analytics requirements to **minimum pixels across target** (e.g., ~**6 px/m** cited as a practical analytics threshold comparable to Johnson recognition). ([flirmedia.com][3])

**Direct use:** translates camera/lens choice and altitude into **expected pixels across a head-and-shoulders target**; combine with ROC from thermal studies to pick safe **altitude bands** for night search.

---

## 3) Altitude → swath → pixels-across target (example with cited specs)

**Camera:** DJI **Zenmuse H20T** thermal (uncooled VOx, **640×512 @ 30 Hz**, **DFOV 40.6°**, **NETD ≤ 50 mK**). HFOV derived from manufacturer DFOV for 4:3 sensor ≈ **33°**. ([Optron][4])

**Formulas:**

* Swath width (W = 2H \tan(\text{HFOV}/2))
* **GSD** (= W / 640) (m/pixel, horizontal)
* Pixels across a **0.5 m** target (= 0.5 / \text{GSD})

**Computed table (20% lane overlap accounted in effective lane width (W_e)):**

| Altitude (H) | Swath (W) (m) | (W_e) (m) | GSD (m/px) | Pixels across 0.5 m |
| -----------: | ------------: | --------: | ---------: | ------------------: |
|         60 m |         35.55 |     28.44 |     0.0555 |         **9.00 px** |
|         90 m |         53.32 |     42.65 |     0.0833 |         **6.00 px** |
|        120 m |         71.09 |     56.87 |     0.1111 |         **4.50 px** |
|        150 m |         88.86 |     71.09 |     0.1389 |         **3.60 px** |
|        200 m |        118.49 |     94.79 |     0.1851 |         **2.70 px** |

**Interpretation (with Johnson/analytics guidance):**

* **≤90 m** altitude keeps **≥6 px** across a 0.5 m head-and-shoulders target—comfortably above bare detection and closer to recognition-grade pixel density for robust CNN performance. ([Wikipedia][2])
* **120–150 m** yields **~3.6–4.5 px**; still within **detection** envelope, but increased risk of missed/fragmentary detections in chop—ROC thresholding should bias to **recall** at these heights. ([PMC][1])
* **200 m** (~2.7 px) approaches **minimum detection**; use only when coverage takes priority over per-frame confidence. ([Wikipedia][2])

**Camera alternatives (to extend altitude without losing pixels):** Teledyne FLIR **Boson 640** lenses with **narrower HFOV** (e.g., **12°**, **8°**) increase pixels-on-target at altitude; published HFOV options: **50°**, **32°**, **12°**, **8°**. ([flircameras.com][5])

---

## 4) Coverage-time vs. altitude (derived from swath & speed)

For H20T HFOV ≈ 33°, **effective lane width (W_e)** scales linearly with altitude; **area-coverage rate** (= v \times W_e).

At **120 m** with **v = 15 m/s**, (W_e ≈ 56.9) m → **~852 m²/s**. A **600 m-radius** initial search cell (≈1.13 km²) sweeps in ≈**22 min** with one UAV; ≈**11 min** with two, assuming uniform distribution and constant POD per pass. Use **≤90 m** where **pixels-on-target** must be maximized (night/chop), trading longer sweep time for higher per-frame POD. Camera specs and FOV above; coverage math follows standard IFOV/GSD relations. ([Optron][4])

---

## 5) False-positive (FPR) modes over water and literature-backed mitigations

* **Whitecaps/foam/glare** are recurrent sources of false alarms. Remote-sensing and ocean-imaging literature explicitly analyzes **whitecap detection** and proposes filters to suppress **false positives under varying illumination and light pollution**, confirming the confusability of bright crests and foam structures. ([MDPI][6])
* **Mitigations supported by studies and vendor practice:**

  1. **Temporal filtering / motion continuity** (reject transient crests not persisting across frames). ([PMC][1])
  2. **Size/shape gating** (exclude large, elongated/irregular foam patches outside human aspect priors). ([PMC][1])
  3. **Thermal-RGB fusion** (reduce glare artifacts while keeping IR recall at night). ([PMC][1])
  4. **Altitude discipline** (maintain ≥6 px across target at night—see §3 table—to stabilize CNN features and lower FPR at operating thresholds). ([Leonardo DRS][7])

---

## 6) What belongs in a spec/trials binder (numbers and citations)

* **Operating ROC**: adopt thresholds from the **YOLOv5s thermal water-person** paper that yield **≥0.8 recall** at night; replicate ROC on proprietary harbor dataset before sea trials. ([PMC][1])
* **Altitude bands (night):** **≤90 m** preferred (≥6 px across 0.5 m head-shoulders), **120–150 m** acceptable with recall-biased thresholds; **200 m** only when coverage must dominate. (Table above; Johnson/IFOV sources.) ([Wikipedia][2])
* **Lens selection:** for higher altitudes or larger standoff, select **Boson 640 lenses 12°–8° HFOV** to maintain ≥6 px across target while increasing swath modestly; document HFOV per lens. ([flircameras.com][8])
* **FPR controls:** implement temporal continuity + aspect gating; document suppression of whitecap/glare via examples and cite whitecap-detection literature in methods. ([MDPI][6])

---

## Citations

* **Thermal water-person detection (night)**: YOLOv5s-IR, **85.49% accuracy @ 23.51 FPS**; ROC/precision-recall curves for aquatic scenes. ([PMC][1])
* **Johnson criteria** (pixels across target for detection/recognition/ID). ([Wikipedia][2])
* **IFOV/GSD** derivations and analytics pixel thresholds (FLIR note; Leonardo DRS range note). ([flirmedia.com][3])
* **H20T thermal specs** (640×512 @ 30 Hz; **DFOV 40.6°**; NETD ≤ 50 mK). ([Optron][4])
* **Boson 640 HFOV options** (50°, 32°, 12°, 8° lens SKUs and datasheets). ([flircameras.com][5])
* **Whitecap/foam false positives** and suppression methods under varying illumination; coastal imagery analyses. ([MDPI][6])

---

**Next block ready on command:** **Coverage-time modeling across sea states** (wind/swell effects on platform envelope and POD), or **multi-UAV cooperative search math** (POS maximization under particle-map priors).

[1]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11175020/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."
[2]: https://en.wikipedia.org/wiki/Johnson%27s_criteria?utm_source=chatgpt.com "Johnson's criteria"
[3]: https://flirmedia.com/MMC/THG/Brochures/17-1465/17-1465_US.pdf?utm_source=chatgpt.com "TECHNICAL NOTE - flir"
[4]: https://optron.com/dji/wp-content/uploads/2020/05/ds_zenmuse-h20-series.pdf?utm_source=chatgpt.com "zenmuse h20 series"
[5]: https://www.flircameras.com/product/flir-boson-640x480-8mm-htm/?utm_source=chatgpt.com "Teledyne FLIR BOSON 640 x 512 8.7mm 50° HFoV"
[6]: https://www.mdpi.com/2072-4292/14/22/5691?utm_source=chatgpt.com "Using Optical Flow Trajectories to Detect Whitecaps in ..."
[7]: https://www.leonardodrs.com/wp-content/uploads/2023/08/201705_truth_about_rangedata_mr-2014-10-683_rev02.pdf?utm_source=chatgpt.com "HOW TO ASSESS THERMAL CAMERA RANGE ..."
[8]: https://www.flircameras.com/product/flir-boson-640x480-36mm-htm/?utm_source=chatgpt.com "Teledyne FLIR BOSON 640 x 512 36mm 12° HFoV"
