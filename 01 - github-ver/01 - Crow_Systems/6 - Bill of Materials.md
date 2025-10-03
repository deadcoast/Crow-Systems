# Bill of Materials for CROW Systems #

## Overview ##

This document contains the bill of materials for the CROW Systems.

## Claims Bill of Materials ##

### BOM - Deployment Module (Claim 5) ###

| Component                 | Reference Product / Standard                                                           | Mass / Dimensions            | Key Specs                                                                 | Relevance                                                          |
| ------------------------- | -------------------------------------------------------------------------------------- | ---------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Inflatable Rescue Pod** | SOS Marine “Little Ripper” rescue pod (ANMM Catalog #00015373)                         | ~798 g packed; 215×290×65 mm | Water-activated CO₂ inflation; high-vis fabric; supports multiple persons | Demonstrates sub-1 kg compact flotation device proven in UAV drops |
| **CO₂ Cartridge**         | 33 g standard marine inflator cartridge (used in SOLAS PFDs)                           | ~120 g; 20×90 mm             | Single-use, water-triggered; ISO 12402 compliant                          | Drives pod inflation within 3–5 s of immersion                     |
| **Strobe Light**          | MED/SOLAS-approved lifebuoy light (e.g., Daniamant L6A)                                | ~150 g; 150×70×40 mm         | ≥2 cd output; ≥2 h operation; auto-ignition on water contact              | Ensures night conspicuity per SOLAS LSA                            |
| **Dye Marker Pack**       | Fluorescent dye marker, NASA Tech Brief & modern commercial packs                      | ~120 g sachet; 100×80×15 mm  | Creates ~50–100 m² slick; visible ≥1 NM; duration 30–40 min+              | Provides daytime aerial visibility                                 |
| **Release Mechanism**     | Mavic 3E drop kit (DJI, 70 g, ≤1 kg load) OR universal UAV drop hook (5–6 kg capacity) | 70–250 g depending on model  | Servo-actuated; secure single-point release                               | Integrates payload with UAV                                        |
| **Mount Cassette**        | Custom semi-rigid valise                                                               | ~150 g (est.)                | Sealed; tamper-evident; swap-in/swap-out                                  | Ensures fast re-arming between flights                             |

**Total estimated module mass:** ~1.3–1.6 kg (depending on release mechanism and strobe choice).  
**Volume envelope:** ~25×30×10 cm (fits under standard enterprise-UAV gimbal mount).  
**Drop envelope:** 10–30 m AGL; hover accuracy ±1–3 m (RTK-GNSS); CEP ≈ 5–10 m in Beaufort 5 winds.

---

### BOM - Payload (Claim 6) ###

(Note: BOM relevant here is software/data payload, not physical. To maintain consistency, here is a one-page listing of the “information payload” required for probability-weighted search.)

| Component              | Reference / Standard                     | Mass / Size | Key Specs                                        | Relevance                                    |
| ---------------------- | ---------------------------------------- | ----------- | ------------------------------------------------ | -------------------------------------------- |
| **Drift Model Input**  | NOAA SAROPS particle drift module        | N/A (data)  | Stochastic Monte Carlo leeway/current simulation | Provides probability grid                    |
| **Environmental Data** | NOAA/NWS wind & current feeds            | N/A         | 10–60 min update cycle                           | Drives probability updates                   |
| **Sweep Width Tables** | IAMSAR Vol. II Annex B                   | N/A         | Defines W vs sensor/sea state                    | Converts sensor coverage into POD            |
| **Onboard Compute**    | Edge module (e.g., NVIDIA Jetson ~150 g) | ~150 g      | 1–2 TOPS for real-time grid calc                 | Enables in-flight updates                    |
| **Mission Software**   | SAROPS-inspired planner                  | N/A         | Coverage optimizer                               | Turns probability grids into flight patterns |
| **Data Link**          | LTE/5G or satcom modem (~200 g)          | ~200 g      | 1–2 Mbps sustained                               | Feeds updates to/from shipboard console      |

**Total “payload” mass (hardware):** ~350 g (Jetson + modem), well within enterprise UAV capacity.

---

### BOM - Evidence & Audit Module (Claim 7) ###

| Component                         | Reference / Standard                                               | Spec / Target                                                       | Purpose                                                                           |
| --------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Time Sync Core**                | RFC 5905 (NTPv4); IEEE 1588 PTP; IMO MSC.333(90) (UTC co-relation) | PTP (preferred) **<1 µs** on engineered LAN; NTP fallback **≤5 ms** | Align VDR, UAV, bridge logs for reconstruction. ([RFC Editor][8])                 |
| **Evidence Encoder (UAV)**        | IEC 60945 env/EMC for shipborne gear                               | Dual-stream 4K RGB + IR; KLV/EXIF UTC stamp                         | High-fidelity, time-stamped video of search/rescue phases. ([Iteh Standards][10]) |
| **Telemetry Capture**             | MSC.333(90) §5.1–5.5 (co-related data)                             | UAV position/attitude/payload events @ ≥10 Hz                       | Co-relates with VDR/bridge events. ([IMO][1])                                     |
| **Immutable Storage Tier**        | NIST FIPS 180-4 (SHA-256)                                          | Segment hashes (1-min clips) + daily manifest; WORM bucket          | Tamper-evident chain for video/logs. ([NIST Publications][7])                     |
| **Chain-of-Custody Ledger**       | ACPO/NPCC; ISO/IEC 27037                                           | Append-only audit log (operator ID, action, time, hash)             | Evidential integrity & audit trail. ([NPCC][6])                                   |
| **Retention Policy**              | MSC.333(90) §5.2, §5.3                                             | **≥48 h** short-term; **≥6 months** long-term medium                | Mirrors VDR practice for accessibility + archive. ([IMO][1])                      |
| **Periodic Test & Certification** | SOLAS V/18.8; class circulars                                      | Annual performance test with report                                 | Verifies evidence system health for audits. ([Eagle][11])                         |

**One-page BOM mass/power (info-heavy, not weight-heavy):**

- Compute & storage (edge box): ~0.5–1.0 kg; 15–25 W.
- Time source: GNSS-disciplined clock or PTP grandmaster (rack/bridge-wing).
- Network: VLAN-isolated timing plane + QoS for PTP/NTP.

## References ##

[1]: https://www.imo.org/en/OurWork/Safety/Pages/VoyageDataRecorders.aspx "IMO MSC.333(90) - Voyage Data Recorders"
[6]: https://www.npcc.police.uk/Publication/National%20Policing%20Guidelines/ACPO%20Guidelines%20on%20Digital%20Evidence.pdf "NPCC Digital Evidence Guidelines"
[7]: https://csrc.nist.gov/publications/detail/fips/180/4/final "NIST FIPS 180-4 - Secure Hash Standard"
[8]: https://datatracker.ietf.org/doc/html/rfc5905 "RFC 5905 - Network Time Protocol Version 4"
[10]: https://www.iec.ch/ip-ratings "IEC 60945 - Maritime navigation and radiocommunication equipment and systems"
[11]: https://www.eagle.org/en/rules-and-resources/rules-and-guides.html "Eagle Classification Society Rules"

---
