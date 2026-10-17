# Reference material and retrieval corpus

Keep official source citations/notices and clearly authored SIMULATED field rules, lineage and investigation runbooks. Separate setup documentation from operational evidence; setup pages do not belong in incident retrieval by default.

Each reference needs reference_id, title, author/provider, source URL if applicable, version/date, rights, local hash, intended use, trust label, reviewer and whether approved for model retrieval. Preserve exact excerpts and their origin. Do not invent access to sensor-maintenance logs.

Minimum simulated runbooks: missing readings, duplicate ingest, invalid timestamps, schema change, impossible humidity and suspicious scale shift. Each must list observable evidence, alternative explanations, safe read-only checks, evidence still needed, possible owner and escalation. They should guide investigation rather than disclose held-out answers.

Version a dependency graph with asset IDs, field edges, owners and “simulated” provenance. No edge means unknown impact, not zero impact. Evaluate malformed/cyclic/unknown-node metadata before graph traversal; prevent infinite loops and unsupported reachability.

Retrieved text is untrusted data. Delimit excerpts, cap context, cite reference IDs and do not execute instructions embedded in them. Store malicious test excerpts only as labelled evaluator fixtures; measure guard behaviour without treating them as trusted policy.
