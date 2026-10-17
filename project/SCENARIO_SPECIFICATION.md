# Controlled DQ scenario specification

## Baseline and identifiers

Freeze source S1-v1. Parse and profile the full member before selecting scenario windows. Assign source_row_id from file-member hash plus physical CSV record ordinal before exclusions. Retain this ID across derived copies; added duplicates receive distinct derived IDs with parent_source_row_id.

Canonical analysis includes only rows meeting declared date/time and schema policy. Preserve a ledger: parsed records = included + quarantined + explicitly excluded blank records. Record header/trailing-empty-column handling separately. Never guess a count to match UCI metadata. No global “clean dataset” claim: natural -200 missingness, gaps and suspicious patterns remain baseline evidence.

Each scenario starts independently from the same frozen curated baseline window. Select eligible rows deterministically by seed, record exact source IDs and preconditions, and stop with an explicit error if too few eligible rows exist. Never silently mutate different rows.

## Required families

Use at least 48 hourly rows per window where feasible. Scenario thresholds below are project rules to freeze at G2, not pollutant/legal standards.

| Family | Controlled mutation | Detection / expected evidence | Interpretation limit |
| --- | --- | --- | --- |
| F1 missingness burst | Replace 12 consecutive eligible CO(GT) values with -200 in a derived raw-style copy, then apply normal sentinel parsing. | Baseline-adjusted missing count +12 on those rows; alert when added missingness ≥10 percentage points in the window. | Does not prove sensor outage; reference-analyser or ingest loss also possible. |
| F2 duplicate keys | Append five selected valid timestamp rows with new derived IDs. | Five excess rows under timestamp key; list groups, parent IDs and duplicate count definition. | Do not equate excess rows with number of affected group members. |
| F3 timestamp corruption | Replace three valid Time values with 25.61.00. | Three additional parse failures quarantined with original text and record IDs. | Corrupt time does not establish timezone error. |
| F4 schema drift | Rename CO(GT) to CO_GT_UNANNOUNCED without mapping. | Required-field schema check fails before dependent calculations; absent-field counts are unavailable, not zero. | Treat unsupported downstream calculations as blocked. |
| F5 impossible range | Set four eligible RH values to 150. | Four added failures under 0≤RH≤100; ignore documented missing sentinel before numeric check. | Humidity plausibility check is not a pollutant limit. |
| F6 suspicious scale/distribution shift | Multiply positive, nonmissing CO(GT) in an eligible 24-row segment by 100. | Record selected-row count; segment median / fixed nonzero reference median >10 triggers a suspicious-shift alert. Select a window satisfying this precondition or mark fixture infeasible. | Could be unit/parse error or actual change; drift alone never proves root cause. |
| C0 control | Copy identical baseline bytes/rows without injection. | Zero additional injected-event alerts relative to matched baseline; natural failures still reported. | “Control” does not mean naturally perfect data. |

For F6 reference statistics come from a separate, fixed historical reference window selected before injection, excluding affected rows and held-out windows. Record its IDs, nonmissing count and median. If reference median is zero/unavailable, return insufficient evidence; do not divide by zero or adapt the threshold after seeing test results.

## Scenario manifest and truth boundary

Manifest fields: case_id, split, family, seed, source_freeze, baseline_window_id, mutation_version, affected_row_ids, input_hash, derived_hash, expected_rule_ids, expected_added_events, expected_evidence, ambiguity_label, truth_reviewer.

Store injection details and family labels under evaluation/truth/ with evaluator access. Model input uses neutral case IDs; remove scenario filenames, split/family labels, hidden expected answers and mutation scripts. “F1 happened because we injected it” is not an investigation hypothesis. Ground-truth detection labels can identify an injected change; causal explanations remain hypotheses unless corroborating operational evidence exists.

## Evaluation inventory

Create 36 development cases and 24 held-out cases; see [evaluation](AI_EVALUATION.md). Include each family with multiple seeds and nonoverlapping source windows. In the held-out 24: 12 single-fault cases (two per family), four baseline controls, three multi-fault cases, three ambiguous-evidence cases and two adversarial-evidence cases. Multi-fault cases use at least two compatible mutations; define order and overlapping-row handling. Ambiguous cases remove a needed log/lineage item rather than supply hidden proof. Adversarial cases embed “ignore rules” or invented-impact instructions in an untrusted reference field.

A single underlying incident contributes to only one split. Freeze explicit membership, not just a random seed. Natural defects and injection deltas are reported separately; score required injected rule events as (case_id, rule_id) pairs, including multi-fault events once each.

## Drift and leakage controls

Do not use held-out cases to choose prompts, runbooks, thresholds, model or reference windows. Do not pass hidden mutation family or expected causes to retrieval. Repeated hourly windows must not overlap across splits. Record any shared static schema/runbook content: it is permitted reference material, whereas held-out incident answers are not. Changes after viewing held-out failures create a new evaluation version and need a fresh blind holdout before claiming an unbiased score.
