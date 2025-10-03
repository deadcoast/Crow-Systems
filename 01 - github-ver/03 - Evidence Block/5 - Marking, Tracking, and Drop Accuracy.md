# Evidence Block — Marking, Tracking, and Drop Accuracy (with standards and quantified references) #

## 1) Electronic homing: AIS-SART / MOB beacons (standards, behavior) ##

- **IEC 61097-14:2010** defines **minimum performance requirements** and test methods for **AIS Search and Rescue Transmitters (AIS-SART)** within GMDSS. Scope includes operational/performance requirements and environmental tests for AIS-SART units used to fix survivor position on all AIS-equipped bridges nearby. ([Iteh Standards](https://cdn.standards.iteh.ai/samples/16694/7bf752a5752548be8abe3a3b90f71445/IEC-61097-14-2010.pdf "IEC 61097-14"))

- **IMO MSC.246(83)** adopts the AIS-SART performance standards: examples include **96 h battery endurance** and operational temperature **–20 °C to +55 °C**; equipment must transmit identity and position in each message and support end-to-end functional testing. ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.246%2883%29.pdf "RESOLUTION MSC.246(83) (adopted on 8 October 2007) ..."))

- **USCG NAVCEN** clarifies **MMSI identifiers** used by AIS SART categories: “970” (standard AIS-SART), “972” (AIS MOB/MSLD), “974” (AIS EPIRB), and notes that **all categories display on IMO-mandated shipboard navigation systems**. ([navcen.uscg.gov](https://www.navcen.uscg.gov/types-of-ais "Types Of Automatic Identification Systems (Per ITU-R M.1371 ..."))

**Implication for UAV-dropped tags:** dropping an **AIS-SART/MOB** device creates an **electronic track** immediately visible to the casualty’s own ship and any AIS-equipped asset in VHF range, with performance bounded by the above standards. ([Iteh Standards](https://cdn.standards.iteh.ai/samples/16694/7bf752a5752548be8abe3a3b90f71445/IEC-61097-14-2010.pdf "IEC 61097-14"))

---

## 2) Visual/IR marking: SOLAS/LSA lifebuoy lights and smoke (performance bars to match or exceed) ##

- **LSA Code / SOLAS III/7.1.3** (as reproduced in multiple official/industry summaries) requires lifebuoy self-igniting lights to **withstand water**, be **white**, and provide **≥ 2 cd** luminous intensity **for ≥ 2 h** (continuous) or flash **50–70 fpm** with equivalent effective intensity. ([imorules.com](https://www.imorules.com/GUID-CE112D86-3D78-44D0-A2D4-C40D56F8B397.html "2.1.2 Lifebuoy self-igniting lights"))

- **LSA smoke**: the test recommendations in **IMO MSC.81(70)** specify prototype tests for **lifebuoy self-activating smoke signals**; drop/temperature cycling and a functional burn **≥ 15 min** are required. National adoptions echo these requirements. ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.81%2870%29.pdf "RESOLUTION MSC.81(70) (adopted on 11 December ..."))

**Implication for UAV payloads:** a drone-delivered light/smoke package should **meet or exceed** the above **2 cd/2 h** and **≥ 15 min smoke** benchmarks to align with bridge expectations and camera/IR visibility. ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.81%2870%29.pdf "RESOLUTION MSC.81(70) (adopted on 11 December ..."))

---

## 3) Flotation delivery: documented drone rescues and products ##

- **Operational rescue (Australia, 2018):** the “**Little Ripper**” UAV **located two swimmers and dropped a self-inflating pod**; **time to delivery ≈ 1–2 min**, recorded on video and widely reported by general and UAV trade press. ([DRONELIFE](https://dronelife.com/2018/01/18/little-ripper-drone-saves-swimmers-australia/ "Watch: Little Ripper Drone Saves Swimmers Down Under"))

- **Commercial drop pod**: SOS Marine’s **Rescue Marine Pod (ULBs)** is marketed for **drone drop**, **auto-inflates**, and stands **~2.0 m long** when deployed—an example payload form factor and deployment behavior suited to rapid buoyancy/visibility. ([SOS Marine](https://www.sosmarine.com/product/rescue-pods-sos-5701/ "Little Ripper Rescue PODS SOS-5701"))

**Relevance:** independent proof that small UAVs can **deliver buoyancy** within minutes and create an immediate **visual marker** on scene. ([TIME](https://time.com/5109269/surf-drone-rescue-worlds-first-australia/ "Watch the World's First Ever Drone Surf Rescue"))

---

## 4) Drop accuracy and positioning (what current systems can credibly achieve) ##

- **RTK-equipped multirotors** (e.g., DJI Matrice 300 RTK) publish **hovering accuracy ±0.1 m (RTK)** and **RTK positioning ≈ 1 cm + 1 ppm (horizontal)** under fixed solutions—manufacturer spec corroborated across independent summaries. These figures bound **release-point** accuracy in low-wind, stationary drops. ([DJI Official](https://www.dji.com/support/product/matrice-300 "Support for Matrice 300 RTK"))

- **Peer-reviewed RTK performance**: multiple studies report **centimeter-level** UAV position accuracy when RTK is correctly configured (open sky, short baseline), noting degradation with distance and multipath; representative results show ~**1 cm** horizontal accuracy and consistent **cm-level** repeatability. ([MDPI](https://www.mdpi.com/1424-8220/23/13/5858 "Image Mapping Accuracy Evaluation Using UAV with ..."))

- **Precision airdrop with vision guidance**: a closed-loop autonomous delivery study (small fixed-wing) reports **mean landing error ≈ 5.5 m** using onboard machine vision to identify the target and compute a release point—useful as a **reference magnitude** for modest-mass payloads without RTK hover holds. ([SpringerLink](https://link.springer.com/article/10.1007/s10514-020-09902-3 "Autonomous ballistic airdrop of objects from a small fixed- ..."))

- **Navigation-method improvement**: a 2023 research preprint demonstrates **≈5× improvement in horizontal precision** over GPS-only by fusing **deep-learning vision alignment** with navigation during drop, indicating the typical **meter-scale CEP** attainable with commodity platforms can be tightened with visual targeting. ([arXiv](https://arxiv.org/html/2310.06329 "Precise Payload Delivery via Unmanned Aerial Vehicles"))

**Interpretation:** with **RTK hover + short-drop** the release-point error can be driven toward **decimeters** (airframe position), but **total drop CEP** at the water surface depends on **descent dynamics and wind drift** of the payload post-release. Vision-assisted, low-altitude drops cited in the literature center around **few-meters mean error** for moving platforms; these bound credible CEP targets before sea-state effects. ([DJI Official](https://www.dji.com/support/product/matrice-300 "Support for Matrice 300 RTK"))

---

## 5) Standards-compatible electronic tagging via UAV ##

- **AIS-SART/MOB via UAV drop** is **standards-conformant** when the tag itself is IEC-certified; **IMO MSC.246(83)** sets performance conditions (e.g., **96 h** operation at –20 °C…+55 °C). Ships’ ECDIS/AIS displays **auto-plot** these targets with distinct symbology per **NAVCEN** guidance. ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.246%2883%29.pdf "RESOLUTION MSC.246(83) (adopted on 8 October 2007) ..."))

- Example device class: commercial AIS-SARTs (e.g., McMurdo/SmartFind S5A) transmit **alert + GPS position** to all AIS-equipped receivers in VHF range upon activation—illustrative of **on-scene discoverability** by any assisting vessel. ([lhrmarine.com](https://www.lhrmarine.com/product/smartfind-s5a-ais-sart "SmartFind S5A AIS SART, McMurdo (Seas of Solutions)"))

---

## 6) Visual marker performance targets derived from SOLAS/LSA ##

- **Light:** ≥ **2 cd for ≥ 2 h** (white; water-resistant operation) or **50–70 fpm** flash with equivalent effective intensity. ([imorules.com](https://www.imorules.com/GUID-CE112D86-3D78-44D0-A2D4-C40D56F8B397.html "2.1.2 Lifebuoy self-igniting lights"))
- **Smoke:** **≥ 15 min** continuous, highly visible color; survive drop and temperature cycling as per **MSC.81(70)** prototype tests. ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.81%2870%29.pdf "RESOLUTION MSC.81(70) (adopted on 11 December ..."))

**Design translation:** specify a payload package whose **strobe** and **smoke/dye** meet or exceed the above; add **retro-reflective** patches per the latest **MSC.1/Circ.1628/Rev.3** reporting forms for personal lifesaving appliances. ([United States Coast Guard](https://www.dco.uscg.mil/Portals/9/MSC_1-Circ_1628-Rev_3.pdf "MSC.1/Circ.1628/Rev.3 22 January 2025 REVISED ..."))

---

## 7) What to claim in a trials binder (bounded by sources) ##

- **Electronic homing:** AIS-SART/MOB drop → **immediate AIS plot** on bridges within VHF range; performance per **IEC 61097-14** and **MSC.246(83)**. ([Iteh Standards](https://cdn.standards.iteh.ai/samples/16694/7bf752a5752548be8abe3a3b90f71445/IEC-61097-14-2010.pdf "IEC 61097-14"))
- **Visual/IR marking:** payload meets **LSA Code** lifebuoy-light (**2 cd/2 h**) and **smoke ≥ 15 min** performance; markers are **camera/IR-visible** and validated by night drills. ([imorules.com](https://www.imorules.com/GUID-CE112D86-3D78-44D0-A2D4-C40D56F8B397.html "2.1.2 Lifebuoy self-igniting lights"))
- **Drop accuracy:** **RTK hover-drop** bounded by **cm-level positioning** (platform) with overall **CEP in the meter class** demonstrated by peer-reviewed vision-guided drops; final CEP documented per sea state and release height during trials. ([MDPI](https://www.mdpi.com/1424-8220/23/13/5858 "Image Mapping Accuracy Evaluation Using UAV with ..."))
- **Operational precedent:** **drone flotation drop** achieved in public rescue (Little Ripper) with **≈1–2 min** time-to-delivery in surf; include as qualitative operational precedent alongside standards references. ([TIME](https://time.com/5109269/surf-drone-rescue-worlds-first-australia/ "Watch the World's First Ever Drone Surf Rescue"))

---

## Sources (representative, high-signal) ##

- **IEC 61097-14:2010** AIS-SART requirements & tests. ([Iteh Standards](https://cdn.standards.iteh.ai/samples/16694/7bf752a5752548be8abe3a3b90f71445/IEC-61097-14-2010.pdf "IEC 61097-14"))
- **IMO MSC.246(83)** AIS-SART performance standards (96 h battery; –20 °C…+55 °C). ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.246%2883%29.pdf "RESOLUTION MSC.246(83) (adopted on 8 October 2007) ..."))
- **USCG NAVCEN** AIS SART/MOB MMSI categories & display behavior. ([navcen.uscg.gov](https://www.navcen.uscg.gov/types-of-ais "Types Of Automatic Identification Systems (Per ITU-R M.1371 ..."))
- **IMO MSC.81(70)** Revised Recommendation on Testing of Life-Saving Appliances (lifebuoy lights, smoke). ([wwwcdn.imo.org](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.81%2870%29.pdf "RESOLUTION MSC.81(70) (adopted on 11 December ..."))
- **LSA Code excerpts** (self-igniting light ≥ 2 cd for ≥ 2 h; water-proof; flash rate). ([imorules.com](https://www.imorules.com/GUID-CE112D86-3D78-44D0-A2D4-C40D56F8B397.html "2.1.2 Lifebuoy self-igniting lights"))
- **Little Ripper rescue** (time to flotation drop ≈ 1–2 min). ([TIME](https://time.com/5109269/surf-drone-rescue-worlds-first-australia/ "Watch the World's First Ever Drone Surf Rescue"))
- **RTK positioning** (DJI M300 RTK specs; independent RTK accuracy studies). ([DJI Official](https://www.dji.com/support/product/matrice-300 "Support for Matrice 300 RTK"))
- **Precision aerial drop** (mean error ≈ 5.5 m with vision-guided release). ([SpringerLink](https://link.springer.com/article/10.1007/s10514-020-09902-3 "Autonomous ballistic airdrop of objects from a small fixed- ..."))
- **Vision-assisted delivery precision improvement** (~5× vs GPS-only). ([arXiv](https://arxiv.org/html/2310.06329 "Precise Payload Delivery via Unmanned Aerial Vehicles"))

---
