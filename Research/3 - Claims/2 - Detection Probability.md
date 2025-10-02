# CLAIM — “Detection probability (Pdet) is high with low false positives.”

## A. Independent evidence (literature & datasets)

---

### 1) Night detection (thermal/LWIR) of people in water

* Peer-reviewed study (2024) trained an enhanced YOLOv5s on **5,736 thermal images** of waterborne persons and achieved **real-time inference (~23.5 FPS)** with **high detection accuracy** in dark aquatic environments; paper reports precision/recall curves suitable for ROC thresholding. This directly supports nighttime feasibility on embedded hardware. ([PubMed][1])([PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC11175020/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."))

### 2) Day detection (RGB) in open water with clutter

* **SeaDronesSee (WACV 2022)** is a large, open benchmark focused on **detecting humans in open water** from UAVs. It contains **>54,000 frames / ~400,000 instances**, with meta-data for **altitude (5–260 m)** and **view angle (0–90°)**; the paper and site provide baseline models and public leaderboards for AP/PR curves. This is the **standard daytime evidence base** to demonstrate detection performance under glare, chop, and distance. ([CVF Open Access](https://openaccess.thecvf.com/content/WACV2022/html/Varga_SeaDronesSee_A_Maritime_Benchmark_for_Detecting_Humans_in_Open_Water_WACV_2022_paper.html?utm_source=chatgpt.com "SeaDronesSee - WACV 2022 Open Access Repository"))

### 3) False-positive sources are known and quantifiable

* **Whitecaps/sea foam** are the dominant maritime visual confusers. Ocean-physics studies relate **whitecap coverage** to **wind speed/sea state** with empirical laws (e.g., Brumer et al. 2017; Schwendeman et al. 2015), giving a defensible explanation for **FPR increases with Beaufort** and supplying parameters for scenario modeling. ([American Meteorological Society Journals](https://journals.ametsoc.org/view/journals/phoc/47/9/jpo-d-17-0005.1.xml?utm_source=chatgpt.com "Whitecap Coverage Dependence on Wind and Wave ..."))
* Remote-sensing literature and satellite algorithms (e.g., Anguelova 2019) further document whitecap fraction behavior and detection, supporting **mitigation claims** (temporal persistence, size/aspect gating, sensor fusion). ([AGU Publications](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2018JC014630?utm_source=chatgpt.com "Whitecap Fraction From Satellite Measurements: Algorithm ..."))

### 4) Standards language for reporting detection to reviewers

* **IAMSAR / USCG search theory** defines **sweep width (W), track spacing (S), coverage C=W/S, POD, POC, POS**, and provides the accepted framework to describe detector performance and its effect on search success. Include these terms verbatim in reporting; cite USCG’s _Theory of Search_ and IAMSAR amendments that define sweep width/coverage. ([Navigation Center](https://navcen.uscg.gov/sites/default/files/pdf/Theory_of_Search.pdf?utm_source=chatgpt.com "The Theory of Search - A Simplified Explanation - navcen"))([Maritime Safety Innovation Lab LLC][4])

**Literature implication:** with modern CNNs on **thermal at night** and **RGB by day**, real-world, water-scene datasets and peer-reviewed results exist that deliver high recall at practical frame rates; whitecap-driven FPR is a known, measurable phenomenon with documented mitigations.

---

## B1. Public-data evaluation (desk research you can run now)

* **Curate** SeaDronesSee (OD/track) day scenes (0–600 m estimated ranges) → train/fine-tune baseline detectors; compute **ROC**, **Pdet** at operating points, and **FPR/min** on **negative clips** (water only). ([CVF Open Access][2])
* **Reproduce** the 2024 **thermal night** results on the paper’s dataset or a matched LWIR set; extract **Pdet at night** for multiple thresholds and report **AUC**; confirm real-time throughput on your intended compute class. ([PMC][5])
* **Whitecap stress test:** pull open imagery/footage with documented **whitecap coverage**; run detectors and measure FPR/min vs wind-indexed clips; cite whitecap-coverage literature to interpret results. ([American Meteorological Society Journals][3])

## B2. Harbor mannequin drills (small-craft charter; one operator)

* Use a certified MOB manikin (e.g., **Ruth Lee “Oscar”**; floats **head-and-shoulders at ~45°**), deploy at 50–200 m from a pier or RIB; record **RGB by day**, **thermal by night** with a gimbal camera (handheld or mast-mounted). Annotate frames and compute **Pdet/FPR** vs range and clothing/contrast. ([Rescue Equipment - RescueTECH1.com][6])

_These two steps yield **publishable ROC curves**, **Pdet by range band**, and **FPR/min** under real backgrounds—without needing a cruise ship or even a flight-qualified prototype._

---

## C. Measurement definitions

* **Pdet (range-banded):** ( \text{Pdet}(r_i) = \frac{\text{TP}}{\text{TP}+\text{FN}} ) within range band (r_i \in {0!-!100,100!-!300,300!-!600,\text{m}}). (Range estimated by GPS marks for manikin or by known pier offsets.)
* **FPR/min:** false alerts per minute **with no target present** (negative clips, same sea state/lighting) or during non-target intervals in positive clips.
* **ROC / AUC:** threshold sweep on detector confidence; report **operating points** (e.g., “VERIFY,” “ALERT”) with their Pdet and FPR/min.
* **Sea-state context:** log **WMO sea state** and **Beaufort** from local marine forecasts/met observations for each session. ([Roboflow][7])

---

## D. Target thresholds

* **Night (thermal):** select an operating point matching the 2024 thermal paper’s **high-recall ROC zone** (≥**0.80** recall) and confirm ≥**20 FPS** on target hardware. ([PMC][5])
* **Day (RGB):** fine-tune on SeaDronesSee; pick a threshold achieving **Pdet ≥ 0.8 (≤300 m)** with **FPR ≤ 0.2/min** on **whitecap-present** negatives; justify FPR with whitecap literature (expect FPR to correlate with wind). ([CVF Open Access][2])

---

## E. False-positive taxonomy and mitigations

* **Whitecaps/foam** (bright textured patches; most frequent maritime FPs). **Mitigation:** temporal consistency (require persistence ≥N frames), size/aspect priors for head-shoulders, fusion (thermal+RGB) at nightfall. ([MDPI][8])
* **Glare/sparkle** (sun angles, speculars). **Mitigation:** polarizer for RGB, HDR exposure, temporal veto. (Assess on SeaDronesSee sun-glint clips.) ([CVF Open Access][2])
* **Birds/kelp/debris.** **Mitigation:** motion/trajectory filtering (ballistic paths for birds), texture cues for kelp mats. (Quantify via negative-only sequences; report FPR/min by class.)
* **Rain/fog attenuation (thermal).** Expect reduced effective range; note in spec that **Pdet distances derate** with precipitation/humidity per IR propagation guidance. (Use AUC at reduced ranges.) ([Maritime Safety Innovation Lab LLC][4])

---

## F. Evidence Tables

### ROC/AP curves

| Operating context   | Dataset / standard             | Evidence type                             | What to claim                                                                                                                                                                                                                                                                                                                                       |
| ------------------- | ------------------------------ | ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Night, dark aquatic | Cheng et al. 2024 (YOLOv5s-IR) | Peer-reviewed ROC/throughput              | **Pdet ≥ 0.8** at chosen threshold; **~23 FPS** inference feasible. ([PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC11175020/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."))                                                                                                                                 |
| Day, open water     | SeaDronesSee (WACV 2022)       | Open benchmark (AP/PR)                    | **High recall** within ≤300 m using published baselines/fine-tunes; public leaderboard for audit. ([CVF Open Access](https://openaccess.thecvf.com/content/WACV2022/html/Varga_SeaDronesSee_A_Maritime_Benchmark_for_Detecting_Humans_in_Open_Water_WACV_2022_paper.html?utm_source=chatgpt.com "SeaDronesSee - WACV 2022 Open Access Repository")) |
| FPR behavior        | Brumer 2017; Schwendeman 2015  | Ocean physics (whitecap fraction vs wind) | **FPR rises with Beaufort**; specify mitigation (temporal/shape/fusion). ([American Meteorological Society Journals](https://journals.ametsoc.org/view/journals/phoc/47/9/jpo-d-17-0005.1.xml?utm_source=chatgpt.com "Whitecap Coverage Dependence on Wind and Wave ..."))                                                                          |
| Reporting           | IAMSAR / USCG                  | SAR doctrine                              | Use **W, S, C, POD/POS** in all performance statements. ([IMO](https://wwwcdn.imo.org/localresources/en/OurWork/Safety/Documents/Documents%20relevant%20to%20SAR/MSC.1-CIRC.1594%20Amendments%20to%20IAMSAR%20Manual.pdf?utm_source=chatgpt.com "MSC.1-CIRC.1594 Amendments to IAMSAR Manual. ..."))                                                |

| Condition     | Sensor     | Range band | Pdet (CI) | FPR/min (CI) | Notes                                                                                            |
| ------------- | ---------- | ---------- | --------: | -----------: | ------------------------------------------------------------------------------------------------ |
| Night, SS 2–3 | LWIR (640) | 0–300 m    |     ≥0.85 |         ≤0.1 | Matches 2024 thermal ROC zone; 20–30 FPS. ([PMC][5])                                             |
| Day, SS 2–3   | RGB        | 0–300 m    |     ≥0.80 |         ≤0.2 | Trained/eval on SeaDronesSee; glare-controlled. ([CVF Open Access][2])                           |
| Day, SS 4–5   | RGB        | 0–300 m    |     ≥0.75 |         ≤0.3 | Whitecaps increase FPR; temporal gating applied. ([American Meteorological Society Journals][3]) |
| Night, SS 4–5 | LWIR       | 0–200 m    |     ≥0.80 |         ≤0.2 | Shorter range due to chop/humidity; verify on thermal set. ([PMC][5])                            |

(Confidence intervals from bootstrap over clip segments; exact numbers filled once desk-evaluation + harbor data are run.)

---

## G. Citations

* **SeaDronesSee** (WACV 2022; dataset + benchmark results; open access). ([CVF Open Access][2])
* **SeaDronesSee site/dataset card** (object detection & tracking tracks; multi-spectral subset). ([SeaDronesSee][9])
* **Night thermal detection of waterborne persons** (Sensors 2024; ROC/throughput). ([PMC][5])
* **Whitecap coverage vs wind/sea state** (J. Phys. Oceanogr. 2017) and **whitecap detection under varied illumination** (Remote Sensing 2022). ([American Meteorological Society Journals][3])
* **IAMSAR & USCG detection constructs** (sweep width, POD/POS) for reporting language. ([Maritime Safety Innovation Lab LLC][4])
* **Ruth Lee “Oscar” MOB manikin** (head-and-shoulders float posture) for harbor drills. ([Rescue Equipment - RescueTECH1.com][6])

---

### Conclusion

Peer-reviewed **night thermal** results and the **SeaDronesSee** open-water human dataset support **high Pdet** at practical frame rates; **whitecap-driven FPR** is real but measurable and controllable with temporal/shape filters and fusion. A **desk-evaluation + small-boat harbor** program produces the ROC curves, **Pdet ≥ 0.8** within the first-sortie envelope, and **FPR ≤ 0.2/min** operating points ([PMC][5])

[1]: https://pubmed.ncbi.nlm.nih.gov/38894113/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."
[2]: https://openaccess.thecvf.com/content/WACV2022/papers/Varga_SeaDronesSee_A_Maritime_Benchmark_for_Detecting_Humans_in_Open_Water_WACV_2022_paper.pdf?utm_source=chatgpt.com "A Maritime Benchmark for Detecting Humans in Open Water"
[3]: https://journals.ametsoc.org/view/journals/phoc/47/9/jpo-d-17-0005.1.xml?utm_source=chatgpt.com "Whitecap Coverage Dependence on Wind and Wave ..."
[4]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2021/02/Doc.9731-EN-IAMSAR-Manual-International-Aeronautical-and-Maritime-Search-and-Rescue-Manual-Volume-III-Mobile-Facilities.pdf?utm_source=chatgpt.com "IAMSAR MANUAL"
[5]: https://pmc.ncbi.nlm.nih.gov/articles/PMC11175020/?utm_source=chatgpt.com "Personnel Detection in Dark Aquatic Environments Based ..."
[6]: https://www.rescuetech1.com/ruth-lee-man-overboard-GEN2.aspx?utm_source=chatgpt.com "Ruth Lee \"Oscar\" Man Overboard Water Rescue Manikin"
[7]: https://universe.roboflow.com/ntnu-2wibj/seadronessee-odv2?utm_source=chatgpt.com "SeaDronesSee ODV2 Object Detection Model by ntnu"
[8]: https://www.mdpi.com/2072-4292/14/22/5691?utm_source=chatgpt.com "Using Optical Flow Trajectories to Detect Whitecaps in ..."
[9]: https://seadronessee.cs.uni-tuebingen.de/?utm_source=chatgpt.com "SeaDronesSee | Drone Detection Tracking Dataset"
