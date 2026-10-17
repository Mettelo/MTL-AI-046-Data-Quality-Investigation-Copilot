# Source and resource register

**Documentation verification date:** 2026-10-17. This register distinguishes verified publisher statements from team acquisition tasks. No archive/model payload was downloaded during creation of this master pack; byte counts, hashes and actual runtime performance remain PENDING until the team records them.

## S1 — UCI Air Quality

| Field | Record |
| --- | --- |
| Provider / creator | UCI Machine Learning Repository / Saverio Vito |
| Landing page | https://archive.ics.uci.edu/dataset/360/air%2Bquality |
| Exact download locator | https://archive.ics.uci.edu/static/public/360/air%2Bquality.zip |
| Persistent citation | Vito, S. (2008). Air Quality [Dataset]. https://doi.org/10.24432/C59K5F |
| Publisher description | 9,358 instances, 15 features; hourly gas sensor/reference concentrations; -200 denotes missing values |
| Expected members | AirQualityUCI.csv and AirQualityUCI.xlsx; inspect actual archive before freeze |
| Core member | CSV; XLSX optional cross-check, never silently mix versions |
| Rights | Page lists CC BY 4.0 and also research-only/non-commercial wording. Preserve both. |
| Approved project use | Educational research simulation; do not assume commercial permission from one statement alone |
| Source limitations | Historical observations, natural missingness/drift, no incident root-cause labels or project lineage |
| Current state | Publisher documentation verified; acquisition, hashes, row profile and team G1 approval PENDING |

The page narrative describes March 2004–February 2005. Actual file dates must be inspected and reported independently; do not trim them merely to match this text.

Attribution must identify creator, dataset/DOI, UCI, listed license, access date, conflicting restriction and transformations. No claim of UCI endorsement. Commercial use requires rights clarification; do not represent that clarification as already obtained.

## R1 — Model resource

Qwen/Qwen2.5-0.5B-Instruct: https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct
Publisher model card declares Apache 2.0. Small local starting candidate, not a promise of meeting quality targets.
Distribution locator: https://ollama.com/library/qwen2.5:0.5b
Team must record actual artifact digest, quantisation, origin/model-card revision, license text and tested configuration. Upstream model-card license and distribution artifact identity are distinct records.

## R2 — Runtime and implementation references

Ollama: https://docs.ollama.com/quickstart and https://docs.ollama.com/api/generate
pandas: https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html
Streamlit: https://docs.streamlit.io/get-started/installation

These are setup/reference resources, not analytical evidence. Installed versions/licenses and local tests must be captured by the team.

## S2 — Authored simulated project metadata

Team creates lineage, runbooks, critical-field policy, scenario recipes and evaluator truth. Assign author/reviewer, version, creation date, hash and “SIMULATED” label. It is prohibited to attribute these to UCI or treat them as a real business deployment.

## Required G1 acquisition fields

source_id/freeze_id; requested/resolved URL; retrieval_utc; archive filename/bytes/sha256; member filename/bytes/sha256; encoding/delimiter/decimal/date/time formats; schema fingerprint; parsed/included/quarantined/excluded row counts; observed date bounds; rights-notice snapshot/hash; citation; raw storage/backup/access/retention owner; analyst; reviewer/date; decision.

Use actual values, never illustrative hashes. A provider URL is a locator, not an immutable snapshot. Restore approved retained bytes if upstream changes or becomes unavailable. If no approved bytes are accessible, block dependent work; no unofficial mirror or substitute data without a new source/rights review.

## Change procedure

New bytes, member structure, model version or rights notice require a new record/version and impact review. State which D/AC/DT and evaluation results must be regenerated. All extra references require official URL/version, rights, purpose, retrieval date and whether they are supplied to inference.
