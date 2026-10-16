---
name: universe
description: Create, launch, explore, update, or repair a project-specific interactive Universe in .universe/ for understanding a repository or project through a progressively expanding graphical representation, persistent knowledge, and AI-assisted questions. Use when asked to initialize a project explorer, visualize a codebase, investigate project architecture or behavior, resume earlier discoveries, or evolve an existing Universe.
metadata:
  version: "1.0.0"
---

# Universe

Build and maintain a **project-specific, interactive environment for understanding a project**. This skill is a **declarative specification**, not a prebuilt application, library, framework, or provider integration. The executing coding agent chooses and implements an appropriate solution inside the target project's `.universe/` directory.

## Defining principle

> **The more a person explores a project, the deeper and more useful its representation becomes—without forcing the person to see all of that complexity at once.**

Apply this principle to both the persistent knowledge and the visible interface:

- **Knowledge grows and improves:** retain useful discoveries, evidence, corrections, relationships, and explanations between sessions. Build on previous work instead of restarting.
- **The view stays comprehensible:** present a small, relevant subset at a time; progressively disclose details when users navigate, expand, or ask questions. Collapsing or changing views never deletes acquired knowledge.
- **Understanding is more important than node count:** deduplicate, correct, summarize, and invalidate knowledge when appropriate.

## Nonnegotiable outcomes

1. **Project-local artifact:** create and maintain `.universe/` in the target project's root. Do not modify application code, configuration, dependencies, or repository-level files outside `.universe/` without explicit authorization.
2. **Working exploration experience:** deliver a launchable graphical application, not merely a diagram, static screenshot, initial scaffold, or descriptive plan. Choose **2D, 3D, or hybrid** based on clarity and constraints; none is universally mandatory.
3. **Arbitrary project questions:** enable investigation beyond a fixed list of diagrams—architecture, features, behavior, data, tests, dependencies, risks, history, and any other subject for which authorized evidence exists. If not enough evidence exists, explain what is unknown.
4. **Question-driven growth:** an exploration request should lead to investigation, a source-grounded explanation, relevant knowledge changes, and a focused visible update **when an operational AI bridge exists**. Never pretend a disconnected UI is performing live AI work.
5. **Persistent, evidence-linked knowledge:** store discoveries independently of the current interface state and the particular AI conversation. Track provenance, uncertainty, and source changes.
6. **Safe, respectful integration:** use the executing AI environment where a supported connection is possible. Do not require a specific model, vendor, SDK, API key, new subscription, or payment by default. Do not bypass authentication, approval, quotas, or licensing restrictions.
7. **Repeatable execution:** if `.universe/` already exists, inspect it and preserve its knowledge, user preferences, and working implementation. Evolve or repair incrementally; never blindly recreate it.
8. **Verifiable delivery:** actually run or build the generated experience and exercise meaningful functionality when the available environment allows. Report working, limited, and unverified capabilities truthfully.

## Choose the requested operation

- **Initialize:** `.universe/` is absent or the user explicitly requests initial creation. Analyze the project, choose an implementation, generate a functioning explorer, seed a high-level knowledge model, verify, and provide launch instructions.
- **Launch:** a Universe already exists. Follow `.universe/README.md` and the generated application's actual startup process. Do not rebuild unnecessarily.
- **Explore:** investigate a subject or question. Reuse existing knowledge, gather fresh evidence as needed, add or refine discoveries, and show the most useful focused view. If the running application cannot talk to the agent, use the supported documented handoff instead of claiming an automatic update.
- **Synchronize:** detect changes in the target project, refresh affected facts, mark stale inferences, and preserve still-valid discoveries and preferences.
- **Evolve/repair:** improve or fix the generated implementation without losing knowledge; migrate data safely if the storage model changes.

When the user's request is broad (for example, “Use Universe here”), default to **initialize if missing; otherwise launch and synchronize as needed**. Do useful work immediately; ask a question only when an essential decision cannot safely be inferred.

## Execution workflow

### 1. Identify context and boundaries

- Determine the intended target project root (usually the current repository root; respect an explicitly selected workspace or subproject). A project need not be a conventional code repository.
- Inspect its visible structure, documentation, build tooling, and environment. Respect ignore rules and denylisted content. Avoid reading credentials, sensitive personal data, and unrelated directories.
- Check for an existing `.universe/`; establish whether you are creating, resuming, or migrating.
- Read [vision and user experience](references/vision-and-experience.md) and [scope and safety](references/scope-and-safety.md).

### 2. Design the project-specific Universe

- Determine what meaningful high-level concepts and relations the project supports. Choose an implementation stack based on the existing environment, expected scale, available graphical capabilities, and maintenance simplicity—not personal preference for a framework.
- Design a durable **knowledge layer separate from the current view** and an exploration mechanism that can extend or revise that layer.
- Select an appropriate 2D, 3D, or mixed visual treatment. Avoid rendering the entire accumulated graph by default.
- Read [knowledge and evidence](references/knowledge-and-evidence.md), [exploration interface](references/exploration-interface.md), and [implementation and lifecycle](references/implementation-and-lifecycle.md).

### 3. Determine AI connectivity honestly

- Detect which AI features are available in the current executing environment and whether it exposes a **documented, authorized interface** usable by the generated application at runtime.
- Prefer reusing that environment. Do not assume that the skill itself or the current chat creates a persistent bridge to a browser UI.
- When supported, build a real request-to-analysis-to-update path; otherwise provide a clearly labeled disconnected/manual-handoff mode while keeping browsing and previously acquired knowledge useful.
- Read [AI connectivity](references/ai-connectivity.md) **before claiming or implementing live AI interaction**.

### 4. Implement, seed, and validate

- Create application code, indexing/analysis code, local persistence, configuration, and launch documentation **under `.universe/`**. Choose internal files and schema to fit the project; they are not prescribed by this skill.
- Construct an honest, useful **initial overview** using available project evidence, with drill-down and provenance. Do not pre-expand all files, symbols, or topics.
- Implement progressive disclosure, navigation, questioning or explicit handoff, durable storage, refresh behavior, and graceful errors. Make the interface responsive and usable without an expensive GPU when reasonably possible.
- Run the application or a smoke test; verify persistence after restart and at least one deeper exploration route. Read [verification](references/verification.md) and use its acceptance scenarios.

### 5. Deliver and maintain

- Write `.universe/README.md` explaining the actual commands to install, start, stop, explore, update, and recover the generated application; its AI mode; its data locations; its limitations; and how to repeat the skill safely.
- Report the exact generated path, launch instructions, what was actually tested, and any limitations. Never label a proposed feature as implemented.
- On later invocations preserve validated knowledge, handle stale evidence, and avoid destructive changes.

## Implementation freedom vs. required behavior

**You choose:** language, framework, database, graph model implementation, 2D/3D/hybrid rendering, layout algorithms, server model, deployment style, and UI details. Different projects may yield different implementations.

**You must preserve:** gradual exploration, persistent accumulating understanding, focused views, arbitrary evidence-grounded questions or a transparent handoff, truthful AI status, project isolation, and safe resumption.

Do not respond with just a technology recommendation, wireframe, or specification when the user requested initialization. **Build the project-specific implementation that the environment permits.** When a capability is blocked, produce the maximum useful working subset and clearly identify the blocker.
