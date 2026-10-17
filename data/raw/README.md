# Raw-data storage

Do not commit dataset archives, extracted raw CSV/XLSX, model weights or secrets here. This directory documents how reviewers restore exact inputs.

1. Retrieve S1 from the official source register URL and verify ZIP integrity.
2. Preserve archive/member bytes read-only outside Git with a recoverable copy.
3. Record actual SHA-256, bytes, retrieval UTC, resolved URL, storage owner and restore path in data/metadata/source_manifest.json.
4. Retain source notices and capture both conflicting usage statements.
5. Give the reviewer access through the cohort-approved route; document the route without credentials.
6. Validate hashes on every restore; changed bytes require a new freeze.

Scenario mutations belong on derived copies. Never overwrite originals to “fix” -200, dates, delimiters or duplicates. A raw-data README with no accessible retained bytes is not a successful freeze.

If downloads fail, record the error/date and use an approved retained copy. Do not invent a checksum or claim this master includes a downloaded dataset.
