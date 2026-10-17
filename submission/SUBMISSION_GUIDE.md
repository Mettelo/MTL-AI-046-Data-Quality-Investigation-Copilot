# MTL-AI-046 — Submission guide

## Release sequence

1. Complete D1–D12 and map agreed user requirements to deliverables, acceptance criteria, tests and evidence.
2. Confirm the approved source manifest, rights/attribution, exact cohort and reviewer restore access.
3. Freeze deterministic DQ rules, controlled scenario recipes, prompts, model/runtime, schemas and dependency lock before final evaluation.
4. Run the deterministic baseline and local-AI workflow. Preserve raw outputs, invalid outputs, rejected claims and measured results.
5. Execute project guardrail/domain tests and **three UAT tasks** with expected/actual results, tester/reviewer, defects and retests. Resolve all critical/high defects.
6. A distinct member performs a clean rerun from the documented source and environment. Record hashes, versions, entry point, elapsed time and discrepancies.
7. Produce a 2-page decision brief, 8–12 slides and a 5–10 minute reproducible demo for the **Data Operations Lead**.
8. Complete `submission/FINAL_SUBMISSION.md`, `CONTRIBUTIONS.md` and the evidence index.
9. Tag the evaluated commit **`v1.0-mettelo-submission`** and verify reviewer access.

## Required walkthrough

Demonstrate one natural/source issue, one injected issue, one ambiguous cause, one unknown downstream dependency and one reviewed incident export.

Show one failure/edge case and explain what the evidence does **not** support.

Preserve the rule that root-cause and impact claims remain hypotheses unless supported by evidence and declared lineage.

## Required evidence bundle

Team repository URL/final SHA/tag; reviewed master commit; traceability index; source manifest; deterministic baseline; local model/runtime/prompt versions; held-out evaluation with denominators; failed/rejected examples; UAT/defect log; clean rerun; technical handover; decision brief/demo; contribution evidence.

Reviewer records **ACCEPTED / REWORK / BLOCKED**, actual reviewer, simulated sponsor role, date, unresolved issues and owners/due dates.

A filled template, screenshot, video or fluent AI output without executed evidence is not acceptance.
