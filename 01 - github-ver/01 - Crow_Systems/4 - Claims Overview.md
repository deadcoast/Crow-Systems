# Claims Overview

## Research Program Overview

We'll validate each core claim with multiple independent evidence types:
literature + bench tests + controlled drills + witnessed sea trials + audited data. Below is the map.

## 1 - Drones cut time-to-first-visual (TTFV) dramatically

What to research:

- Baseline MOB drill timelines on cruise ships (alarm→visual reacquisition).
- `CROW` timelines with auto-launch IRD + pilot takeover across day/night and sea states.

How to support:

- **Controlled A/B drills** on partner vessels: run standard MOB drill (no drone) vs identical drill with `CROW`.
  - Randomize order; repeat across conditions.
- **Metrics captured:** TTFV, time-to-GPS-fix, time-to-buoy-drop, time-to-handoff to boat.
- **Analysis:** paired comparison with confidence intervals; bootstrap for robustness; pre-registered analysis plan.
- **Third-party witness:** class society surveyor or maritime test lab present for a subset; signed witness statements.

Success criteria:

- Median TTFV reduction ≥ 60% (night) and ≥ 40% (day) vs baseline, sustained across ≥ 20 drills.

---

## [[02 - obsidian-ver/Research/3 - Claims/2 - Detection Probability]] - “Detection probability (Pdet) is high with low false positives.”

What to research:

- Realistic detection across **thermal/RGB** in varying sea states, lighting, and clothing.
- False positive sources (whitecaps, kelp, birds, glare).

How to support:

- **Harbor trials** with certified MOB mannequins (OSCAR type) and different clothing/skin-temp conditions.
- **Open-sea trials**: day/night, Sea State 2–5, upwind/downwind placements at known ranges.
- **Dataset** creation (annotated frames) → publishable detection ROC curves.

Metrics:

- Pdet by range band (0–600 m); FPR per minute; detector ROC (AUC).
- **Target:** Pdet ≥ 0.8 within first sortie envelope; FPR ≤ 0.2/min with human verify.

---

## [[02 - obsidian-ver/Research/2 - Evidence Block/3 - Evidence]] - “Auto-launch, then human-in-the-loop is safer and faster.”

What to research:

- Reliability of **auto-launch + bounded IRD**.
- **Pilot takeover latency** (alarm→pilot in command).
- Human factors: workload, situational awareness with HUD/goggles.

How to support:

- **Bench simulation** of dock→airborne cycles (≥500 cycles).
- **Timed drills** measuring takeover ≤ 60 s; command preempt latency < 300 ms.
- **Human-factors study** (NASA-TLX), pilot debriefs, error logs.

---

## [[02 - obsidian-ver/Crow_Systems/4 - Claims Overview]] - “`CROW` remains effective in real maritime conditions.”

What to research:

- Performance envelope: wind, spray, rain, night ops near a moving hull.

How to support:

- **Environmental tests:** salt-fog (ASTM B117), ingress (IP), vibration, rain/spray rigs.
- **Sea trials:** launches while ship maintains 3–5 kn headway;
  - precision dock returns; turbulence handling on leeward/windward sides.
- **Failure-mode analysis (FMEA)** with mitigations validated (e.g., beacon-only behavior in high winds).

---

## [[02 - obsidian-ver/Research/3 - Claims/5 - Tool Deployment]] - “Buoy/dye/strobe deployment improves survival odds.”

What to research:

- Time from visual to **buoy within reach**; drift offset accuracy; visibility impacts of dye/strobe.

How to support:

- **Drop accuracy tests** (CEP ≤ 10 m 95%) using up-drift aim points.
- **Visibility studies:** observer trials from:
  - Rescue boat/bridge rating detectability
  - With vs without dye/strobe at set ranges

---

## [[02 - obsidian-ver/Research/3 - Claims/6 - Probability over Uniform Patterns]] - “Probability-weighted search beats uniform patterns.”

What to research:

- Monte Carlo drift (windage + current) vs. simple expanding square for time-to-reacquisition.

How to support:

- **Replay drills** with and without PDM overlays; measure TTFV and distance flown.
- **Stat test:** Wilcoxon signed-rank on paired drills; effect size calculation.

---

## 7) Claim: “Integration aligns with SOLAS/LSA and insurer expectations”

What to research:

- Regulatory landscape:
  - SOLAS Ch. III & LSA Code (
  - rescue boats, MOB detection)
  - flag-state circulars
  - class guidance for auxiliary lifesaving equipment

- Insurer requirements for “reasonable available technology.”

How to support:

- **Regulatory matrix** mapping each `CROW` function to current clauses;
  - document that `CROW` is **auxiliary** (not replacing boats).
- **Letters of no-objection / statements of intent** from class societies after design review.
- **Risk assessment** and SOPs validated in witnessed drills.

---

## 8) Claim: “Cost/benefit and PR risk reduction are compelling”

What to research:

- CAPEX/OPEX vs. incident costs (SAR ops, delays, reputational damage).
- Case analyses of MOB incidents (time to detection, outcomes).

How to support:

- **Model** expected value (EV) reduction in loss given improved TTFV/Pdet.
- **Sensitivity analysis** across fleet sizes & incident frequencies.
- **Insurer feedback** memos on premium/coverage implications.

---

## Evidence production plan

### Phase 0 — Desk research

- Literature review:
  - MOB survivability (cold shock/hypothermia)
  - SAR drift (SAROPS)
  - thermal detection at sea
  - existing MOB camera systems

- Regulatory map:
  - SOLAS/LSA
  - MSC circulars
  - flag-state notes
  - class (DNV/ABS/LR) relevant test standards

- Deliverable: **Evidence Landscape Brief** (citations + gaps).

### Phase 1 — Bench & environmental

- Dock life-cycle (≥500 auto launch/land), ingress, salt-fog, vibration.
- Radio link and video latency measurements.
- Deliverable: **Bench Test Report** with pass/fail + photos/videos.

### Phase 2 — Harbor trials

- Controlled mannequin placements; day/night; sea states 1–3.
- Build the labeled dataset; tune detector thresholds; initial ROC.
- Deliverable: **Harbor Trial Report** (TTFV, Pdet/FPR, ROC; video reels).

### Phase 3 — Open-sea trials

- Partner vessel runs randomized A/B MOB drills (baseline vs `CROW`).
- Include moving-ship launches @ 3–5 kn; Sea State 2–5; downwind/down-current placements; dye/strobe tests.
- Witnessed subset with class society/independent lab.
- Deliverable: **Sea Trial Report** + **Witness Statements**.

### Phase 4 — Comparative analysis & whitepaper

- Stats (paired tests, CI/bootstraps), effect sizes, limitations.
- Risk assessment + SOP refinements; maintenance schedule.
- Deliverables:

  - **Peer-style Whitepaper** (methods, results, limitations).
  - **Operator SOP Pack** (drills, checklists, envelopes).
  - **Insurer Pack** (loss modeling, EV, compliance mapping).
  - **Class Submission Dossier** (drawings, FMEA, test evidence).

---

## Data integrity & trust

- **Pre-registered protocol** (timestamped) to avoid post-hoc cherry-picking.
- **Immutable logs:** signed telemetry & video hashes; provide raw data excerpts.
- **Independent witnesses** for key trials (class/insurer observers).
- **Open methods:** publish anonymized detector dataset & code stubs for peer scrutiny (as feasible).

---

## KPIs & acceptance thresholds (examples you can tune)

- TTFV median reduction ≥ 50% overall; ≥ 60% at night.
- Pdet ≥ 0.8 within 400 m; FPR ≤ 0.2/min (human-verified).
- Pilot takeover ≤ 60 s (p95) from alarm; command preempt < 300 ms.
- Drop CEP ≤ 10 m (95%); beacon CEP ≤ 10 m (95%) in Beaufort 5.
- Launch reliability ≥ 99% across 100 consecutive auto-launches.

---

## Artifacts you’ll hand decision-makers

- **Video demo reel:** side-by-side baseline vs `CROW` overlays.
- **One-page results sheet:** clear plot of TTFV reductions + ROC curves.
- **Signed witness letters** and **class pre-review notes**.
- **Raw data portal** (read-only) for auditors.
- **Operator SOPs** with training/drill checklist.

---

## Resourcing & partnerships

- **Partners needed:**
  - one cruise line for drills
  - one maritime test lab
  - one class society for witness days
  - one insurer observer

- **Procurement:** certified MOB mannequins, dye/smoke (SOLAS), measurement gear, environmental test house time.

---
