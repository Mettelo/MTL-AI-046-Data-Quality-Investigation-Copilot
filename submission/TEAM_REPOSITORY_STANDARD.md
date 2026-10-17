# MTL-AI-046 — Team repository standard

Create **MTL-AI-046-<team-name>** under the **Mettelo GitHub organisation** and add each member using their individual GitHub account.

Record the master repository URL, reviewed master specification commit SHA, team members/responsibilities, final team commit/tag, approved source version and exact run instructions.

## Required repository structure

```text
README.md
CONTRIBUTIONS.md
.gitignore
requirements.txt or equivalent lock
config/
src/
app/
tests/
prompts/
evaluation/
outputs/
data/
  SOURCE_REGISTER.md
  raw/
    README.md
  reference/
  metadata/
  curated/
docs/
  01-discovery/
  02-data-governance/
  03-data-model/
  04-data-quality/
  05-evidence/
  06-ai/
  07-decision-framework/
  08-assurance-uat/
  09-technical-handover/
deliverables/
submission/
  FINAL_SUBMISSION.md
```

Equivalent tool-specific folders are allowed only with an explicit mapping in the README.

## Data handling

Use the approved UCI Air Quality source described in the master data pack. The team may obtain the approved raw file from the master `data/raw/` or reacquire it from the documented official source, but must create its own source manifest recording filename, source/version, retrieval/copy date, bytes/hash, licence/terms, parser assumptions and reviewer.

Do not treat the presence of the raw ZIP in the master as proof of successful ingestion or validation. Large raw payloads and model weights should remain outside the team Git repository unless cohort guidance says otherwise.

## README and contribution evidence

State the commissioned decision:

> Prioritise a failed data-quality incident, explain the evidence-supported investigation path and produce a human-reviewed incident handover.

Name **Data Operations Lead** as the simulated sponsor.

Preserve this limitation:

> Validation failures show what failed; model-generated root causes remain hypotheses unless supported by evidence. Only declared lineage can support downstream-impact statements.

Every member links substantive artefacts they authored, at least one meaningful peer review, and contribution to UAT, demo or handover. Commit count alone is not Proof.

## Required project-specific artefacts

- **D5 Data-quality evidence and impact ledger:** `data/curated/dq-evidence-impact-ledger.csv` and `docs/05-evidence/dq-evidence-impact-ledger.md`.
- **D6 AI investigation evaluation:** `docs/06-ai/investigation-evaluation.md` plus `evaluation/results.csv`.
- **D7 Investigation decision framework:** `docs/07-decision-framework/investigation-policy.md` plus `case-register.csv`.
- **D8 Working copilot/review workflow:** `app/README.md` plus reproducible examples in `outputs/examples/`.
- **D11 Incident operating and recommendation pack:** `deliverables/incident-operating-pack.pdf` plus editable slides.

Maintain a D1–D12 / acceptance / test / UAT evidence index with owner, distinct reviewer, state and final-commit path.

Recommended team size: **3–5 people**.
