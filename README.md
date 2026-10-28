# J26-CS-323

**A Unified Cyber Governance and Digital Trust Framework for Banking AI Systems**

SLIIT Faculty of Computing · IT4010 Research Project (2026) · Cyber Security specialisation, IAS research cluster · Panel CS-P02

Supervisor: Mr. Deemantha Siriwardhana · Co-supervisor: Ms. Ayesha Wijesuriya

## What this project is

An inspection method for AI systems used in banks. One AI system is assessed for **trust**, **cyber risk** and **regulatory compliance**, and the three results are combined into one auditable governance decision: **Approve, Monitor, Restrict or Reject**, with a named owner for every follow-up action.

The project builds no machine-learning model and uses no real bank or customer data. Every component assesses the same **simulated AI-enabled credit-scoring system**, split into four layers: training data, AI model, inputs and interfaces, and outputs and decisions.

## Components

| # | Component | Owner | Output |
|---|---|---|---|
| C1 | AI Cyber Trust Assessment | K H Gunatilake (IT23210356) — group leader | Cyber Trust Index (CTI, 0–100) and a six-dimension trust profile |
| C2 | AI Cyber Risk Exposure (AICRE) | Y M K Jayasinghe (IT23432666) | Cyber Risk Exposure Index (CREI, 0–100), band Low / Medium / High / Critical, priority threats |
| C3 | Regulatory Compliance Harmonisation | Madugaswaththa A S (IT23245488) | Compliance Coverage Score (CCS %), harmonised control set, gap register |
| C4 | Governance Decision and Accountability | H D P P Jayasekara (IT23293830) | Verdict (Approve / Monitor / Restrict / Reject), prioritised actions with named owners (RACI across the Three Lines of Defense), accountability checks, decision authority |

C1, C2 and C3 are independent. C4 combines their outputs.

## Proof-of-concept tools (Progress Presentation 1)

Each component has one self-contained web page in its own folder:

| Folder | Tool | Built-in test cases |
|---|---|---|
| [`component-1-cyber-trust/`](component-1-cyber-trust/index.html) | Cyber Trust Index | 4 (one per verdict band) |
| [`component-2-risk-exposure/`](component-2-risk-exposure/index.html) | Cyber Risk Exposure Index | 4 deployment variants (one per band) |
| [`component-3-compliance-harmonisation/`](component-3-compliance-harmonisation/index.html) | Compliance Coverage Score | 4 (including an EU-scope applicability case) |
| [`component-4-governance-decision/`](component-4-governance-decision/index.html) | Governance Decision Scorecard | 6 scenarios (three decided by override rules) + 7 accountability tests |

### How to run

1. Open the `index.html` file in any modern browser (Chrome, Edge or Firefox). There is nothing to install or build.
2. Pick a test case at the top of the page. The score, verdict and evidence update straight away.
3. Scroll down to the **Test case verification** panel (C4: **Scenario testing**). It recomputes every test case and shows PASS or FAIL against the result fixed in advance, with a weight-sensitivity check. All 25 test cases across the four tools passed on 24 October 2026.

The tools run offline. With an internet connection they load the IBM Plex fonts from Google Fonts; without one they fall back to the system font. No data leaves the computer.

### What each tool shows

- **C1** — 18 evidence-based indicators scored Absent / Partial / Full against a written guide; AHP-derived weights with the consistency ratio; a warning when a score has no evidence recorded.
- **C2** — rule-based selection of 13 AI threats (MITRE ATLAS, NIST AI 100-2, OWASP LLM); five context-exposure factors; likelihood × impact with control discounting; override rules that stop an average from hiding one severe threat.
- **C3** — 12 harmonised controls traced to 42 requirements in 8 sources, using six relationship types; applicability check; weighted coverage score; conflict register; gap register; comparison with two baselines.
- **C4** — normalisation of the three inputs; AHP weights; five override rules; then the accountability model:
  - findings from C1–C3 that need the same control are merged into one prioritised action;
  - each action is assigned with RACI to named people in an editable owner register for the simulated bank (fictional people): Accountable and Responsible on the 1st line, a 2nd-line reviewer who signs off closure, and internal audit as 3rd-line assurance;
  - accountability checks re-run on every change: CHK-1 coverage (every action fully assigned, target 100%), CHK-2 line placement, CHK-3 independence (nobody reviews or audits their own work), CHK-4 the verdict signer does not own the system;
  - decision authority rises with the verdict (AI Governance Committee → Chief Risk Officer → board risk committee), and escalation rules fire when an action is set to Overdue or left awaiting sign-off;
  - accountability playbook and a copyable decision record.

C1, C2 and C3 each display the data they would send to C4 (display only).

## Current status and limits

- **Not integrated yet.** C4 runs on simulated trust, risk and compliance values that mirror the other tools' test outputs. Real outputs are connected at integration. C4's accountability part (routing, checks, authority, escalation) works on any list of findings, so it does not depend on C1–C3 being finished.
- **Fictional organisation.** C4's owner register for the simulated bank uses made-up people and a role structure designed for this prototype (iteration 1). The RACI routing and the four checks go to expert review.
- **Simulated evidence.** The credit-scoring system, its evidence and the assessor ratings are simulated for demonstration.
- **Placeholder expert judgements.** The AHP judgements in C1 and C4 are illustrative until the structured expert review is complete. C2's context weights are the proposal's default values until the Delphi review.
- **Iteration-1 formulas.** Where the proposal reports do not fix an exact formula, each tool states the one it uses in its footer. These are refined after expert review.
- **References checked at source level.** Standard references were checked online on 21 October 2026 and eight were corrected (for example SR 11-7 → SR 26-2, current MITRE ATLAS names). ISO/IEC 42001 is cited at Annex A control-area level only, because the full text is paid.
- **Simulated evidence pack.** `evidence-pack/` holds the Simulated Evidence Pack v1.1, generated from the four tools' own data, so the pack and the tools cannot drift apart.

## Validation plan

Case study on the simulated credit-scoring system; structured expert review (AHP with consistency ratio < 0.10, and a two-round Delphi for C2); inter-rater agreement (ICC ≥ 0.75, Cohen's κ ≥ 0.6, C2 κ ≥ 0.70); and sensitivity analysis (weights changed by ±10% and ±20%).
