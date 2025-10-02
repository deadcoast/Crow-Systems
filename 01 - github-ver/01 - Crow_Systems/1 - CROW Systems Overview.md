# Cruise Overboard Watch(CROW) Drone System

## 1) Purpose & Mission Profile

**Mission:** Launch in seconds on MOB, perform a brief **IRD** autonomously, **pilot-controlled** search to **find**, **mark**, **monitor**, and **deliver buoyancy** while providing live geo-tagged video to bridge/rescue, acting as a visual/IR beacon to vector rescue craft.

**Primary outcomes (first minutes):**
(1) Auto-launch + IRD; (2) Manual pilot control; (3) Geo-tagged target tracking; (4) Beaconing (visible + IR); (5) Buoy/dye deployment on pilot command.

**Primary outcomes (within first minutes):**

1. Aerial detection in night/day;
2. Continuous geo-tagged tracking;
3. On-site beaconing (visible + IR + optional audio);
4. Drop a lightweight auto-inflating flotation/marker;
5. Stream video/telemetry to the bridge and rescue boat helm.

## 2) System Overview (shipboard set)

- **`CROW` Drone** (marine-ruggedized quad)
- **MOB Dock** (auto-hangar/charger; instant launch)
- **Bridge Interface Unit (BIU)** (MOB input, comms, records, pilot takeover handoff)
- **Rescue Payloads** (inflatable ring, dye/smoke, strobes)
- **Pilot Kit (on-person satchel)** (see §12)

## 3) Key Performance Targets (MVP)

- **Auto-launch latency:** ≤ 20 s from MOB alarm
- **IRD duration (hard-limit):** 60–120 s (configurable, default 90 s)
- **IRD radius cap:** ≤ 200 m from LKP (configurable envelope)
- **Manual control availability:** pilot can take over **at any time** during IRD via priority command
- **Time-to-first-sweep:** ≤ 60 s to begin grid at last-known position (LKP)
- **Effective detection radius (night IR, sea state ≤ 4):** ≥ 400 m from LKP within first sortie
- **Endurance:** ≥ 18 min hover / ≥ 14 min mixed (transit + loiter) on standard pack
- **Wind envelope (operational):** up to Beaufort 6 (≈ 22–27 kn) with degraded performance; survivable gusts to 35 kn on launch/return
- **Ingress protection:** Drone IP55 (operational rain/spray), Dock IP66/67
- **Payload capacity:** ≥ 1.0 kg (MVP); growth path 1.8 kg
- **Thermal detection:** 640×512 LWIR, 30–60 Hz; NETD ≤ 50 mK
- **Visible camera:** 4K/30 main + 1080p/60 low-latency stream
- **Strobe:** visible + IR, ≥ 200 cd, 1–4 Hz, IR 850 nm band
- **Geo accuracy:** GNSS L1 standard; optional RTK base in dock (<0.5 m)
- **Comms:** 2.4/5 GHz to ship mesh, AES-256; backup sub-GHz C2 link

## 4) Human-in-the-Loop Operations Doctrine

**Trigger → Auto-Launch → Human Pilot Takes Over.**

- **Auto-Launch Only (no autonomy beyond initial diagnostic sweep):**
  Upon **MOB alarm**, the system **automatically undocks and launches** to a safe altitude, transits to the **Last Known Position (LKP)**, and begins a **short, bounded Initial Rescue Diagnostic (IRD)**: a pre-approved **micro-grid** (e.g., expanding square / cloverleaf) limited by both **time (e.g., 60–120 s)** and **radius (e.g., ≤ 200 m)** to establish immediate situational awareness and reduce “lost time.”
- **Mandatory Human Takeover:**
  After the IRD, **the drone must not continue autonomous search**. Control is **handed to the on-duty, trained drone pilot** who resumes the operation in **Manual/Assisted** modes (stabilization + collision/geo fences remain active).
- **On-Duty Pilot Protocol:**
  A **dedicated drone pilot** remains on shift with a **minimal satchel** (remote + video goggles/HUD + spare pack). On MOB alarm, pilot **stops current task**, moves to the nearest designated control point, **unpacks within ~30–45 s**, and **assumes command**.
- **Design Outcome:**
  This balances *seconds-matter* auto-launch speed with **human judgment** for search, marking, and buoy drop. It also aligns with conservative maritime safety culture (human-in-the-loop).

---

**V2.0** -> Autonomous Flight

- **Frame:** 4-arm quadcopter, 350–400 mm class, corrosion-resistant (anodized Al + marine-grade polymer; stainless fasteners A4)
- **Coatings:** Conformal PCB coating; sealed motor bearings; hydrophobic vents
- **Motors/ESCs:** 4 × 2806–3110 class outrunners; salt-tolerant; ESCs with conformal coat and conformal drain paths
- **Props:** 10–11″ low-noise, glass-nylon; spare “storm” props with higher pitch
- **Landing:** skid feet with anti-slip; precision landing markers for dock (AprilTag/LED fiducials)
- **Mass (target):** 1.8–2.3 kg empty; 3.0–3.5 kg MTOW w/ payload

---

## 5) Power System

- **Battery:** 6S Li-ion (21700 cells) 10–12 Ah pack; cold-tolerant; smart BMS
- **Hot-swap:** Dock maintains 2–3 charged packs; robotic pusher/latch or manual slide-in for MVP; target 20-second swap cycle
- **Heaters:** pack pre-warm to ≥ 10 °C via dock; flight pack thermal wrap
- **Charger:** 400–600 W CC/CV in dock; pack-ID & cycle logging

## 6) Sensors & Payload (MVP)

**Gimbal:** 2-axis stabilized, IP54 seal

- **Thermal LWIR core:** 640×512, 30–60 Hz, 13–19 mm lens options (adjustable FOV for altitude); on-core AGC and radiometric stream
- **RGB camera:** 4K/30 record + 1080p/60 live; low-light sensor, wide FOV (≈ 84° HFOV)
- **Rangefinder (optional):** 905 nm ToF/Lidar for low-altitude altitude hold over waves
- **mmWave module (future option):** 60–77 GHz compact radar pod to improve detection in whitecaps/heavy spray—kept as a growth port on payload bus

**Rescue/Marking Payloads (under-gimbal mount rail):**

- **Inflatable ring module:** 300–600 g, CO₂ cartridge, remote drop + auto-inflate on contact (COTS module or bespoke)
- **Dye pack (day):** non-toxic, high-contrast surface dye, 5–10 min persistence
- **Smoke (day, low-wind only):** SOLAS-grade orange for visual cue; lockout above Beaufort 4
- **Beacon:** high-intensity visible strobe + 850 nm IR strobe; auto-pattern on “Target Locked” state
- **Audio (optional):** 85–95 dB buzzer/voice prompt for conscious casualty orientation

## 7) Avionics & Compute

- **Flight controller:** Redundant IMU; open architecture (PX4-class) or enterprise controller with marine tuning; dual GPS if possible
- **Edge compute:** ARM SoC (8-core) + NPU (≥ 4 TOPS) for onboard detection/tracking; NVMe 256–512 GB for video & event logs
- **Interfaces:** CSI for cameras, SPI/I²C for sensors, UART for payload release, Ethernet-over-USB to Dock diag when seated
- **Failsafe:** RTH to dock, hover-and-descend if GNSS lost, geofence off ship superstructure

## 8) Comms & Navigation

- **Pilot Priority Link:** the hand controller establishes a **privileged control session** on connection; receiving this signal **preempts autonomy** and switches to Manual/Assisted mode.
- **Hot Handoff:** BIU UI displays “Pilot in Command” state; bridge can still view video/telemetry but cannot drive the aircraft while pilot is active (to avoid command contention).
- **Primary link:** 5 GHz low-latency video (≤ 120 ms), adaptive bitrate, AES-256
- **Control link:** frequency-hopping 900 MHz/Sub-GHz backup with range ≥ 2 km LOS
- **Networking:** Bridge Interface Unit (BIU) acts as ground station server; streams to ECDIS/helm tablet via RTSP/WebRTC
- **GNSS:** GPS/GLONASS/Galileo; optional RTK via dock base for precise geotag; magnetometer offset calibration for ship superstructure

## 9) Software Modes

1. **Auto-Launch (MOB Triggered):** Dock opens; drone arms; climbs to safe height and proceeds to LKP.
2. **IRD (Initial Rescue Diagnostic):** **Strictly bounded** autonomous micro-grid (time+radius caps). **No buoy drop** in IRD (observe-only) unless **pilot authorizes**.
3. **Pilot Takeover (Manual/Assisted):** On pilot connect or command, autonomy **ceases**; pilot flies search patterns, commands buoy/dye, sets hover altitude; stabilization and geofences remain.
4. **Lock & Mark:** Pilot can enable “assisted hover” above target (beacons on; GPS pinging).
5. **Precision Dock Return:** Pilot or BIU commands return; precision land/dock.
6. **Failsafe:** Loss of pilot link → hover + slow climb to safe altitude → BIU alert; after timeout, return-to-dock unless bridge/pilot intervenes.

**Safety Interlocks:**

- IRD cannot exceed configured time/radius.
- Buoy release requires **positive pilot command** (two-stage confirm).
- Smoke locked out above Beaufort 4; dye pack pilot-approval.

### **V2.0** -> Autonomous Flight

- **Auto-Launch on MOB:** Dock lid pops, props arm, ascent to safe height (e.g., 25–35 m AGL), immediate transit to LKP
- **Grid Search:** expanding square or sector sweep; adaptive to wind/current; probability-weighted (future: Monte Carlo PDF from BIU)
- **Detect & Verify:** IR detector pings → RGB confirm; confidence gating; human-in-loop override on bridge
- **Lock & Mark:** hold over target 10–20 m; strobe on; drop buoy/dye if commanded or auto-threshold met; emit GPS pings @ 1–2 s
- **Hand-off:** maintain hover beacon until rescue craft on-scene; follow-assist if drift exceeds X meters
- **Precision Dock Return:** approach corridor, precision land using visual markers + Lidar; auto-wipe & charge

## 10) Dock (MOB Dock) — Mechanical & Electrical

- **Enclosure:** IP66/67, marine-coated aluminum; salt-fog tested (ASTM B117)
- **Lid:** motorized lift; water-shedding lip + gasket; de-icing heater pads
- **Deck interface:** shock-isolated base, stainless hardware; drain channels
- **Guidance:** LED fiducials for precision landing; internal bumpers; alignment funnel
- **Power:** 110/220 VAC → DC; UPS buffer (5–10 min) for blackout; PoE to BIU optional
- **Thermal mgmt:** desiccant canister + Gore vents; internal recirculation fan; dehumidifier cartridge service door
- **Battery bay:** 2–3 slot smart charger; pack ID, cycle count; safety interlocks
- **Self-care:** wiper/nozzle to clear salt film on gimbal window; rinse cycle (manual maintenance mode)

## 11) Bridge Interface Unit (BIU)

- **Workflow:** MOB alarm → **Auto-Launch (T-0)** → IRD countdown visible (e.g., “IRD: 0:90…0:00”) → “Awaiting Pilot” banner until takeover.
- **Controls:** Bridge can **abort IRD**, command **Return**, or **Pause & Hold** (hover). **Buoy drop is pilot-only** by policy.
- **Recording:** Tag timeline with MOB, IRD start/stop, Pilot-in-Command, drops, and coordinates.
- **Form:** 1U fanless box, PoE; dual NIC (ship LAN + dock LAN)
- **I/O:** dry-contact input from ship MOB alarm; NMEA 0183/2000 out to ECDIS/plotter; HDMI for local display
- **Software:** mission control UI (Web), recording (video/GPS), Alert API hooks, user roles; health telemetry of Dock/Drone
- **Cyber:** signed firmware; audit logs; TLS cert pinning

## 12) Safety & Training

**Pilot:**

- **Satchel** (camera-bag sized, ≤ 2.5 kg):**
- **Rugged hand controller** with C2 + low-latency video receiver
- **Video goggles / HUD visor** (sun-capable; hot-swap to a **bridge repeater tablet** if needed)
- **One spare flight battery** (flight-ready; dock continues charging rotation)
- **Compact weather meter** (wind gust read and sea spray check)
- **High-vis armband** (“DRONE PILOT”) for quick crew clearance
- **Quick SOP card** (checklist: connect → assume control → confirm IRD cancel → commence search)
- **Emergency tether** (optional short lanyard to controller in heavy sea states on open decks)

**Control Point Layout:** Mark **two or more** pilot control points (port/starboard, leeward bias) with clear RF coverage to the dock/LKP sector.

- **Doctrine:** Auto-launch buys **seconds**; **humans rescue**. The system **assists**, it does **not** replace pilot judgment.
- **Training:**
  - **Monthly drill:** Auto-launch + IRD + pilot takeover within 60 s; no passenger areas overflight.
  - **Quarterly drill:** Full night ops; buoy drop on dummy; beacon hover + handoff to rescue boat.
- **Checklists:** IRD limits, smoke/dye use gates, buoy drop confirmation, lost-link actions.
- **Passenger comms:** PA option (“drone in operation, remain clear of designated deck area”).
- **One-button flow:** MOB alarm → BIU pops dialog: “LAUNCH?” (auto after 5 s unless canceled)
- **Interlocks:** no-launch if wind/diagnostics out of envelope; override with captain key
- **Deck crew safety:** defined launch corridor away from passengers; PA announcement option
- **Training:** 30-min CBT; monthly drill (auto-launch + hover); quarterly full payload drill

## 13) Environmental & Compliance (design intent)

- **EMC/EMI:** IEC 60945 guidance; CISPR 22/24 shipboard emissions/immunity
- **Ingress/Corrosion:** IP ratings above; ASTM B117 salt-fog; ISO 9227
- **Batteries/Transport:** UN 38.3; IEC 62133; maritime MSDS on packs and CO₂ canisters
- **Maritime class engagement:** DNV/ABS/LR “auxiliary lifesaving equipment” path; document FMEAs, test plans, and maintenance schedules

## 14) Test Regimen (MVP → Pilot)

- **Human-in-the-loop drills:** measure **time-to-pilot-control** (target ≤ 60 s from MOB alarm), **command preempt latency** (< 300 ms), IRD adherence (no overrun).
- **Trials:** same SAR metrics as before, plus pilot workload assessment and visibility with goggles vs. bridge repeater.
- **Bench/Env:** salt-fog 96 h, rain spray, vibe test to simulate ship vibration; wind tunnel to 30 kn equivalent
- **Dock cycle:** 500 auto land/launch cycles; battery swap wear; lid duty cycles
- **Sea trials (harbor):** launch in 15–25 kn wind; precision return on moving vessel @ 5–10 kn headway
- **SAR trials:** dummy in water (day/night, sea state 2–4); metrics: time-to-detect, false positives/hour, beacon hold accuracy, buoy drop CEP
- **Reliability target:** MTBF ≥ 200 flight hours in marine environment across 6 months

## 15) Rough BOM Targets (MVP, per ship set)

- **Drone airframe + sensors + compute:** $6–10k
- **Thermal core (640):** $2.5–5k (depends on supplier)
- **Dock (marine, heated, auto-open, charger):** $12–18k
- **BIU + software licenses (annual):** $3–7k
- **Payloads (initial kit):** $1–2k (rings, dye, smoke, strobes, spares)
- **Total per ship (MVP):** ~$25–40k hardware; support & training separate
  *(Intentionally aggressive; goal is “no-brainer” CAPEX vs. safety/PR upside.)*

## 16) Known Challenges & Mitigations

- **Command contention (bridge vs pilot):** Adopt **Pilot-in-Command** lock with explicit “Request Control” handshake on BIU.
- **Over-automation risk:** IRD hard caps + hardware **Auto-Launch Enable** switch; policy that **all critical actions** (buoy/smoke/dye) are **pilot-commanded**.
- **Pilot mobilization time:** Satchel-on-person policy; designated control points; drills to hit ≤ 60 s takeover.
- **Salt spray/corrosion** → Conformal coatings, sealed bearings, sacrificial anodes, maintenance rinse schedule, dock desiccation, wiper system.
- **Launch/landing turbulence off a moving ship** → Higher initial climb power, defined launch corridor, precision landing markers, approach corridor logic.
- **Wind & sea state** → Specify operating envelope, storm prop set, dynamic hover controller tuned for gust response, fall-forward to “mark by drop-buoy then climb to safer hover.”
- **False positives (whitecaps/foam/kelp)** → IR+RGB fusion, temporal filters, ML tuned on maritime datasets; human-in-loop verify on bridge.
- **Passenger interactions/curiosity** → Locking dock, crew-only area, PA procedure.
- **Regulatory novelty** → Early engagement with class societies; treat as auxiliary—not replacement—lifesaving; clear SOPs & drills; insurer briefings.

## 17) Growth Path / Future Options

- **Assisted “pilot tools”:**

  - **Probability-map overlay** (from drift model) on pilot HUD.
  - **Aim-assist hover** (maintains offset over target in gusts).
  - **Auto-camera framing** (keeps detection in frame; pilot flies, camera follows).

- **Dual-drone concept:** One auto-launch IRD unit; second queued and **pilot-launched** on demand for relief/beacon handoff.
- **mmWave micro-radar pod:** Boost detection in spray/foam; fuse into detector stack.
- **RTK base in dock:** Sub-meter geotag for better waypointing in heavy drift.
- **Auto-tether recharge:** Lightweight retractable power tether for long hover (pilot later; watch for entanglement risk).
- **AIS-SART tie-in:** Drop AIS-SART marker for universal receiver visibility on nearby craft.
- **Thermal zoom/lens switcher:** Dynamic FOV based on altitude for best detection swath vs. resolution.

## 18) Deliverables (to instruct integrator)

- **3D CAD pack:** drone frame, dock, mounts, harness drawings; IP ratings callouts
- **Electrical schematics:** power, payload bus, release circuit, strobe driver, BIU I/O
- **Firmware/software specs:** state machine for modes; APIs for BIU; logging & telemetry schema
- **SOPs:** launch, detect, drop, hand-off, recovery, abort; maintenance schedule; drills
- **Verification plan:** pass/fail criteria per test regimen; data collection templates

---
