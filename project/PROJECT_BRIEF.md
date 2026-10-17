# Project brief — MTL-AI-046

## Commission

The simulated Data Operations Lead commissions a local investigation assistant for historical environmental sensor batches. A failed validation should lead to a defensible investigation draft, not an unexplained alert or invented root cause. The analyst decides what to investigate and whether an incident report is suitable for handover.

**Team:** 3–5. **Timebox:** 8 cohort weeks. **Budget:** £0 incremental tools/services using existing equipment. The assignment ends at a local research prototype and reproducible evidence handover.

## Users and workflow

The on-duty analyst opens a batch validation result, checks affected rows and rule evidence, generates an investigation, follows citations into field definitions/runbooks, edits hypotheses, assigns an owner and exports after explicit review. The data engineer reproduces evidence and checks hypotheses. The Data Operations Lead prioritises follow-up. Assurance independently tests unsupported claims and review controls.

As-is: failed check → manual log search → informal hypothesis → manually written report.
To-be: failed check → deterministic evidence bundle → local model draft → automated guard checks → human edit/decision → versioned incident handover.

## Eight mandatory requirements

| ID | User need and observable behaviour | Main deliverable / criterion |
| --- | --- | --- |
| R1 | Engineer restores exact frozen source bytes and reconciles parsing/exclusions; changes never overwrite raw input. | D2–D3 / AC2–AC3 |
| R2 | Analyst sees reproducible natural versus injected failures, counts, fields and rows from six scenario families. | D4 / AC4 |
| R3 | Analyst receives a model-generated draft citing only the selected run's evidence; facts and hypotheses are separate. | D6 / AC6 |
| R4 | Lead sees severity and declared downstream reach computed by code; unregistered dependencies stay unknown. | D5, D7 / AC5, AC7 |
| R5 | Analyst receives safe investigation steps and explicit missing evidence; model failure leaves a usable deterministic report. | D6–D7 / AC6–AC7 |
| R6 | Reviewer edits, rejects or approves a persisted draft; export records original/edits/decision and never executes fixes. | D8 / AC8 |
| R7 | Assurance compares frozen baseline and model on held-out incidents, including ambiguity and adversarial evidence. | D9 / AC9 |
| R8 | Another member reproduces the local workflow and metrics without a paid account or hidden files. | D10–D12 / AC10–AC12 |

At G1 assign priorities, requirement owner, reviewer and specific test links; add justified requirements without deleting this core contract.

## Scope

Include historical data ingestion, baseline profiling, controlled scenario generation, deterministic DQ rules, supplied project lineage/runbooks, bounded retrieval, actual local inference, response validation, human review, incident export, evaluation and handover. Detect structural failures and suspicious changes; do not pretend a drift alert proves instrument failure.

Exclude live sensors, production connectors, autonomous remediation, SQL/shell execution by the model, fine-tuning, enterprise access management, internet agents, public deployment and air-pollution forecasting. The simulated organisation and its dependencies are authored metadata, not facts supplied by UCI.

## Delivery responsibilities

| Responsibility | Required work |
| --- | --- |
| Delivery / business analysis | R1–R8, user workflow, decisions, risks, acceptance mapping |
| Data governance | Rights caveat, attribution, source freeze, dictionary and retention |
| Data engineering / DQ | Reproducible parser, scenario generator, row ledger, executable checks |
| AI engineering | Retrieval, prompt/response contracts, local model, guards, evaluation |
| Product / interface | Evidence drill-down, review states, editable exports and usability |
| Independent assurance | Tests, blind review, defects/retests and clean rerun |

Members may combine roles. A different member reviews critical calculations, model scoring and the final rerun. Sign-offs record the actual reviewer and the simulated role separately.

## Eight-week plan

Week 1: read pack, assign roles, source acquisition and local-model feasibility smoke test.
Week 2 / G1: scope, rights, hardware report, source profile, eight requirements and acceptance plan.
Week 3: curated ingestion, scenario injection and executable checks.
Week 4 / G2: evidence schemas, declared lineage, baseline report and metric reconciliation.
Week 5: bounded retrieval, local generation, response guards and failure handling.
Week 6 / G3: review workflow and frozen held-out AI evaluation.
Week 7: independent tests, UAT, defect repair and repeat only affected evaluation.
Week 8 / G4: independent rerun, final recommendation, demo and tagged submission.

An unsuccessful feasibility check triggers prompt/model/context adjustments on existing hardware and a documented scope review. Do not solve it by requiring paid services. Full acceptance still requires demonstrated inference; if no local route works, record BLOCKED and the precise constraint.
