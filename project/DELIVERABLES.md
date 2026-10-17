# Deliverables — D1–D12

All paths below refer to the team's separate delivery repository. Each deliverable needs named author, different reviewer, immutable evidence link, state and revision date. A document title or screenshot alone is not completion.

| ID | Required output / default path | Minimum content | Accountable responsibility |
| --- | --- | --- | --- |
| D1 | Discovery — docs/01-discovery/requirements.md | R1–R8 plus priorities; as-is/to-be journey; stakeholder map; scope; requirement→D→AC→DT mapping; G1 decision record. | Delivery |
| D2 | Governed source — data/SOURCE_REGISTER.md and data/metadata/source_manifest.json | Exact source/rights notices, citation, requested/resolved URLs, retrieval time, archive/member hashes, storage/restore, parser settings, dictionary and reviewer freeze. | Governance |
| D3 | Reproducible pipeline — src/ingest.py, src/validate.py and docs/03-data-model/model.md | Immutable raw ingestion; canonical timestamp and row IDs; sentinel conversion; row ledger; quarantine; versioned schemas; declared lineage graph and automated checks. | Engineering |
| D4 | Scenario laboratory — scenarios/manifest.csv and docs/04-data-quality/scenarios.md | Six families, control, natural profile; seeds/windows/row IDs; before/after hashes; independent frozen evaluation truth; multi-fault, ambiguity and prompt-injection cases. | Engineering |
| D5 | Metrics and impact — docs/05-metrics/catalogue.md and reports/metrics.csv | K1–K7 definitions/results/denominators; deterministic severity; dependency graph/version; five independent reconciliations; failure-to-output trace. | Engineering / governance |
| D6 | Local AI investigation — src/copilot.py, prompts/ and docs/06-ai/model-card.md | Real local inference, model digest/license/runtime, bounded retrieval, prompt version, response schema, raw outputs, validators, retries/timeouts/fallback; facts versus hypotheses. | AI engineering |
| D7 | Triage and review policy — docs/07-decision-framework/policy.md | Severity/priority, evidence sufficiency, safe investigation catalogue, manual escalation, ownership, unknown impact, draft/rejected/approved states; ten worked case cards. | Delivery / domain |
| D8 | Working interface — app/ and app/README.md | Run/scenario selection; failures/evidence; generated draft; citation drill-down; edit/reject/approve; persisted audit history; JSON and Markdown export; static walkthrough. | Product |
| D9 | Independent evaluation — evaluation/results.csv and docs/08-assurance-uat/ | Frozen case inventory, baseline/model raw outputs, K1–K7, annotation rules and adjudication, DT1–DT10, three UAT tasks, defects/retests and final target decisions. | Assurance |
| D10 | Technical handover — docs/09-technical-handover/runbook.md | Clean setup/run commands, pinned dependencies, model/data restore, measured CPU/RAM/disk/latency, offline operation, backups, troubleshooting and distinct-member rerun. | Engineering |
| D11 | Sponsor recommendation — deliverables/recommendation.md and presentation | Five evidence-backed findings, three owned next steps, deferred/unknown case, baseline/model trade-off, actual target status and prototype/rework/pilot recommendation; 8–12 slides and 5–10-minute demo. | Delivery |
| D12 | Submission and contribution — submission/FINAL_SUBMISSION.md and CONTRIBUTIONS.md | Full evidence index, named contributions/reviews, final commit/tag, master version, source/prompt/model versions, cost declaration, reviewer access and acceptance decision. | All / delivery |

## Seven metric definitions

Use the [evaluation protocol](AI_EVALUATION.md) for exact units and annotation rules.

- K1 injected-event recall: detected required injected events / all required injected events.
- K2 clean-control false alert rate: clean-control cases with any injected-event alert / all clean-control cases.
- K3 raw factual grounded precision: supported factual atomic claims / all factual atomic claims in raw model outputs.
- K4 raw citation validity: valid run-specific evidence references / all evidence references emitted.
- K5 raw required-field completeness: present and semantically usable required fields / applicable required fields.
- K6 human usability: cases rated at least 4/5 for investigation usefulness / all reviewed cases.
- K7 local latency: median and nearest-rank p95 generation wall time, with attempts/timeouts included and completion rate reported.

Do not confuse raw model metrics with guarded-display safety or human-edited results. Evaluate all three stages separately.

## Ten case cards

Choose at least one from every failure family, one clean control, one multi-fault, one ambiguous cause and one malicious-instruction evidence case. Each card contains case/run IDs, observed findings, evidence IDs, deterministic severity/declared impact, model draft, guard result, reviewer edits/decision, safe next action, owner and explicit unresolved questions. Cards must not expose evaluation truth to inference.

## Cross-functional quality

A measurable detector alone is not the copilot. A persuasive report alone is not evidence. D2–D5 establish reproducibility, D6–D8 make a usable AI investigation workflow, and D9–D12 establish whether it is ready for handover. Equivalent file formats are permitted only with an explicit mapping in the final index.
