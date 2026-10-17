# MTL-AI-046 — Data Quality Investigation Copilot

**Track:** AI Engineering · **Team:** 3–5 people · **Duration:** 8 weeks · **Completion budget:** £0 incremental software/service spend using an existing computer and internet connection.

## The business problem

A data operations team receives failed validation checks but still investigates each alert by hand. Engineers search logs, compare batches, ask which reports depend on a damaged field and write an incident summary. Validation says what failed; it rarely establishes why, what may be affected or what evidence to collect next.

Build a working local AI copilot that turns **verified DQ failures, field definitions, runbooks and declared lineage** into an evidence-linked investigation draft. An analyst must inspect the evidence, edit or reject hypotheses, assign an owner and export a reviewed incident report.

**Simulated organisation:** Mettelo Environmental Data Operations Lab. **Decision owner:** Data Operations Lead. This is an educational research simulation using historical public measurements. It is not an air-quality forecasting, health-advice or regulatory-compliance product.

**Decision to support:** Which failed batch needs investigation first, which declared downstream outputs may be affected, and which safe checks should a human perform next?

## What the team must build

1. Download and freeze UCI Air Quality; preserve originals and profile existing missing values.
2. Create deterministic, labelled failure scenarios on derived copies, preserving a separate clean control.
3. Run executable checks and calculate counts, severity and downstream reach in code.
4. Assemble a bounded evidence bundle with stable evidence IDs.
5. Run an actual open-weight language model locally to propose evidence-linked hypotheses and investigation steps.
6. Validate the response; reject unsupported citations/numbers and route uncertainty or inference failure to manual review.
7. Provide a local interface for inspect → generate → edit/reject → approve → export.
8. Compare the model against a deterministic report baseline on a frozen evaluation set.

A static dashboard, chatbot without validation evidence, template report labelled “AI”, or notebook containing only prompts does not complete this assignment. A deterministic fallback is required for usability but cannot replace demonstrated local model inference.

## Specific business outputs

| Output | Required evidence |
| --- | --- |
| Controlled incident laboratory | Immutable source manifest; baseline profile; at least six failure families plus controls; separate scenario truth. |
| Evidence-backed investigation draft | Observed failures, cited facts, uncertain hypotheses, declared impact, safe next checks and explicit unknowns. |
| Review and incident workflow | Named reviewer, draft revisions, decision/reason, action owner and persisted editable Markdown plus structured JSON export. |
| AI evaluation and release recommendation | Baseline/model comparison, per-case raw outputs, seven measured metrics, failure analysis and retain-baseline/revise/pilot recommendation. |

## Master success contract

| ID | Pass requirement |
| --- | --- |
| SC1 | Reproducible ingestion and six scenario families; 100% of required injected events detected on the held-out suite; clean controls create no injected-event alerts. Existing source issues remain visible separately. |
| SC2 | Real local model execution with pinned model/runtime and raw response evidence; every displayed numeric fact and citation validated against the current bundle. |
| SC3 | Model raw-output grounded factual precision ≥95%, valid evidence references ≥95%, required-field completeness ≥90%; no unsupported critical impact assertion or destructive action in released reports. |
| SC4 | All approved exports preserve reviewer identity, original draft, edits, evidence/run IDs and decision history; no approval can be inferred from generation. |
| SC5 | Ten executed domain tests, three UAT tasks, five metric reconciliations and a distinct-member clean rerun; zero unresolved critical/high defects; no paid dependency. |

Thresholds are assignment targets, not claimed results. A missed AI target requires an honest REWORK or BLOCKED result, not a fabricated pass. Recommendations can favour the baseline, but full copilot acceptance still requires the model and review workflow.

## Start here

Read [business context](project/BUSINESS_CONTEXT.md), [project brief](project/PROJECT_BRIEF.md), [deliverables](project/DELIVERABLES.md) and [acceptance criteria](project/ACCEPTANCE_CRITERIA.md). Follow [data guidance](data/README.md), [source register](data/SOURCE_REGISTER.md), [scenario specification](project/SCENARIO_SPECIFICATION.md) and [AI evaluation](project/AI_EVALUATION.md). Then create your separate team repository using the [repository standard](submission/TEAM_REPOSITORY_STANDARD.md).

This master is the assignment and reference pack. It does not contain a completed application, executed team evaluations or approved submissions. Team implementation belongs in the separate delivery repository.

## Data and practical availability

**Primary source:** [UCI Air Quality](https://archive.ics.uci.edu/dataset/360/air%2Bquality).
**Direct ZIP:** https://archive.ics.uci.edu/static/public/360/air%2Bquality.zip
**Citation:** Vito, S. (2008). Air Quality [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C59K5F

UCI lists 9,358 instances and 15 features. Reconcile actual CSV records rather than assuming the catalogue count equals usable observations. Parse semicolon-separated fields, decimal commas and Date/Time explicitly; preserve -200 as a documented missing-value sentinel before deriving nulls. Never treat it as a measured pollutant concentration or genuine zero.

**Rights caveat:** UCI lists CC BY 4.0 alongside a legacy research-only/non-commercial statement. Use this data for the educational research assignment only; preserve both notices, attribution and changes. Commercial deployment or redistribution beyond that scope requires rights clarification. No dataset payload is bundled in this master.

## Zero-cost implementation path

Use Python, pandas, standard-library validation or Pandera, SQLite, Streamlit and a local Ollama runtime with qwen2.5:0.5b as a small starting model. The upstream Qwen2.5-0.5B-Instruct model card declares Apache 2.0. Model quality is not guaranteed: measure it and revise prompts/context or use another locally runnable openly licensed model with a recorded justification.

No paid APIs, cloud inference, hosted vector database, subscription BI, paid hosting or expiring credits are required. Optional tools cannot be needed for assessment. Install once, download the dataset/model once, then run offline. Use deterministic keyword/runbook retrieval before adding vector search. A CPU is sufficient to attempt the small-model path; record measured RAM, disk, latency and runtime errors on the available machine. Complete the hardware feasibility check in week 1; do not assume a GPU or purchase hardware.

See [local build guide](project/LOCAL_BUILD_GUIDE.md) for commands and an implementation contract. These are team build instructions, not runnable app commands supplied by this master.

## Delivery gates and roles

| Gate | Due | Required review |
| --- | --- | --- |
| G1 scope/source | Week 2 | Eight requirements; source/rights decision; manifest/profile; hardware model smoke test; named owners and distinct reviewers. |
| G2 evidence pipeline | Week 4 | Scenario ledger, checks, contracts, lineage and five verified calculations. |
| G3 AI and review | Week 6 | Frozen prompt/model, blind evaluation, guarded generation and persisted human decisions. |
| G4 handover | Week 8 | D1–D12, AC1–AC12, DT1–DT10, UAT, clean rerun, demo and final evidence index. |

Combine delivery, governance, engineering, AI, interface and assurance roles across 3–5 members; critical work must have a different reviewer. Record real member names separately from simulated sponsor roles.

## Complete project pack

- [Project index](project/README.md), [governance](project/GOVERNANCE.md), [architecture and contracts](project/ARCHITECTURE_AND_CONTRACTS.md)
- [Raw-data guidance](data/raw/README.md), [reference guidance](data/reference/README.md), [metadata guidance](data/metadata/README.md)
- [Submission index](submission/README.md), [submission guide](submission/SUBMISSION_GUIDE.md), [final submission template](submission/FINAL_SUBMISSION_TEMPLATE.md)

All business stakeholders, operational dependencies, incident scenarios and benefit targets are simulated. Do not claim client employment, endorsement, live deployment, real root-cause confirmation or realised savings. Observed data, injected defects, model hypotheses and reviewer decisions must stay distinguishable.
