# Metadata and reproducibility contracts

Create real manifests during team execution; all acquisition fields are currently pending in this master.

Required records:

| File | Minimum contents |
| --- | --- |
| source_manifest.json | S1/freeze; URLs/time; archive/member hashes/bytes; parse policy; rights/citation; storage/restore; actual row/date profile; reviewer |
| field_dictionary.csv | Source/curated fields; types; units; sentinel; transform/rule; criticality; provenance |
| row_ledger.csv | Source member/record ID; included/quarantined/excluded state; reason; derived parent ID |
| lineage.json | Versioned assets/edges/owners; simulated provenance; field-to-output paths |
| run_manifest.json | run_id; source/config/code/rule hashes; scenario-neutral batch ID; timestamps; output hashes |
| model_manifest.json | Runtime/version; model digest/quantisation/license; hardware; prompt/reference hashes; generation limits |
| evaluation_manifest.json | Split/case IDs; nonoverlapping windows; truth access boundary; frozen versions; annotation/reviewer details |

source_row_id is stable before filtering. run_id identifies one execution and must not be reused for changed inputs. Evidence IDs resolve only within their run. Timestamp values retain source timezone uncertainty; acquisition, generation and review timestamps explicitly use UTC.

All generated reports link to these versions. Keep unknown values null with a reason. A template value, guessed hash or claimed PASS without execution invalidates the evidence record.
