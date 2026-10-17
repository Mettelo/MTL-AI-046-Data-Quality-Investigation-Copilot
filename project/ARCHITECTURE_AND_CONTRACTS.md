# Architecture and contracts

## Processing path

Immutable source → parser/row ledger → curated batch → deterministic checks → evidence bundle + registered lineage/runbooks → bounded retrieval → local model → schema/fact/citation/action guards → human review → versioned exports.

Scenario truth goes only to evaluation. No model tool can modify data, run code, query arbitrary databases or fetch the internet.

## Evidence bundle v1

Required fields:

- schema_version, run_id, batch_id, source_freeze, input_sha256, rule_config_hash, lineage_version.
- validation_results: rule_id, field, status, expected_rule, observed_value, unit, denominator, affected_count, affected_row_ids, evidence_id.
- computed_metrics: metric_id, value, unit, population, evidence_id. Unknown values use null plus reason.
- field_definitions: name, type, unit, missing_convention, source_reference_id.
- dependencies: explicit directed edges, asset IDs, owner and provenance label “simulated”.
- retrieved_references: reference_id, version/hash, exact excerpt, trust label, source and retrieval score/order.
- unknowns: absent metadata/logs/lineage and checks blocked by upstream failures.

Stable evidence IDs are unique within a run. Cross-run IDs must fail validation. Cap example rows and context size while preserving full evidence in local storage. Record truncation; never silently omit critical failures. Retrieval uses a versioned rule→runbook mapping plus keyword matches on approved local references, at most five excerpts and a declared token budget.

## Model output v1

Required top-level fields: run_id, summary, observed_facts, hypotheses, affected_assets, investigation_steps, unknowns, suggested_priority, review_required.

Observed fact item: claim_id, text, evidence_ids, metric_refs. Numeric values must be referenced by metric ID and rendered from trusted metrics; the model must not supply authoritative display numbers.

Hypothesis item: hypothesis_id, possible_cause, supporting_evidence_ids, alternative_explanations, missing_evidence, confidence_label. Confidence labels mean low/medium/high evidence support under a documented rubric, never calibrated probability.

Affected asset item: asset_id, lineage_path_ids, evidence_ids, uncertainty. Only assets reachable in the registered graph may be presented as potentially affected. Unknown lineage produces unknown impact.

Investigation step item: step_id, action_code from an approved read-only catalogue, rationale, evidence_ids, proposed_owner_role. Safe codes include inspect_source_rows, compare_prior_batch, request_ingest_logs, verify_parser_config, confirm_schema_change and request_owner_review. Human ownership is assigned in review.

review_required must be true. suggested_priority is advisory text; displayed operational priority comes from the deterministic policy.

## Guard and rendering rules

1. Parse JSON and validate types, required fields and size.
2. Enforce selected run_id and valid current evidence references; reject cross-run, missing and fabricated IDs.
3. Resolve every metric reference from trusted computation. Reject contradictory quantities; do not trust prose numeric extraction alone.
4. Verify declared impact paths exist and severity is not overridden by the model.
5. Reject action codes outside the allowlist; quarantine free-text instructions suggesting executable fixes.
6. Treat reference excerpts and dataset text as untrusted data. Prompt instructions outrank embedded commands. Test malicious excerpts.
7. Flag semantic claims that cannot be mechanically verified for human review. Automated citation checks cannot establish that a sentence is entailed by a source.
8. Preserve raw output, guard errors and disposition. One corrective retry maximum, with original evidence and guard feedback; timeout default 120 seconds per attempt. Log each attempt.
9. On invalid response/runtime unavailable/context overflow, show a deterministic report labelled FALLBACK — AI DRAFT UNAVAILABLE. No automatic approval.

## Review state and audit contract

Persist in local SQLite or equivalent: incident_id, run_id, revision, raw_response_hash, guarded_draft_hash, editable_report, reviewer_id, decision, reason, action_owner, reviewed_at_utc, parent_revision.

States: generated → awaiting_review → approved or rejected or needs_more_evidence; edits create a new revision awaiting review. Source/run changes invalidate prior approval. Approve requires a named reviewer, reason, review of evidence and an action owner or explicit “no action”. No empty identity, default approval or approval by generation. Clearly label authenticated identity versus self-entered reviewer name; production-grade identity is out of scope.

JSON and Markdown exports include schema/run/source versions, observed facts, hypotheses/unknowns, declared impact, steps, original draft reference, edits, reviewer decision and timestamp. Allow draft export only with prominent UNREVIEWED DRAFT marking. Retain approved exports immutably; later revisions create new files. Rendering escapes untrusted HTML and prevents model text from becoming executable content.
