# Universe: implementation and lifecycle

Read before writing a generated `.universe/`, choosing a stack, running project analysis, or modifying an existing Universe.

## Contract: generated, project-specific implementation

The Markdown skill remains technology-neutral. The **executing agent** chooses the code, storage, visualization, and runtime based on what works for this project and environment. The result lives in:

```text
<target-project>/
├── ... existing project files ...
└── .universe/
    ├── README.md       # Required: real launch/use/maintenance instructions
    └── ...             # Implementation-defined app, data, configuration, tests
```

Do not require folders such as `app/`, `db/`, `api/`, `viewer/`, or a specific manifest: these may be useful, but the agent must be free to choose a coherent organization. The stable boundary is **`.universe/`**, with a clear way to read, migrate, and reuse persistent discoveries.

The agent may generate source code and non-Markdown files **inside `.universe/`**. Only the distributed *skill* is Markdown-only.

## Initial installation sequence

### Phase A — Inspect

- Locate the intended root and establish whether it is a monorepo, single app, documents-only project, or mixed workspace.
- Respect exclusions (`.gitignore`, build outputs, vendored dependencies, private areas). Seek high-value manifests, entry points, architecture docs, tests, interfaces, and project-specific conventions.
- Determine available local languages, package managers, servers, webview/browser capabilities, and execution constraints. Check whether an existing `.universe/` needs resumption instead.
- Identify the most meaningful initial areas and a small amount of reliable evidence for each. Avoid a complete repository crawl as a blocking prerequisite when targeted scanning suffices.

### Phase B — Decide

Select a simple, maintainable architecture that delivers:

- A launchable interactive graphical interface.
- A persistent evidence-backed project knowledge layer.
- An analyzer/indexer that can seed and deepen knowledge on demand.
- A mechanism to transfer new validated discoveries into that layer.
- An AI-runtime adapter **only if supported**, otherwise an explicit handoff.
- Synchronization and repair that avoid data loss.

Record consequential decisions briefly in `.universe/README.md` or a local design note. Resist unnecessary infrastructure, cloud dependencies, lock-in, and the urge to parse every source symbol upfront.

### Phase C — Generate

Create the smallest **complete** vertical slice:

1. An initial, coherent project map with meaningful project facts.
2. A way to focus and expand an item and return to a compact overview.
3. A detail/explanation surface with navigable provenance where available.
4. Durable knowledge storage and reloading after restart.
5. A question/investigation flow through a real supported agent bridge **or** an obvious manual handoff that can update the persisted knowledge.
6. A project-change refresh process that can invalidate stale evidence.
7. A readable runbook for starting and maintaining it.

Enhancements like rich animations, multiple camera systems, graph analytics, live collaboration, advanced semantic search, and several visual lenses come later when useful. Do not sacrifice the vertical slice for visual spectacle.

### Phase D — Verify and hand over

- Run dependency installation only in approved, appropriately scoped locations; prefer the project's existing toolchain where practical and avoid global installations.
- Actually start/build the generated app or execute a meaningful smoke test. If a browser is available, navigate core paths and inspect errors; if not, run the strongest available CLI/integration checks.
- Exercise persistence and at least one expansion pathway. Verify the AI bridge with an actual request if claimed connected. Never count mocked output as proof of live AI operation.
- Document exact launch and stop commands, ports, optional prerequisites, known limitations, and how to reset or back up knowledge.
- Report honestly what was generated, verified, and blocked.

## Re-execution rules

If `.universe/` already exists:

1. Read its `README.md`, current configuration, storage structure, and existing tests before modifying anything.
2. Distinguish **refreshing knowledge**, **fixing a broken feature**, and **upgrading architecture**. Do the smallest change that meets the request.
3. Preserve evidence, discoveries, user notes, navigation preferences, bookmarks, and prior sessions to the extent stored.
4. Back up or migrate data transactionally before incompatible storage changes; do not silently reset a database or overwrite hand-written notes.
5. Resolve or mark stale evidence after target project modifications. Avoid re-indexing everything if incremental refresh can work.
6. Test the changes and document any migration.

Do not overwrite a functioning `.universe/` simply because a new agent prefers another stack. A different implementation is justified only by a real requirement, a proven limitation, or the user's explicit request.

## Project-relative operating rules

- Do not edit, reformat, or refactor code outside `.universe/` as a side effect of building a visualization.
- Do not add project-root dependencies, config changes, `.gitignore` entries, IDE files, or CI jobs without approval. You can place `.gitignore` *inside* `.universe/` if needed to manage generated caches or secret-free local data.
- Do not recursively analyze `.universe/` as though it were the target project's domain code; otherwise the graph can become self-referential.
- Use portable project-relative paths in stored source references so a cloned project can reopen its Universe when possible.
- Large projects may require index limits or on-demand expansion. Expose coverage rather than pretending the initial index is exhaustive.
- On documents-only projects, model concepts, decisions, evidence, and relations instead of inventing software services or API endpoints.

## Generated `.universe/README.md` checklist

It should contain, at minimum:

- A short description of this particular project's generated Universe.
- Required local prerequisites and **actual** commands for starting, stopping, rebuilding, and testing it.
- Where persistent knowledge and configuration live; backup/recovery and migration guidance.
- How to investigate a question, expand a topic, and access evidence.
- AI mode: supported connection or explicit handoff; login and authorization expectations, without secrets.
- Refresh/sync behavior and how it detects stale evidence.
- What sources have been indexed and what is still outside current coverage.
- Any limitations or features not actually completed.
