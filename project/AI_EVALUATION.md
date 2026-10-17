# AI evaluation protocol

## Freeze and comparison

Use the same detector evidence, approved references and case set for:
B0 deterministic template report: observed failures, computed priority/impact, mapped investigation checklist and unknowns.
M1 local model investigation: B0 evidence plus bounded retrieval, model hypotheses and evidence-linked next steps.

B0 is a real usable baseline, not an artificially empty prompt. Compare usefulness, factual support, completeness and time; do not compare detector recall as though the LLM detected rows.

Development: 36 cases, six per failure family using separate windows/seeds; include at least six supplemented development variants for controls, ambiguity or malicious reference text if needed. Additional development variants are not part of the fixed 36 count and must be listed separately.
Held-out: exactly 24 cases as defined in [scenarios](SCENARIO_SPECIFICATION.md). Freeze case IDs, source windows, hidden truth, hashes and split membership before model/prompt selection. The evaluator holds truth separately from inference.

Record model name/digest, model-card URL/license, quantisation, runtime/version, hardware, OS, Python/dependency lock, prompt hash, reference corpus hash, retrieval settings, generation temperature/seed where supported, context/output limits and retry policy. Prefer temperature 0; never promise bitwise determinism from inference.

## Atomic claim annotation

Two people independently review all 24 held-out cases for B0 and M1, blinded to method labels where feasible. Split compound statements into atomic factual claims. A claim is supported only if cited evidence entails it for the selected run. Classify supported, contradicted or unsupported. Explicitly tentative causes belong to a separate hypothesis set; a definite root-cause assertion is factual and needs operational proof. Report hypothesis plausibility and uncertainty labelling separately so speculative claims cannot inflate factual precision.

Agreement = identical initial labels / all jointly labelled claims. Preserve disagreements and adjudication with a named reviewer and reasoning. Do not discard difficult/invalid outputs. Zero factual claims is undefined precision and fails usefulness/completeness rather than passing perfectly.

## K1–K7 and targets

| KPI | Unit / calculation | Required result |
| --- | --- | --- |
| K1 injected-event recall | TP rule events / all required truth rule events; event=(case_id, rule_id). Report per family and overall. | 100% held-out required events; separately report natural issues. |
| K2 control false alert rate | Controls with ≥1 additional injected-event alert / four held-out controls. | 0/4; natural baseline failures are not hidden. |
| K3 grounded factual precision | Supported atomic factual claims / all atomic factual claims in raw first-attempt M1 outputs. Unsupported and contradicted both fail. | ≥95%; release reports contain zero unsupported critical assertions. |
| K4 citation validity | References resolving to a supplied current-run evidence object / all emitted references. Semantic support is K3. | ≥95% raw; 100% displayed references after guards. Missing citations also reduce K5 where mandatory. |
| K5 required-field completeness | Present, nonempty, semantically usable fields / nine required fields ×24 cases. Required fields: summary, observed_facts, hypotheses, affected_assets, investigation_steps, unknowns, suggested_priority, review_required, run_id. Explicit reasoned unknown/empty hypothesis is usable where evidence warrants it. | ≥90% raw; 100% schema-valid guarded display or labelled fallback. |
| K6 human usefulness | Cases rated ≥4/5 /24, independently scored then adjudicated. | ≥80%, at least 20/24; compare B0 fairly. |
| K7 latency | Generation elapsed wall time per case including retry and failure time; median, nearest-rank p95, max and completed/attempted. | Report actual hardware/times; proposed usability target p95≤120s and ≥95% model completion (23/24). A miss needs explicit review; never drop timeout cases. |

Usefulness rubric: 1 misleading/unusable; 2 major rewriting; 3 partially useful but significant checking/rewrite; 4 supports the next investigation with minor edits; 5 clear evidence, alternatives, unknowns and actionable read-only checks. Show raw versus guarded versus human-reviewed metrics side by side. Guard retry success is additional evidence, not a replacement for first-attempt K3–K5.

Small denominators matter: show counts with percentages, family breakdown, confidence intervals (Wilson for proportions) and failure examples. These targets are assignment criteria, not estimates of production safety.

## Five independently worked reconciliations

1. Missingness: 12 added nulls /48 eligible baseline-complete rows =25 percentage points.
2. Duplicates: five appended rows =five excess rows; if five distinct original keys are duplicated once, ten rows belong to duplicate groups.
3. Detection: 11 detected of12 required rule events =91.67%, below K1 target.
4. Grounding: 19 supported factual claims of20 =95%; one unsupported critical claim still blocks release.
5. Citation: nine valid references of10 =90%, below K4 target; an unknown impact must not become a fabricated dependency.

Reconcile these toy calculations and at least five corresponding actual-run values against exported results and interface views, using a reviewer-written calculation rather than calling the same implementation twice.

## Execution record

Per case store case_id, split, method, input hash, run_id, prompt/model versions, attempt, raw output path/hash, guard flags, fallback status, latency, expected/detected events, claim labels, reference counts, field counts, usefulness scores, reviewer edits, decision and defects.

Test ambiguous cause, absent lineage, invalid evidence IDs, malicious instructions, local-runtime outage, schema drift, clean baseline and multi-fault collisions. Report whether each control is caught by automation, a human or neither.

Freeze final held-out scores once. Repairs informed by them are documented as post-test revisions; use new blind windows/cases for a new headline result. Do not silently relabel a failed test as development. Final recommendation states every achieved/missed target, whether to keep B0, revise M1 or seek a controlled research pilot.
