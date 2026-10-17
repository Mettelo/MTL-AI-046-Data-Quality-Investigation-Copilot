# Data guidance

## Approved core input

Use UCI Air Quality CSV inside the official archive in [SOURCE_REGISTER.md](SOURCE_REGISTER.md). No account or data purchase is required. Source documentation was checked on 2026-10-17; this master does not claim archive bytes were downloaded or checksummed. Team acquisition/hash verification is mandatory at G1.

The source is historical hourly multisensor/reference-analyser measurements, not incident tickets. Teams author explicitly simulated lineage, DQ policy, runbooks, scenario truth and review records.

## Acquisition and preservation

Download official ZIP unchanged into external read-only storage, record requested and resolved URL/retrieval UTC, compute SHA-256 and extract member metadata without changing bytes. Retain a recoverable copy, source notices and citation. Follow [raw guidance](raw/README.md); do not upload payloads to this master/team Git repository.

Inspect member names instead of assuming a successful HTML download is a ZIP. Verify archive integrity, CSV header/encoding/delimiter, actual records and date bounds. Use explicit parser configuration and record differences between publisher descriptions and observed content.

## Parsing contract

CSV uses semicolon-separated values and decimal commas; inspect actual encoding. Date is DD/MM/YYYY; Time uses HH.MM.SS. Preserve original texts and derive a canonical timestamp with explicit invalid-value quarantine. Do not invent a timezone or convert naive source times to UTC without evidence. UTC acquisition/review timestamps are separate metadata.

Known missing sentinel is -200. Preserve original values, then derive nulls for relevant measurements before statistics/range checks. Missing is not zero. Drop fully blank trailing records/columns only under logged rules; preserve source-row IDs and excluded counts. Do not silently drop rows with missing measurements or impute before evaluating DQ.

UCI lists 9,358 instances; record actual parsed/included/excluded counts and explain differences without forcing the result. Treat the source's drift narrative as context, not labelled incident truth.

## Field dictionary

At minimum map Date, Time, CO(GT), PT08.S1(CO), NMHC(GT), C6H6(GT), PT08.S2(NMHC), NOx(GT), PT08.S3(NOx), NO2(GT), PT08.S4(NO2), PT08.S5(O3), T, RH and AH. Confirm exact spellings from actual bytes.

Dictionary fields: original/curated name, description, unit, source type, parsed type, missing convention, parser transform, valid/project rule, criticality, downstream asset, provenance. Distinguish reference gas concentrations from sensor responses. Preserve units from official documentation; project plausibility rules are not regulatory thresholds.

## Derived and simulated inputs

- curated/ contains reproducible normalized outputs outside Git when large.
- scenarios/ holds versioned recipes and manifests; evaluation truth is kept separate from model inputs.
- reference/ holds notices and authored simulated runbooks/lineage definitions.
- metadata/ holds source/row/schema/model/prompt/evaluation manifests.

Every added source needs purpose, owner, provenance, rights, version/hash, grain and integration/joins. No supplementary dataset is required. Do not join external weather/health data or substitute another UCI dataset silently.

## Data-quality reporting

Show baseline natural issues, injected deltas and all final alerts separately. A negative model result is an evaluation result, not a reason to rewrite the source or relabel truth. Preserve unknowns and blocked calculations. See [scenario specification](../project/SCENARIO_SPECIFICATION.md).
