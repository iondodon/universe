# Universe: vision and user experience

Read this when designing the initial experience, deciding what to visualize, or interpreting a request that is not about source-code structure alone.

## Purpose

Universe is an interactive way to **discover, understand, and revisit** a project. The explorer starts with an appropriately small overview and grows through user-driven investigation. It should help users learn *what exists*, *why it exists*, *how it works*, *what depends on it*, and *what is known or uncertain*.

The word **project** is intentionally broad: a software repository, monorepo, document-heavy project, architecture proposal, infrastructure repository, or another collection of accessible project evidence. Model the actual project rather than forcing all projects into a code-only hierarchy.

## The governing principle

> The more a person explores a project, the deeper and more useful its representation becomes—without forcing the person to see all of that complexity at once.

This is a two-system requirement:

1. **Persistent understanding** grows in the background as evidence-backed discoveries are made, refined, and corrected.
2. **The visible presentation** is a focused projection of that understanding. Its complexity is controlled by the user's current question, selection, zoom level, and chosen perspective.

**Do not equate knowledge volume with visible node count.** Collapsing, filtering, or switching views hides information; it must not erase it.

## The conceptual user journey

### Orientation

On first launch, the user should understand what project is being represented and see a useful high-level structure. Seed a small number of meaningful areas or capabilities, rather than indexing everything into an unreadable cloud.

Examples of initial anchors include major packages, business capabilities, application boundaries, data stores, interfaces, external dependencies, primary workflows, or sections of a documentation-centric project. Show only the anchors actually supported by source evidence.

### Focus and expansion

A user selects a topic such as “Authentication,” sees an understandable summary, and expands to surrounding services, call paths, tests, policies, or data contracts. A user can travel between levels of abstraction, revisit earlier areas, and return to the overview without losing previously explored details.

### Question-led investigation

A user asks, “What happens when a token expires?” or “Where could a schema migration break clients?” Universe reuses earlier discoveries, fetches fresh evidence where needed, explains the answer with traceable sources, and reveals the resulting relationships and relevant pathways. A question can create a **new lens** or annotate an existing view; it need not merely add more nodes.

### Return and recall

After reopening the application, prior knowledge is still available. The user can find earlier explored subjects, see where a claim came from, and detect if recent project changes may have invalidated it. A small overview can still be shown even if the stored model has become deep.

## Exploration can span multiple perspectives

Do not hard-code a closed list of possible subjects. Useful **examples** include:

- **Structure:** packages, services, files, modules, deployments, configurations.
- **Behavior:** request life cycles, state transitions, errors, background jobs, runtime paths.
- **Data:** entities, storage, ownership, transformations, APIs, contracts, migrations.
- **Product:** features, goals, requirements, workflows, ownership and documentation.
- **Quality:** tests, coverage evidence, code coupling, hotspots, reliability signals.
- **Change:** Git history, decisions recorded in docs, deprecations, recent changes.
- **Risk and hypotheses:** suspected impacts and assumptions, visibly distinguished from facts.

Source code alone may not prove *why* an architecture decision was made or *what happened* in a live production environment. Preserve uncertainty, request additional authorized evidence when useful, and do not manufacture explanations.

## 2D, 3D, and hybrid are peers

The requirement is **interactive, spatially or graphically meaningful exploration**, not a dimensionality target.

- **2D** may be better for directed dependencies, sequence flows, or accessibility and performance.
- **3D** may be useful when different abstraction layers, spatial clusters, or larger contextual structures benefit from depth.
- **Hybrid** may use a network or map plus more legible tables, timelines, execution traces, and detail panels.

The agent should choose based on legibility, meaningful navigation, technology constraints, and user value. A clean 2D explorer is better than an impressive but confusing 3D cloud. Switching modes is a welcome enhancement but never a prerequisite.

## What the first screen should accomplish

An effective overview answers most of these without a tutorial:

- What project am I looking at, and when was it last analyzed?
- What are the principal areas and how are they connected?
- How do I focus, expand, collapse, and return to the top level?
- How do I ask a new question or trigger an investigation?
- How do I inspect the evidence for a displayed claim or relationship?
- Is AI-assisted investigation currently connected, disconnected, or unavailable?

Use a default layout and interaction vocabulary that can be learned quickly. Preserve keyboard-accessible routes to core operations where feasible; do not hide essential information behind hover-only gestures.

## Anti-patterns

- An enormous force-directed hairball loaded on the first visit.
- A static graph with cosmetic zoom controls but no further discovery.
- A chat that answers questions without recording and reconnecting what was learned.
- A graph that adds AI-created nodes without provenance, correction, or de-duplication.
- An interface that forgets everything when the user's conversation or server ends.
- Conflating inference with facts or treating unavailable information as certain.
- Forced 3D rendering when a simple 2D view communicates the subject better.
