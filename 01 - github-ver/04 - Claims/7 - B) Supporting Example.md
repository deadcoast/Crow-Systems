# Supporting and Worked Example #

CROW Systems evidence pipeline mirrors VDR practice: all video (RGB/LWIR), telemetry, and bridge records are **UTC-synchronized** (PTP/NTP), sealed with **SHA-256** manifests, and retained on WORM storage. Chain-of-custody is enforced via an **append-only ledger**. This satisfies IMO **MSC.333(90)** expectations for co-related, tamper-evident incident data; aligns with **ISM Code** reporting; and follows **ACPO/ISO 27037** digital-evidence principles. The result is an audit-ready package that improves accountability and speeds investigations.

## Evidence & Audit Pipeline Scenario ##

*Fixed numbers, verifiable against standards:*

- **Vessel:** Passenger ship “EXAMPLE,” UTC time synched by **PTP grandmaster** on bridge LAN; UAV console and encoder are PTP clients; VDR is UTC-referenced.
- **Event:** MOB alarm at **2025-06-18 21:14:30.000 UTC** (from BNWAS/MOB button).

Systems involved:
    - **VDR** (per **MSC.333(90)**) recording bridge audio, VHF, AIS, gyro/Speed, ECDIS screenshots, UTC.
    - **UAV Evidence Encoder** capturing **RGB (4K/30) + LWIR (640/30)** with **on-frame UTC**, plus **telemetry @10 Hz** (position/attitude/payload events).
    - **Audit service** computing **SHA-256** for 60-second file segments and writing an **append-only event ledger**.
    - **Time sync:** **IEEE-1588 PTP** on ship LAN; **NTPv4** fallback on the UAV control tablet.

---

## Step-by-step pipeline (timestamps, hashes, and checks) ##

### 1) Time synchronization (pre-incident, continuous) ###

- **PTP**: PMU on bridge is grandmaster; **sync status** on encoder and UAV console shows **offset = 0.28 ms (P95)**.
- **Fallback**: UAV tablet also runs **NTPv4** to the ship’s stratum-1; measured skew **≤ 3 ms** on audit page.

    - Why this matters: VDR, UAV video, and telemetry are **co-related** to the same UTC timebase (VDR requires this).
    - References: PTP/NTP accuracy ranges and UTC correlation in VDR:

        - RFC 5905 (NTPv4) • NIST NTP performance • NIST/EndRun/NVIDIA PTP primers • **MSC.333(90)** VDR time correlation.
        - Links: [RFC 5905](https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf) • [NIST NTP](https://tf.nist.gov/general/pdf/2776.pdf) • [NIST PTP tutorial](https://www.nist.gov/document/tutorial-basicpdf) • [EndRun PTP](https://endruntechnologies.com/pdf/PTP-1588.pdf) • [NVIDIA PTP DG](https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf) • [MSC.333(90)](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf)

### 2) Event begins (MOB alarm fired) ###

- **21:14:30.000** MOB alarm asserted (BNWAS/MOB; VDR discrete input **D-MOB=1**).
- VDR writes to **Incident ring buffer**; UAV encoder marks **EventID=“MOB-2025-06-18-211430Z”** in on-screen OSD and telemetry.

### 3) Capture windows and segmentation ###

- **Video segmentation policy:** 60-second files, rolling, independent for RGB and LWIR.
- **Telemetry** segmented into 60-second JSON lines with matching filenames.
- **Files created** (examples):

    - `RGB_20250618_2114Z_part01.mp4` (21:14:00–21:14:59)
    - `RGB_20250618_2115Z_part02.mp4` (21:15:00–21:15:59)
    - `LWIR_20250618_2115Z_part02.mkv` (same window)
    - `TEL_20250618_2115Z_part02.jsonl` (10 Hz telemetry)

### 4) Immediate integrity sealing (per digital evidence practice) ###

- At file close, audit daemon computes **SHA-256** and appends to **manifest.csv** with UTC.
- Example row (hash shortened for display):

```makefile
2025-06-18T21:16:00.200Z, RGB_20250618_2115Z_part02.mp4, \
c1b8d6f2e1a9d77ef7b29c39c9a7a5c8d8e1b3f6a9c0e4e2... (SHA-256)
```

- **Chain-of-custody ledger entry** (append-only):

```makefile
2025-06-18T21:16:00.240Z  OP=pipeline  EVT=file_close  USER=system \
OBJ=RGB_20250618_2115Z_part02.mp4  SHA256=c1b8d6f2...  SIG=ed25519:ab93...
```

- Evidence principles referenced: **ACPO/NPCC Good Practice** & **ISO/IEC 27037** (originals preserved; audit trail; competent handling; integrity).

    - Links: [ACPO/NPCC v5](https://www.npcc.police.uk/Publication/National%20Policing%20Guidelines/ACPO%20Guidelines%20on%20Digital%20Evidence.pdf) • [ISO/IEC 27037 (mirror)](https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf)
- Hash algorithm: **SHA-256** per **NIST FIPS 180-4**.

    - Links: [FIPS 180-4](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf)

### 5) Co-relation check (VDR ⇄ UAV) ###

- **21:15:07.400** UAV telemetry logs **PayloadDrop=1** with on-frame UTC **21:15:07.3**; RGB frame shows splash at **21:15:07.3** (OSD time).
- VDR audio shows “**Drop away**” call at **21:15:07.5**; ECDIS screenshot at **21:15:08** marks MOB waypoint.
- **Skew report**: Max time delta between sources **≤ 2.0 ms** (PTP clients) and **≤ 4.5 ms** (NTP tablet), within target **≤ 5 ms**.

    - VDR time-correlation requirement reference: **MSC.333(90)** (VDR data items co-related in time).
    - Link: [MSC.333(90)](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf)

### 6) Retention and export (aligned to VDR practice) ###

- **Short-term tier:** minimum **48 h** rolling on-board SSD (mirrors VDR quick-access expectation).
- **Long-term tier:** **WORM** object storage ashore; retention **≥ 6 months** for MOB-flagged incidents; **daily manifest hashes** bundled and countersigned.

    - VDR retention/performance standard: **MSC.333(90) §5.2–5.3**.
    - Links as above.

### 7) Audit pack for Safety/Flag/Class (deliverable list) ###

- **/evidence/2025-06-18-MOB-211430Z/**

    - `manifest.csv` (all segments + SHA-256)
    - `ledger.log` (append-only chain-of-custody)
    - `RGB_...mp4`, `LWIR_...mkv`, `TEL_...jsonl` (segmented)
    - `timesync_report.json` (PTP offset histogram; NTP stats)
    - `vdr_extract.zip` (from approved VDR playback tool: audio, ECDIS scrapes, AIS snippets)
    - `audit_summary.pdf` (who/what/when; checksums; deviations; signatures)
- **Annual assurance:** wrap this pipeline under ship’s **SOLAS V/18.8 performance test** umbrella (same idea used for VDR annual tests) — one consolidated verification per year for evidence subsystem readiness.

    - Link: [ABS note referencing SOLAS testing](https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf)

---

## Acceptance criteria (the checklist reviewers look for) ##

- **Time alignment:** PTP clients **< 1 ms P95**; NTP devices **≤ 5 ms P95**; incident skew report attached.
- **Integrity:** Every file segment listed in `manifest.csv` with **SHA-256**; daily manifest signed; **no hash mismatches**.
- **Completeness:** RGB, LWIR, telemetry, and VDR extracts cover **alarm ± 20 min** with no gaps.
- **Chain-of-custody:** `ledger.log` is **append-only**, monotonic UTC, cryptographically signed (operator actions present: launch, control transfer, payload release).
- **Retention:** MOB incident copied to WORM store within **≤ 24 h**; retention policy metadata shows **≥ 6 months**.
- **EMC/Environment:** evidence hardware (encoders/switches near radios) documented to **IEC 60945**.

    - Link: [IEC 60945 sample](https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf)

---

## Failure modes & how the record still holds ##

- **PTP grandmaster loss:** NTP fallback continues; skew exceeds target → **red banner** on audit; include drift plot; still within reconstruction tolerances per investigation norms (second-level tolerance acceptable with audio corroboration).
- **Segment loss/corruption:** manifest shows **missing hash**; investigation uses neighboring segments + VDR audio/ECdis to bridge; integrity of remaining files provable.
- **Clock step on a device:** audit daemon raises **clock-step alert**; downstream viewer clamps to VDR UTC; report includes offset correction used.

---

## Investigator reconstruction (how this gets used) ##

1. Load VDR in official playback; mark **MOB alarm** and **ECDIS MOB mark**.
2. Import UAV **RGB/LWIR** and **telemetry**; tool aligns streams by UTC, displays **on-frame UTC** and **course/speed**.
3. Jump to **PayloadDrop** event from telemetry (21:15:07.4) and verify **RGB/LWIR** splash frame; cross-check VDR audio (“Drop away”) at 21:15:07.5.
4. Confirm **strobe-on** event (water contact) in LWIR; measure **time-to-drop** and **time-to-first-visual** directly.
5. Produce **timeline exhibit** with clipped videos, hash report, and event ledger — defensible to Class/Flag/MAIB/ATSB.

---

## Payload BOM — **Evidence & Audit Module** ##

| Component                | Reference / Standard                         | Spec / Target                                     | Purpose                                     |
| ------------------------ | -------------------------------------------- | ------------------------------------------------- | ------------------------------------------- |
| **Time Sync Core**       | RFC 5905 (NTPv4); IEEE 1588 PTP; MSC.333(90) | PTP **< 1 µs** (engineered LAN), NTP **≤ 5 ms**   | Align VDR, UAV, bridge logs.                |
| **UAV Evidence Encoder** | IEC 60945 env/EMC                            | Dual stream 4K RGB + 640 LWIR; UTC OSD; KLV/EXIF  | High-fidelity time-stamped capture.         |
| **Telemetry Capture**    | MSC.333(90) correlation                      | 10 Hz pos/attitude/events; UTC                    | Event correlation (launch, drop, recovery). |
| **Integrity Engine**     | NIST FIPS 180-4; ACPO/ISO 27037              | SHA-256 per 60-s file; daily manifest + signature | Tamper-evident chain.                       |
| **Event Ledger**         | ACPO/ISO 27037                               | Append-only, operator ID, UTC, hash pointer       | Chain-of-custody.                           |
| **Retention Store**      | MSC.333(90) §§5.2–5.3                        | On-board ≥ 48 h; shore WORM ≥ 6 mo                | Access + archive.                           |
| **Annual Assurance**     | SOLAS V/18.8; class circulars                | Yearly performance test report                    | System health & compliance.                 |

---

## Sources ##

- **VDR performance standard (IMO MSC.333(90))** — data security, time correlation, retention: [https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf](https://wwwcdn.imo.org/localresources/en/KnowledgeCentre/IndexofIMOResolutions/MSCResolutions/MSC.333%2890%29.pdf)
- **IMO VDR page**: [https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx](https://www.imo.org/en/OurWork/Safety/Pages/VDR.aspx)
- **ABS regulatory note (VDR/EPIRB performance standards)**: [https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf](https://ww2.eagle.org/content/dam/eagle/regulatory-news/2022/Regulatory%20News%20-%20IMO%20Revised%20Performance%20Standards%20for%20EPIRBs%20and%20VDRs.pdf)
- **ISM Code & Guidelines**: [https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf](https://maritimesafetyinnovationlab.org/wp-content/uploads/2014/02/ism-code.pdf)
- **Casualty Investigation Code (IMO MSC.255(84))**: [https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf](https://wwwcdn.imo.org/localresources/en/OurWork/MSAS/Documents/Res.MSC.255%2884%29CasualtyIinvestigationCode.pdf)
- **ACPO/NPCC Digital Evidence Guide (v5)**: [https://www.npcc.police.uk/Publication/National%20Policing%20Guidelines/ACPO%20Guidelines%20on%20Digital%20Evidence.pdf](https://www.npcc.police.uk/Publication/National%20Policing%20Guidelines/ACPO%20Guidelines%20on%20Digital%20Evidence.pdf)
- **ISO/IEC 27037 (overview/mirror)**: [https://www.iso.org/standard/44381.html](https://www.iso.org/standard/44381.html) • [https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf](https://amnafzar.net/files/1/ISO%2027000/ISO%20IEC%2027037-2012.pdf)
- **NIST FIPS 180-4 (SHA-256)**: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.180-4.pdf)
- **NTP/PTP timing**: RFC 5905: [https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf](https://www.rfc-editor.org/rfc/pdfrfc/rfc5905.txt.pdf) • NIST NTP: [https://tf.nist.gov/general/pdf/2776.pdf](https://tf.nist.gov/general/pdf/2776.pdf) • NIST PTP tutorial: [https://www.nist.gov/document/tutorial-basicpdf](https://www.nist.gov/document/tutorial-basicpdf) • EndRun PTP: [https://endruntechnologies.com/pdf/PTP-1588.pdf](https://endruntechnologies.com/pdf/PTP-1588.pdf) • NVIDIA PTP DG: [https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf](https://network.nvidia.com/files/doc-2020/ieee-1588-precision-time-protocol-design-guide.pdf)
- **IEC 60945** (marine EMC/environment): [https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf](https://cdn.standards.iteh.ai/samples/6359/5e7d127ed2e74ba1af3aee001a7ca5cb/IEC-60945-2002.pdf)
- **MAIB Safety Digest 1/2025** (investigation lessons): [https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf](https://assets.publishing.service.gov.uk/media/67ebba71e9c76fa33048c561/2025-1-SafetyDigest.pdf)
- **ATSB investigation process**: [https://www.atsb.gov.au/about_atsb/investigation-process](https://www.atsb.gov.au/about_atsb/investigation-process)
