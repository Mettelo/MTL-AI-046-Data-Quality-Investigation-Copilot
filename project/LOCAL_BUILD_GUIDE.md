# Local build and zero-cost completion guide

This master supplies the assignment. The team implements the application and the commands specified below in its delivery repository.

## Free reference stack

Python + pandas for parsing; standard-library checks or Pandera for validation; SQLite for review persistence; Streamlit for interface; Ollama for local inference; Qwen2.5 0.5B Instruct as a small initial model. pytest may support meaningful parser/guard/state tests. No vector database, GPU, cloud hosting, Docker or paid API is required.

Official setup references:
- Python: https://www.python.org/downloads/
- pandas CSV parsing: https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html
- Streamlit installation: https://docs.streamlit.io/get-started/installation
- Ollama quickstart: https://docs.ollama.com/quickstart
- Local API generation: https://docs.ollama.com/api/generate
- Structured outputs: https://docs.ollama.com/capabilities/structured-outputs
- Qwen model/license: https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct
- Ollama model distribution: https://ollama.com/library/qwen2.5:0.5b

Record installed versions and model digest. An Ollama tag is a convenience locator, not an immutable model version. Preserve quantisation and origin; verify license for any replacement. Structured output support reduces formatting failures but cannot guarantee grounded claims.

## Week-one feasibility experiment

On available equipment, record OS, CPU, physical RAM, free disk, runtime/model download size and license. Start Ollama, download the small model with:

```text
ollama pull qwen2.5:0.5b
ollama run qwen2.5:0.5b
```

Run five representative bounded evidence prompts, including one unknown-impact case. Save raw output, schema validity, peak memory where measurable and elapsed time. Begin with ≤2,048 input tokens and ≤512 generated tokens; measure rather than promise capacity. Reduce context/examples before increasing model size. If the machine cannot complete the small model, investigate installation/memory issues on existing equipment; record unresolved blockers. A rule-only app cannot claim full AI acceptance.

Downloads require internet once; final operation requires no external service. Normal internet/electricity/existing equipment are assumed, so “£0” means no incremental paid software, hosting, inference or data purchase.

## Team run contract

Provide a dependency lock or exact tested pins, Python version and PowerShell plus POSIX equivalents where relevant. Example PowerShell installation sequence for the implemented team repo:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.lock
```

Do not publish invented version pins. Generate them from the tested team environment.

Implement and document equivalent entry points:

```text
python -m src.acquire --manifest data/metadata/source_manifest.json
python -m src.ingest --config config/project.json
python -m src.scenarios --manifest scenarios/manifest.csv
python -m src.validate --config config/rules.json
python -m src.evaluate --split heldout --config config/evaluation.json
python -m pytest
python -m streamlit run app/main.py --server.address localhost
```

Evaluation truth must never be passed to the copilot function; the evaluator joins it after generation. Separate generation logs from metric aggregation so evaluation can resume without silently regenerating failed cases.

## Runbook and recovery

Document acquisition/restore, hash validation, parser failures, unknown schema, absent lineage, malformed response, model unavailable/timeout, storage permission errors, audit backup and export restoration. Preserve previous runs; each run gets a new ID. Provide a sample incident workflow with expected files, not just screenshots.

Final clean rerun: different member, clean environment, approved source/model bytes, network disconnected after installation, locked configuration. Compare deterministic ledger/check/metric outputs exactly; document any model-output variation and recheck safety/usefulness. Record elapsed time, evidence/output hashes and reviewer signature.

Optional extensions such as embeddings, larger models or advanced charts must not be prerequisites for the core. Public deployment is not required.
