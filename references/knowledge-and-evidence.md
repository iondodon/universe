# Universe: persistent knowledge, evidence, and change

Read before selecting storage and indexing strategies or implementing investigation results, merge logic, persistence, or project synchronization.

## Separate three things

Design the generated system around three distinct conceptual layers, regardless of chosen technologies:

1. **Target evidence:** accessible files, documents, source symbols, tests, history, traces, and other authorized material; this is the basis for claims.
2. **Persistent project knowledge:** extracted or inferred entities, relationships, explanations, explorations, and evidence links.
3. **Current presentation:** the subset, layout, filtering, highlighting, and focus shown to the user right now.

Knowledge is not a snapshot of rendered nodes. Presentation state can be discarded or collapsed; knowledge remains.

## Model concepts, not just files

Represent meaningful **entities** and **relationships** appropriate to the project. Examples: a capability, package, data structure, endpoint, workflow, responsibility, function, requirement, decision, person/team role (only from authorized information), test, risk, document, or question.

Possible relations include `calls`, `depends-on`, `implements`, `reads`, `writes`, `tests`, `documents`, `belongs-to`, `constrains`, `changed-by`, `impacts`, `conflicts-with`, and `flows-to`. These are examples, **not a closed ontology**. Different explorations may need to introduce new concepts and relation types.

For each meaningful knowledge item, store the equivalent of:

| Field | Intended meaning |
| --- | --- |
| Stable identity | A durable key for matching the item across refreshes and explorations. |
| Kind and label | Human-meaningful concept and type. |
| Summary or attributes | Only as much as is justified by evidence; may evolve. |
| Relationships | Connections to other items, with direction or semantics where needed. |
| Provenance | Which files, symbols, docs, logs, or other evidence support this item. |
| Verification status | Directly observed, mechanically derived, AI-inferred, disputed, or unknown. |
| Scope/version | Where and when the supporting evidence applied. |
| Updated/validated status | Whether evidence is current, stale, deleted, or requires review. |

The generated implementation may use tables, documents, append-only events, a property graph, relational storage, or other persistence. **Do not require a graph database** unless the target project warrants one.

## Provenance and confidence

A factual claim must have accessible, traceable support where feasible:

- **Repository evidence:** project-relative path, optional symbol and line range, and an identifying revision or content hash.
- **Non-code evidence:** document identifier and section/paragraph where supported; timestamps for time-sensitive data.
- **Derived or inferred knowledge:** link to the inputs, derivation method or explanation, and an explicit uncertainty label.

Do not invent a source link, line number, commit ID, or file path. If source locations are missing, mark the claim provisional; if the answer is unsupported, say it is unknown. Separate a user's note or hypothesis from verified project facts.

When citing lines, recognize they can move. Version or hash the referenced content so stale line references are not presented as current. Keep the underlying evidence reference available or expose a clear indication that it can no longer be resolved.

## Merge and correction

Explorations often rediscover the same entity from different directions. Normalize identities and merge duplicates where justified; avoid merging two similar-sounding concepts without evidence. Preserve alternate names and historical context when relevant.

When later findings contradict earlier assertions:

1. Re-evaluate supporting evidence and current project version.
2. Prefer corrected verified observations over stale or unsupported statements.
3. Mark conflicts or uncertainty instead of silently choosing an attractive narrative.
4. Retain useful history or a lightweight audit trail where economical.
5. Update affected summaries and links; do not leave misleading visible relations.

A larger knowledge store should become **more accurate and navigable**, not merely bigger.

## Investigation transaction (semantic contract)

For a user-requested exploration, the system should perform the equivalent of:

1. **Understand intent:** question, selected entity, current lens, and desired depth.
2. **Reuse knowledge:** retrieve relevant existing facts and prior explorations.
3. **Collect evidence:** inspect *only* the authorized, necessary project material.
4. **Reason and classify:** distinguish observed facts, deductions, hypotheses, and unknowns.
5. **Create a bounded update:** new/updated concepts and relationships, provenance, and a human-readable answer.
6. **Validate and merge:** check references where practical, deduplicate, reject unsupported assertions, persist atomically enough to avoid corruption.
7. **Update the focused view:** reveal just enough structure to answer the question. Do not suddenly display all stored entities.

An implementation may use its own data contract or protocol. Preserve **this behavior**, not any prescribed JSON schema.

## Changes in the target project

The world changes after analysis. Track enough source fingerprints (revision IDs, modification times combined with hashes, or equivalent) to detect relevant changes.

- Refresh mechanically derivable facts when files change.
- Mark dependent inferences **stale/pending review** before treating them as current.
- Keep evidence-linked older conclusions discoverable as historical when appropriate.
- Preserve user bookmarks, layout preferences, and unrelated validated knowledge.
- Handle renames, deletions, and new files without duplicating the entire map.
- Provide a manual synchronization action; automated watching is optional and must not consume unbounded resources.

If the project is huge, prioritize targeted indexing and lazy expansion. A complete upfront parse is not required for a good initial overview. Bound time, storage, and model usage; index high-value surfaces first and expand when requested.

## Durability expectations

Data should survive app restart, agent restart, or model/provider changes. A failed analysis should not destroy earlier discoveries. Use safe writes, migrations or backups when schemas change, and a documented recovery route. Store only appropriate local data, not copied credentials or entire secret-containing files.
