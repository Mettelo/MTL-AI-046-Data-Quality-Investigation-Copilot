# Business context and sponsor commission

## Simulated operating environment

Mettelo Environmental Data Operations Lab maintains hourly sensor tables used in a daily analyst summary and a weekly research report. These downstream assets and staff roles are fictional project metadata. UCI supplies historical measurements; it supplies neither our organisation, incident labels nor our lineage.

A batch may have missing sensor readings, malformed dates, duplicated timestamps or a suddenly changed measurement scale. The current alert tells the analyst that a rule failed. It does not explain whether this resembles an ingest defect, a missing-data convention or a real environmental change.

## Decision and value

The Data Operations Lead must choose investigation priority and an accountable owner. The product should reduce evidence-search effort while making uncertainty visible. Proposed benefits are quicker triage, more complete incident reports and fewer unsupported impact statements. They are hypotheses until measured.

Measure report preparation time with at least three paired tasks under comparable conditions. Record participant, case order, prior exposure, hardware and start/stop rule. Report individual times and median; do not claim causal productivity gains from a small classroom study. Any monetary saving is unmeasured unless supported by an explicitly labelled assumption and calculation.

## Stakeholders and competing needs

| Stakeholder | Need | Risk / resolution |
| --- | --- | --- |
| Analyst | Fast readable guidance | Concision must not hide evidence or unknowns. |
| Data engineer | Reproducible failures | Every count and example links to a rule result and source-row ID. |
| Research report owner | Understand affected outputs | Use registered dependency paths; absence of lineage means unknown impact. |
| Data Operations Lead | Prioritise effort | Severity is a documented deterministic policy, not model intuition. |
| Governance reviewer | Attribution and usage limits | Retain conflicting source notices; educational research scope only. |
| Assurance reviewer | Recheck claims | Preserve raw generations, guard outcomes and manual annotations. |

## Operational policy assumptions

P1 critical: parse/schema failure prevents reliable ingestion, or a required key fails.
P2 high: an accepted rule breaches its documented threshold on a critical field feeding a registered output.
P3 medium: noncritical field or exploratory distribution alert needing further evidence.
P4 informational: known baseline missingness within the approved profile.

At G1 specify actual field criticality, numeric thresholds and batch boundaries. At G2 freeze the rules before evaluation. These are simulation policies, not environmental standards.

Declared example dependencies: curated_hourly.CO(GT) → daily_co_summary → weekly_research_report; curated_hourly.T/RH → sensor_context_summary → weekly_research_report. Model any additional edges explicitly. A failed CO measurement can affect a summary; it does not prove the report has been published or that the population is unsafe.

## Example analyst journey

The rule engine finds duplicate timestamp keys in a derived batch. The analyst sees affected-row IDs, duplicate groups and the selected policy. The copilot proposes replay/re-ingestion as one possible cause and asks for ingest logs, citing the runbook. The reviewer notes that no logs are present, keeps the cause unconfirmed, assigns an engineer and exports a reviewed investigation. No source records are deleted.

## Boundaries of evidence

Observed: field value, timestamp parse outcome, computed count, registered edge.
Injected: deliberate transformation recorded only in the evaluator's truth.
Hypothesis: a possible mechanism consistent with available evidence.
Decision: a human-authorised follow-up with owner/reason.

Never turn the known injection into proof of a real operational root cause, or supply hidden scenario labels to the model. The product is successful when reviewers can explain both what the evidence supports and what remains unresolved.
