# CLAIM [7/7] — “Data capture & audit improves accountability.”

## A) Independent evidence (with links)

1. **Voyage Data Recorder (VDR) purpose is investigation + tamper-resistant storage**
   IMO performance standard **MSC.333(90)** states the VDR “maintain[s] a store… of information… leading up to and following an incident,” made available to the Administration and shipowner “for use during any subsequent safety investigation to identify the cause(s)” (incl. data security, time correlation, and retention requirements).
   🔗 [https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf) ([IMO][1])

2. **VDR carriage + performance testing are mandated**
   SOLAS V/20 requires VDRs on passenger ships; class/flag guidance reflects **annual performance tests** for VDR systems and sensors (SOLAS V/18.8).
   🔗 IMO VDR overview: [https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx](https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx)
   🔗 ABS Regulatory note (amendments to performance standards): [https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf](https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf)
   🔗 Danelec regulatory summary: [https://www.danelec.com/newsroom/voyage-data-recorder-regulations-and-performance-standards](https://www.danelec.com/newsroom/voyage-data-recorder-regulations-and-performance-standards) ([International Maritime Organization][2])

3. **ISM Code requires procedures for reporting + analyzing non-conformities/accidents**
   The ISM framework (SOLAS IX) mandates a Safety Management System that includes **reporting and analysing non-conformities, accidents and hazardous occurrences** (internal audits, management review).
   🔗 ISM Code + Guidelines compendium (official text reproduced): [https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf](https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf) ([Maritime Safety Innovation Lab LLC][3])

4. **Casualty Investigation Code (IMO) — independent safety investigations rely on records**
   The Code underpins international practice for **evidence-based** investigations following marine casualties.
   🔗 [https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf](https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf) ([IMO][4])

5. **MAIB/ATSB: investigations use recorded data to produce safety lessons**
   Official safety digests emphasize **learning from evidence** gathered post-occurrence (VDR/CCTV/logs).
   🔗 MAIB Safety Digest 1/2025: [https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf](https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf)
   🔗 MAIB digests collection: [https://www.gov.uk/government/collections/maib-safety-digests](https://www.gov.uk/government/collections/maib-safety-digests)
   🔗 ATSB investigation process/annual reports (no-blame, evidence-driven): [https://www.atsb.gov.au/about_atsb/investigation-process](https://www.atsb.gov.au/about_atsb/investigation-process) ; [https://www.atsb.gov.au/sites/default/files/2023-11/ATSB%20Annual%20Report%202022-23_2.pdf](https://www.atsb.gov.au/sites/default/files/2023-11/ATSB%20Annual%20Report%202022-23_2.pdf) ([GOV.UK][5])

6. **Digital evidence integrity (chain-of-custody) standards**
   The **ACPO/NPCC Good Practice Guide** and **ISO/IEC 27037** define principles: don’t alter original data, ensure a competent person handles any access, maintain an audit trail, and preserve integrity/authenticity.
   🔗 ACPO/NPCC Guide (v5): [https://npcc.police.uk/documents/crime/2014/Revised%20Good%20Practice%20Guide%20for%20Digital%20Evidence_Vers%205_Oct%202011_Website.pdf](https://npcc.police.uk/documents/crime/2014/Revised%20Good%20Practice%20Guide%20for%20Digital%20Evidence_Vers%205_Oct%202011_Website.pdf)
   🔗 ISO/IEC 27037 overview: [https://www.iso.org/standard/44381.html](https://www.iso.org/standard/44381.html) (open-brief) / mirror PDF: [https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf](https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf) ([NPCC][6])

7. **Cryptographic hashing for tamper-evidence**
   NIST **FIPS 180-4** (SHA-256) is the federal standard used to detect alteration of digital records.
   🔗 [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf) ; [https://csrc.nist.gov/pubs/fips/180-4/upd1/final](https://csrc.nist.gov/pubs/fips/180-4/upd1/final) ([NIST Publications][7])

8. **Time correlation across devices (VDR/UAV/bridge logs)**
   VDR requires UTC-referenced time and co-related data streams. **NTPv4 (RFC 5905)** and **IEEE 1588 PTP** are the established protocols: NTP typically millisecond-range on LAN; PTP routinely sub-microsecond on engineered networks.
   🔗 RFC 5905 PDF: [https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf](https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf)
   🔗 NIST paper on NTP limits (~1 ms on LAN): [https://tf.nist.gov/general/pdf/2776.pdf](https://tf.nist.gov/general/pdf/2776.pdf)
   🔗 PTP primers (NIST tutorial; EndRun; vendor white papers): [https://www.nist.gov/document/tutorial-basicpdf](https://www.nist.gov/document/tutorial-basicpdf) ; [https://endruntechnologies.com/pdf/PTP-1588.pdf](https://endruntechnologies.com/pdf/PTP-1588.pdf) ; [https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf](https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf) ([RFC Editor][8])

---

## B) Quantitative thresholds (business-plan ready)

- **Record & retain (aligned to VDR practice):**
  Continuous dual-channel capture (UAV RGB+IR + shipboard console screen/video) with **time-aligned** telemetry and UTC timestamps. **Minimum retention:** **≥48 h** for quick-access tiers and **≥6 months** for long-term media (mirroring VDR §5.2 requirements). ([IMO][1])
- **Integrity:**
  **SHA-256** hashes per file segment (e.g., 1-min clips) + daily manifest; immutable object storage (WORM policy) on shore. ([NIST Publications][7])
- **Time sync:**
  **PTP (IEEE 1588)** on ship LAN for sub-µs alignment where feasible; otherwise **NTPv4** with target **≤5 ms** skew across VDR/UAV/bridge logging hosts. ([NIST][9])
- **Auditability:**
  Machine-readable **event ledger** (append-only) logging operator actions (pilot-in-command changes, payload drops) with user ID + timestamp + hash pointer (per ACPO/ISO 27037 principles). ([NPCC][6])
- **Environmental/EMC:**
  Evidence-capture hardware (encoders, storage, PoE switches near radio gear) designed/tested against **IEC 60945** for maritime environments. ([Iteh Standards][10])

---

## D) Evidence table (with links)

| Source                            | Key point                                                                                          | Link                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| IMO **MSC.333(90)**               | VDR purpose, data security, time correlation, retention (≥48 h fixed/float-free; long-term medium) | [https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf) ([IMO][1])                                                                                                                                                                                                                                                                                                                  |
| SOLAS + class guidance            | VDR carriage; annual performance testing                                                           | ABS: [https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf](https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf) ; IMO page: [https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx](https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx) ([Eagle][11])                                                                                           |
| **ISM Code**                      | SMS must report/analyze accidents & non-conformities                                               | [https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf](https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf) ([Maritime Safety Innovation Lab LLC][3])                                                                                                                                                                                                                                                                                                                                                       |
| **Casualty Investigation Code**   | International foundation for evidence-based investigations                                         | [https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf](https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf) ([IMO][4])                                                                                                                                                                                                                                                                                                                  |
| **ACPO/NPCC** & **ISO/IEC 27037** | Digital evidence integrity, audit trail, preservation                                              | [https://npcc.police.uk/documents/crime/2014/Revised%20Good%20Practice%20Guide%20for%20Digital%20Evidence_Vers%205_Oct%202011_Website.pdf](https://npcc.police.uk/documents/crime/2014/Revised%20Good%20Practice%20Guide%20for%20Digital%20Evidence_Vers%205_Oct%202011_Website.pdf) ; [https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf](https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf) ([NPCC][6])                                                                                                                      |
| **NIST FIPS 180-4**               | SHA-256 for tamper-evident hashing                                                                 | [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf) ([NIST Publications][7])                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **NTP/PTP**                       | Time sync accuracy ranges (ms for NTP; sub-µs for PTP)                                             | RFC 5905: [https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf](https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf) ; NIST/EndRun/NVIDIA PTP docs: [https://tf.nist.gov/general/pdf/2776.pdf](https://tf.nist.gov/general/pdf/2776.pdf) ; [https://endruntechnologies.com/pdf/PTP-1588.pdf](https://endruntechnologies.com/pdf/PTP-1588.pdf) ; [https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf](https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf) ([RFC Editor][8]) |
| **IEC 60945**                     | Marine environmental/EMC requirements for electronics                                              | [https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf](https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf) ([Iteh Standards][10])                                                                                                                                                                                                                                                                                                                                            |
| **MAIB/ATSB**                     | Safety investigations convert records into lessons learned                                         | MAIB SD 1/2025: [https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf](https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf) ; ATSB process: [https://www.atsb.gov.au/about_atsb/investigation-process](https://www.atsb.gov.au/about_atsb/investigation-process) ([GOV.UK][5])                                                                                                                                                                                              |

---

## E) Payload BOM — **Evidence & Audit Module** (Claim 7)

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

---

## Sources

- IMO **MSC.333(90)** — VDR performance: [https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf) ([IMO][1])
- IMO — VDR overview: [https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx](https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx) ([International Maritime Organization][2])
- ABS Regulatory note on VDR standards: [https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf](https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf) ([Eagle][11])
- Danelec VDR regulations summary: [https://www.danelec.com/newsroom/voyage-data-recorder-regulations-and-performance-standards](https://www.danelec.com/newsroom/voyage-data-recorder-regulations-and-performance-standards) ([Danelec][12])
- ISM Code & Guidelines: [https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf](https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf) ([Maritime Safety Innovation Lab LLC][3])
- IMO Casualty Investigation Code: [https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf](https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf) ([IMO][4])
- MAIB Safety Digest 1/2025: [https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf](https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf) ; MAIB digests: [https://www.gov.uk/government/collections/maib-safety-digests](https://www.gov.uk/government/collections/maib-safety-digests) ([GOV.UK][5])
- ATSB investigation process / annual report: [https://www.atsb.gov.au/about_atsb/investigation-process](https://www.atsb.gov.au/about_atsb/investigation-process) ; [https://www.atsb.gov.au/sites/default/files/2023-11/ATSB%20Annual%20Report%202022-23_2.pdf](https://www.atsb.gov.au/sites/default/files/2023-11/ATSB%20Annual%20Report%202022-23_2.pdf) ([ATSB][13])
- NIST **FIPS 180-4** (SHA-256): [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf) ; [https://csrc.nist.gov/pubs/fips/180-4/upd1/final](https://csrc.nist.gov/pubs/fips/180-4/upd1/final) ([NIST Publications][7])
- NTPv4 **RFC 5905**: [https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf](https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf) ; NIST NTP performance: [https://tf.nist.gov/general/pdf/2776.pdf](https://tf.nist.gov/general/pdf/2776.pdf) ([RFC Editor][8])
- PTP (IEEE 1588) intros: NIST tutorial: [https://www.nist.gov/document/tutorial-basicpdf](https://www.nist.gov/document/tutorial-basicpdf) ; EndRun: [https://endruntechnologies.com/pdf/PTP-1588.pdf](https://endruntechnologies.com/pdf/PTP-1588.pdf) ; NVIDIA design guide: [https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf](https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf) ([NIST][9])
- **IEC 60945** (marine EMC/environment): [https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf](https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf) ([Iteh Standards][10])

---

[1]: https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf "MSC 333 90"
[2]: https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx?utm_source=chatgpt.com "Voyage Data Recorders"
[3]: https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf "IB117E.indd"
[4]: https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf?utm_source=chatgpt.com "Casualty Investigation Code"
[5]: https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf?utm_source=chatgpt.com "MAIB Safety Digest 1/2025"
[6]: https://npcc.police.uk/documents/crime/2014/Revised%20Good%20Practice%20Guide%20for%20Digital%20Evidence_Vers%205_Oct%202011_Website.pdf?utm_source=chatgpt.com "ACPO Good Practice Guide for Digital Evidence"
[7]: https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf?utm_source=chatgpt.com "nist.fips.180-4.pdf"
[8]: https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf?utm_source=chatgpt.com "Internet Engineering Task Force (IETF)"
[9]: https://www.nist.gov/document/tutorial-basicpdf?utm_source=chatgpt.com "IEEE-1588 Standard for a Precision Clock Synchronization ..."
[10]: https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf?utm_source=chatgpt.com "IEC 60945:2002"
[11]: https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf?utm_source=chatgpt.com "IMO Revised Performance Standards for EPIRBs and VDRs"
[12]: https://www.danelec.com/newsroom/voyage-data-recorder-regulations-and-performance-standards?utm_source=chatgpt.com "Danelec Newsroom | Voyage Data Recorder requirements"
[13]: https://www.atsb.gov.au/about_atsb/investigation-process?utm_source=chatgpt.com "The investigation process"
