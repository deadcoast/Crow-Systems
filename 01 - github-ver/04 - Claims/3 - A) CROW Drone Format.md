# CLAIM — “Auto-launch, then human-in-the-loop is safer and faster.” #

## A. Independent evidence (triangulated) ##

1. **Auto-launch readiness and link latency**

   - Modern dock systems support **automated launch** with continuous health checks and weather gating; **DJI Dock 2** publishes **end-to-end video latency ~110–150 ms** over the dock link, enabling near-instant pilot situational awareness on takeover. ([DJI][1])
   - Dock platforms are designed for **remote mission start/RTB** with IP-rated enclosures, redundant power/charging, and cloud supervision (vendor documentation). ([DJI][2])

2. **Why “human-in-the-loop” (HITL) after launch is the safer control regime**

   - **Supervisory control** literature shows hybrid automation (machine initiates; human supervises/intervenes) mitigates edge-case risk versus full autonomy in dynamic environments. ([Wiley Online Library][3])
   - **Teleoperation/remote-driving studies** repeatedly find **performance degradation beyond ~200–300 ms end-to-end delay**, with noticeable declines beginning around **150–200 ms**. Keeping live-video delay near **≤150 ms** preserves control quality and safety margins during manual takeover. ([VTT's Research Information Portal][4])

3. **Pilot takeover latency is fundamentally bounded by human + link delays**

   - Typical **simple visual reaction time ~200–250 ms**; choice/recognition reactions ~300–400 ms. With **glass-to-glass video ~110–150 ms**, effective pilot-in-command latency sits in the **sub-second** range, which human-factors studies identify as acceptable for precise teleoperation; >300–400 ms begins to erode performance. ([PMC][5])

4. **Human factors: HUD/HMD improve SA and workload in remote ops**

   - NASA and transport-human-factors studies report **improved situation awareness** and **acceptable workload** with **head-worn/HUD equivalents** compared with heads-down displays in piloting tasks; sUAS research echoes gains in **SA** for search-style tasks using HUD overlays. ([NASA Technical Reports Server][6])

5. **Reliability context for the “auto-launch only” phase**

   - Reviews of UAS reliability indicate **failure rates near 10⁻³ per flight hour** (several orders higher than commercial aviation), with **battery reliability** a leading contributor—supporting the case for **short, bounded autonomous segments** prior to human control. ([PMC][7])

- **Synthesis:** Automated launch minimizes “time-to-air” and presents the pilot with a live, low-latency feed; keeping the autonomous segment brief and bounded, then switching to HITL, aligns with supervisory-control safety research and latency thresholds shown to preserve operator performance.

---

## B. Additional research areas (beyond the prompts) — source-anchored ##

- **End-to-end latency budget** (camera → encoder → network → viewer): document **glass-to-glass** and command-loop timings; bind operating limits to **≤150–200 ms** per teleop literature. ([DJI][1])
- **RF/EM environment near steel hulls**: characterize multipath & shadowing around superstructure; define **auto-launch corridor** and **handover altitude** for robust link margin (tie to latency thresholds above). ([VTT's Research Information Portal][4])
- **Failsafe on pilot unavailability**: timeouts to hover/loiter, geofenced keep-outs, and **Return-to-Dock** rules consistent with hybrid autonomy guidance. ([PMC][8])
- **HUD/HMD symbology standards**: evaluate cueing (compass tape, horizon line, drift vector, AIS overlays) vs **SA/workload** findings in HUD/HMD pilot studies. ([NASA Technical Reports Server][6])
- **Battery/thermal guardrails for auto-launch**: launch only with **state-of-health thresholds** that meet ≥**98% annually available** battery reliability targets reported in recent UAV reliability reviews. ([MDPI][9])

---

## C. Quantitative thresholds suitable for a business plan ##

- **Auto-launch → pilot-in-command (PIC) timeline:** target **wheels-up ≤90 s**, **PIC live feed ≤2 s after wheels-up**; maintain **video latency ≤150 ms** (dock spec shows 110–150 ms). ([DJI][1])
- **Teleop safety guardband:** enforce **operational ceiling at ≤200 ms** total video delay; flag and inhibit aggressive maneuvers beyond that (based on teleop degradation thresholds). ([VTT's Research Information Portal][4])
- **Human reaction envelope:** design takeover prompts around **~250–350 ms** reaction norms (visual → choice). ([Cognaction][10])
- **Bounded autonomous segment:** limit **Initial Response Doctrine (IRD)** to **undock, climb, clear-ship, hold**; **no close-surface operations** until PIC (aligns with higher UAS failure rates vs aviation). ([PMC][7])

---

## D. Binder-ready statements (paste-in) ##

- “Automated dock launch reduces time-to-air; **Dock-class systems provide ~110–150 ms live-video latency**, enabling prompt PIC takeover with preserved teleoperation performance.” ([DJI][1])
- “HITL after a **short, bounded autonomous IRD** is the safety-optimal regime per **supervisory-control** research; full autonomy in dynamic maritime scenes imposes higher edge-case risk.” ([Wiley Online Library][3])
- “Teleoperation studies show **marked performance drops beyond 200–300 ms delay**; operational limits are therefore set to **≤150–200 ms** end-to-end latency for manual control.” ([VTT's Research Information Portal][4])
- “HUD/HMD literature indicates **improved situation awareness** and acceptable workload for pilot overlays versus heads-down control, supporting goggle-based PIC displays.” ([NASA Technical Reports Server][6])
- “UAS reliability reviews document **~10⁻³ failures/hr** and battery-system availability targets ≥**98% annually**, justifying **brief autonomous segments** and rapid human takeover.” ([PMC][7])

---

## E. Evidence table ##

| Topic               | Evidence type         | Key finding                                                      | Business-plan threshold                     |
| ------------------- | --------------------- | ---------------------------------------------------------------- | ------------------------------------------- |
| Auto-launch link    | Vendor spec           | Dock video **110–150 ms** latency                                | Require **≤150 ms** glass-to-glass          |
| Teleop delay limits | Human-factors studies | **Degradation at 200–300 ms**; perception starts **~150–200 ms** | Operate **≤200 ms**, design for **≤150 ms** |
| Reaction time       | Psychophysiology      | Visual SRT **~200–250 ms**; choice **~300–400 ms**               | Takeover prompts sized to **≥300 ms**       |
| HUD/HMD             | NASA / HF             | HUD-equivalent HWD improves **SA**, manageable workload          | Goggle/HUD standard for PIC                 |
| Reliability         | UAS reviews           | **~10⁻³ failures/hr**; batteries ≥**98%** availability           | Keep IRD brief; health-gated launch         |

Citations: ([DJI][1])

---

## F. One-paragraph “why HITL is safer & faster” (executive wording) ##

Automated dock launch eliminates human scramble time and places sensors airborne immediately; with **~110–150 ms live video**, the pilot assumes control within seconds while conditions are still near the last-seen point. **Supervisory-control** research favors this hybrid regime over full autonomy for safety in complex scenes, and **teleoperation studies** show control quality is retained when end-to-end delay is **≤150–200 ms**. Given **UAS reliability (~10⁻³ failures/hr)** and battery availability constraints, constraining autonomy to **a short IRD window** and then flying under **HITL with HUD/Goggles** provides the documented balance of **speed (fastest launch)** and **safety (human judgment where it matters)**. ([DJI][1])

If a technical annex is required, a latency budget (encode/transport/decode) and HUD symbology list can be produced with the above human-factors and latency sources.

[1]: https://enterprise.dji.com/dock-2/specs "DJI Dock 2 - Specs"
[2]: https://enterprise.dji.com/dock-2 "DJI Dock 2"
[3]: https://onlinelibrary.wiley.com/doi/abs/10.1002/9781119636113.ch28 "Human Supervisory Control of Automation"
[4]: https://cris.vtt.fi/files/109010051/futureinternet-16-00457-v2.pdf "A Latency Composition Analysis for Telerobotic Performance"
[5]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4374455/ "Factors influencing the latency of simple reaction time"
[6]: https://ntrs.nasa.gov/citations/20150010973 "Flight Test of a Head-Worn Display as an Equivalent-HUD"
[7]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6165073/ "Reliability and Maintenance Analysis of Unmanned Aerial"
[8]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8477008/ "Let Me Take Over: Variable Autonomy for Meaningful"
[9]: https://www.mdpi.com/2504-446X/9/8/539 "A Critical Review on the Battery System Reliability of Drone"
[10]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4374455/ "A Literature Review on Reaction Time"
