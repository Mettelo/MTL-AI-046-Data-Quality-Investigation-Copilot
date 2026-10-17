# Team repository standard

Create **Mettelo/MTL-AI-046-<team-name>**, subject to cohort repository access arrangements. Do not put team answers in the master. Record master URL https://github.com/Mettelo/MTL-AI-046-Data-Quality-Investigation-Copilot and the reviewed master commit in the team README.

## Required structure

```text
README.md
CONTRIBUTIONS.md
requirements.lock
.gitignore
config/
src/
app/
tests/
prompts/
scenarios/manifest.csv
data/SOURCE_REGISTER.md
data/raw/README.md
data/reference/
data/metadata/
docs/01-discovery/
docs/02-data-governance/
docs/03-data-model/
docs/04-data-quality/
docs/05-metrics/
docs/06-ai/
docs/07-decision-framework/
docs/08-assurance-uat/
docs/09-technical-handover/
evaluation/truth/
evaluation/results.csv
reports/
deliverables/
submission/FINAL_SUBMISSION.md
```

Do not expose evaluation/truth to inference. Public Git repositories do not provide confidentiality between folders: freeze cases before tuning, use neutral incident inputs and have a distinct evaluator keep blind truth in approved local storage until evaluation completes. Record the final truth hash/index and reviewer-access route; publish only after the blind assessment if cohort policy permits.

Keep raw data/model weights outside Git. Use .gitignore for local data payloads, environments, caches, review databases and secrets; commit small authored fixtures and anonymised/simulated evidence intentionally. Explicitly retain approved audit/export evidence through a documented safe snapshot instead of ignoring the only review copy.

## README requirements

State business decision, simulated sponsor, team names/roles, master version, source/rights caveat, frozen cohort, six scenarios, local model and tested hardware, exact setup/run commands, baseline/model metrics and limitations. Include evidence links, workflow screenshots/static export, clean rerun, review controls and cost declaration.

## Collaboration and review

Use individual accounts, meaningful commits, issues and reviewed pull requests where available. Name deliverable owners and distinct reviewers. Contributions must link authored artefacts, one substantive review and demo/handover work per member. Commit counts alone do not prove contribution. Shared accounts and one person's bulk upload cannot substitute for attribution records.

Every R/D/AC/DT/SC entry links to evidence at the final commit, with owner, reviewer, date and state. Preserve failed outputs and repaired versions. Pin tested dependencies and model digest; provide one documented run sequence. Equivalent paths/formats need a complete mapping in the index.

## Release

Tag the final team commit (for example submission-v1), check reviewer access and retain a copy of all external inputs needed to reproduce it. A live local URL or video alone is insufficient: reviewers need source, metadata, runs, results and exports. No paid tool or external deployment can be a prerequisite for assessment.
