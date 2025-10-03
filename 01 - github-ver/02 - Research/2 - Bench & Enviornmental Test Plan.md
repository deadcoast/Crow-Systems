# Step 2 — Bench & Environmental Test Plan (with procedures, instruments, thresholds, and sources) #

Goal: prove `CROW`’s **marine durability, launch reliability, and data integrity** before harbor/open-sea trials. Every test has: purpose → method → instrumentation → pass/fail thresholds → records → sources.

---

## 2.1 Salt-fog (corrosion) — dock + drone assemblies ##

**Purpose:** verify corrosion resistance of exposed metals/fasteners, coatings, connectors, and dock mechanisms in marine air.
**Method:** neutral salt spray per **ASTM B117** / ISO 9227 reference. Continuous exposure at 35 °C; 5 % NaCl; fallout 1–3 mL/80 cm²/hr. 96 h for screening; 240 h for qualification on coated assemblies; visual check at 24 h increments. ([ASTM International | ASTM][1])
**Instrumentation:** calibrated salt-fog chamber; pH meter (6.5–7.2); fallout collection funnels; temp probes.
**Pass/Fail:** no red rust on stainless fasteners; no blistering/cracking of coated parts; connectors mate/demate normally; dock lid/hinge actuation torque ±15 % of baseline; no binding.
**Records:** pre/post photos; torque logs; mass/continuity checks of sacrificial anodes; corrective actions.

---

## 2.2 Ingress protection (spray/immersion) — drone, gimbal shroud, dock ##

**Purpose:** verify rain/spray ingress resistance and (for dock) immersion resilience of seals/drains.
**Method:** **IEC 60529 IPX6** (powerful jets) on drone airframe & gimbal shroud; **IPX7** immersion on dock floor pan/sump module; verify seals and drains. IPX6: 12.5 mm nozzle, ~100 kPa, 100 L/min, ≥3 min. IPX7: 1 m / 30 min. ([iec.ch][2])
**Instrumentation:** IP jet rig with flow/pressure gauges; immersion tank; leak-detection paper; insulation tester (megger).
**Pass/Fail:** no water ingress to electronics; no moisture flags on conformal-coated PCBs; post-test functional flight check OK; dock lid seals intact; drains clear.
**Records:** video, leak map, insulation resistance readings, pass ticket.

---

## 2.3 Environmental (marine) — IEC/EN 60945 alignment ##

**Purpose:** align with marine bridge/upper-deck electronics environmental expectations.
**Method:** sample subset of **IEC/EN 60945** tests: temperature/humidity cycling, salt mist reference, shock/vibration, EMC pre-screen. (Formal type-approval not required for MVP, but test to comparable severities). ([Applus+ Keystone][3])
**Instrumentation:** climatic chamber (-15→+55 °C, 95 %RH), shaker (random vibe), shock table; EMC pre-scan.
**Pass/Fail:** continuous operation through temp/humidity cycles; no structural cracks; no loss of control link/video; emissions/immunity prelim within marine expectations.
**Records:** chamber profiles; vibe spectra; fault logs.

---

## 2.4 Rain/blowing rain (operational) — drone in powered state ##

**Purpose:** ensure sustained prop-wash + rain does not ingress or destabilize avionics.
**Method:** **MIL-STD-810H, Method 506.6** (blowing rain) tailored to drone footprint; operate motors at hover thrust under spray. ([Wikipedia][4])
**Instrumentation:** rain booth with wind; high-speed video of droplets around vents; current draw logging.
**Pass/Fail:** no resets; IMU/GNSS stable; no water pooling inside.
**Records:** logs + annotated video.

---

## 2.5 Vibration & shock — dock on deck; drone in dock ##

**Purpose:** survivability under ship vibration and slamming shocks.
**Method:** random vibration + functional shock referencing **MIL-STD-810H 514/516** tailoring and **60945** expectations for shipboard equipment. ([Wikipedia][4])
**Instrumentation:** shaker; accelerometers on dock lid, hinge, PCB; strain gauges on mount points.
**Pass/Fail:** no latch loosening; precision landing alignment remains within ±5 mm; no cracked solder joints; FOC ESCs pass BIST.
**Records:** PSD profiles; modal notes; pre/post functional tests.

---

## 2.6 Auto-launch life-cycle — dock + aircraft ##

**Purpose:** prove the “seconds-matter” reliability of **auto-launch** and precision return.
**Method:** **500 continuous cycles**: dock opens → aircraft auto-arms → liftoff to 2 m AGL → settle back → precision dock land; every 20th cycle include 10 m ascent and short translation to exercise guidance.
**Instrumentation:** cycle counter; high-speed overhead camera; event timestamps.
**Pass/Fail:** **≥ 99.0 %** successful cycles (no human touch); mean cycle time stability ±10 %; landing offset ≤ ±15 mm (p95).
**Records:** cycle log; exceptions with root-cause, fix, re-test.

---

## 2.7 Video/C2 latency and link margin ##

**Purpose:** guarantee pilot sees and acts within < 300 ms end-to-end.
**Method:** optical time-stamping rig (LED flash in scene + photodiode trigger logged at controller); measure **glass-to-glass latency** at 1080p/60; measure C2 packet RTT under interference.
**Instrumentation:** LED/photodiode jig; logic analyzer; spectrum analyzer for 2.4/5 GHz; shielded room for impairment tests.
**Pass/Fail:** video median latency **≤ 150 ms**; p95 **≤ 220 ms**; C2 RTT p95 **≤ 50 ms**; sustained control at -65 dBm RSSI.
**Records:** latency histograms; RF scans; impairment matrix.

---

## 2.8 Battery safety & transport (UN 38.3) ##

**Purpose:** ensure flight packs can be shipped & carried aboard safely.
**Method:** cell/pack qualification to **UN 38.3** (T1–T8: altitude, thermal, vibration, shock, external short, impact, overcharge). Keep **PHMSA Test Summaries** on file for each pack SKU. ([PHMSA][5])
**Instrumentation:** qualified lab (internal or external) with UN 38.3 capability; pack BMS logs.
**Pass/Fail:** pass all T-tests; no vent/thermal runaway; labels and TS documents generated.
**Records:** UN 38.3 TS PDFs; lot traceability.

---

## 2.9 Thermal camera calibration & minimum pixel footprint ##

**Purpose:** validate IR detector sensitivity vs. altitude; set pilot altitude guidance.
**Method:** mount calibrated **blackbody** targets (34–36 °C) on a water background; fly heights 10–120 m; compute **minimum pixel footprint** for head/shoulders; derive altitude→swath **w(h)** table used by HUD.
**Instrumentation:** lab blackbody; range pole; drone flight logs.
**Pass/Fail:** at guidance altitude bands, human-sized target ≥ 10–15 px across in LWIR; detector confidence ≥ target ROC threshold (see 2.11).
**Records:** plots of w(h), ROC by altitude.

---

## 2.10 Buoy/dye/strobe actuation bench tests ##

**Purpose:** guarantee clean release, inflation, and beacon function.
**Method:** 50 dry firings (buoy CO₂), 20 wet; 30 dye; 30 strobe extended runs (≥ 30 min).
**Instrumentation:** scale for payload forces; high-speed video; battery logger.
**Pass/Fail:** 100 % release; buoy full inflation < 5 s; dye visible > 10 min (daylight); strobe visibility per spec.
**Records:** actuation times; any mis-fires with root cause.

---

## 2.11 Detector pre-screen (lab/bench ROC) ##

**Purpose:** ensure the IR-first detector/fusion pipeline is above a minimum ROC before harbor trials.
**Method:** curated video corpus (thermal+RGB) of water surfaces (whitecaps/foam/kelp) + mannequins; run inference; generate ROC, choose thresholds (PING/ALERT/VERIFY) that hit target **AUC** and **FPR**.
**Instrumentation:** dataset player; labeling tool; inference rig with NPU.
**Pass/Fail:** AUC ≥ 0.90 on bench set; **FPR ≤ 0.2/min** at VERIFY threshold; latency budget met (detector→HUD < 250 ms).
**Records:** ROC curves; confusion matrices; chosen thresholds.

---

## 2.12 Man-overboard mannequin procurement/spec check ##

**Purpose:** realistic signature & float posture in harbor/sea trials.
**Method:** acquire **Ruth Lee “Oscar” MOB** (GEN2/MK2) or equivalent; verify **45° head-and-shoulders** float posture and mass spec (adult 88 lb). ([Rescue Equipment - RescueTECH1.com][6])
**Instrumentation:** stills & measurements in calm basin.
**Pass/Fail:** posture consistent; reflective tape/strobe mount points present.
**Records:** spec sheet; acceptance photos.

---

## 2.13 Documentation, EMC & cyber pre-checks ##

**Purpose:** ensure data integrity and bridge-safe behavior prior to shipboard power-up.
**Method:** hash-chained telemetry files; TLS certs; **EMC** pre-scan for emissions; map to **IEC/EN 60945** EMC expectations for bridge gear. ([Applus+ Keystone][3])
**Instrumentation:** spectrum analyzer; oscilloscope; code signing pipeline.
**Pass/Fail:** no spurious emissions near nav bands; signed logs; BIU hardening checklist complete.
**Records:** EMC pre-scan plots; cyber checklist.

---

### Test Records Package (bench stage deliverables) ###

- **Bench Test Report**: each test’s raw data, plots, and pass/fail.
- **Environmental Summary**: statement of conformance vs ASTM B117 / IEC 60529 IPX6/IPX7 / IEC/EN 60945 elements. ([ASTM International | ASTM][1])
- **UN 38.3 Pack File**: PHMSA-compliant Test Summaries for each battery SKU. ([PHMSA][7])
- **Detector ROC Memo**: thresholds adopted for harbor trials.
- **Mannequin Acceptance Note**: posture/mass verification with photos. ([Rescue Equipment - RescueTECH1.com][6])

---

## Notes on standards scope (to set reviewer expectations) ##

- **ASTM B117** is a **comparative** corrosion method (not a life-prediction test) but is the global norm for screening coating/metal systems; we combine it with 60945 salt-mist expectations. ([DECRA Metal Roofing][8])
- **IEC/EN 60945** is the **marine environmental/EMC anchor** for bridge equipment; we use it to frame severities (temp, humidity, shock/vibration, EMC) even though the drone/dock are auxiliary. ([Applus+ Keystone][3])
- **UN 38.3** documentation is mandatory for logistics and class/insurer comfort. ([PHMSA][5])

---

## Dependency hand-off to Step 3 (Harbor Trials) ##

Proceed only when all **critical gates** pass:

1. Auto-launch life-cycle ≥ 99.0 % across 500 cycles (2.6)
2. Video/C2 latency p95 within budget (2.7)
3. IPX6/IPX7 passed with post-test functional checks (2.2)
4. Detector AUC ≥ 0.90; FPR ≤ 0.2/min in bench set (2.11)
5. UN 38.3 Test Summaries on file (2.8)

---

**Primary sources used above:**
ASTM B117 & overviews (method, scope), IEC 60529 IP ratings (IPX6/IPX7), EN/IEC 60945 marine environmental/EMC expectations, UN 38.3 lithium battery transport requirements, USCG SAROPS Monte-Carlo background, MIL-STD-810H rain/vibration methods, Ruth Lee “Oscar” MOB manikin specs. ([ASTM International | ASTM][1])

If you’re good with this, I’ll move to **Step 3 — Harbor Trial Protocols** (test cards, run-of-show, data sheets, acceptance thresholds, and reporting templates) and keep the same level of detail and citations.

[1]: https://www.astm.org/b0117-19.html "Standard Practice for Operating Salt Spray (Fog) Apparatus"
[2]: https://www.iec.ch/ip-ratings "Ingress Protection (IP) ratings"
[3]: https://keystonecompliance.com/en-60945/ "EN 60945 Maritime Navigation Device Compliance Testing"
[4]: https://en.wikipedia.org/wiki/MIL-STD-810 "MIL-STD-810"
[5]: https://www.phmsa.dot.gov/training/hazmat/new-un-requirement-test-summaries "Lithium Battery Test Summaries (TS) | PHMSA"
[6]: https://www.rescuetech1.com/ruth-lee-man-overboard-GEN2.aspx "Ruth Lee \"Oscar\" Man Overboard Water Rescue Manikin"
[7]: https://www.phmsa.dot.gov/sites/phmsa.dot.gov/files/2024-09/Lithium-Battery-Test-Summary-2024.pdf "Lithium Battery Test Summaries (TS)"
[8]: https://www.decra.com/pro/astm-b117-the-salt-spray-test "ASTM B117 – The Salt Spray Test"
