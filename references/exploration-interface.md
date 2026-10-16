# Universe: interactive exploration experience

Read before choosing the renderer, designing interaction flows, or building the investigation UI.

## Core UI capabilities

The generated application must make the project **explorable**, not simply display an illustration. Users should be able to:

1. **Orient** at a high level with meaningful project areas and relationships.
2. **Focus** on an area or item and see its role, explanation, connections, and source evidence.
3. **Expand** a subject into deeper concepts, examples, behavior, data flows, or implementation details when needed.
4. **Collapse or zoom out** without losing accumulated knowledge.
5. **Follow connections** between topics and jump across abstraction levels.
6. **Search or navigate** to previously discovered subjects and earlier explorations.
7. **Ask an arbitrary project-related question**, or use an explicit handoff if no connected runtime agent exists.
8. **Understand status**: which details were directly verified, inferred, stale, unknown, or generated in response to a question.

An index, breadcrumb trail, mini-map, history, search, or similar orientation aids are implementation options. Ensure there is *some* reliable way to return to earlier contexts and recover from getting lost.

## Question-driven adaptation

A question should influence what the user sees. It may:

- Highlight a causal or dependency path.
- Expand a cluster while leaving unrelated parts collapsed.
- Switch to a more suitable lens, such as an execution flow or timeline.
- Introduce new concepts and evidence-backed relationships.
- Attach an explanation and traceable sources to existing structures.
- Mark an open question, ambiguity, conflict, or missing evidence.

Not every answer needs to add nodes. Sometimes the right result is a clearer summary, an identified unknown, or a correction to earlier information.

## Progressive disclosure mechanics

Use visible complexity budgets, whatever their implementation:

- Begin with **conceptual anchors**, not every source file or symbol.
- Keep the selected subject and its relevant neighbors in focus; hide or summarize distant relationships.
- Expand information in response to deliberate navigation, investigation, or zoom/context changes.
- Group dense regions by meaningful project concepts and support drill-down.
- Preserve view context when new data arrives; avoid uncontrolled layout jumps.
- Support stable focus, restoring location after expanding or collapsing.

Do not silently replace the user's current view when an unrelated background update occurs. Signal updates and let the user decide whether to follow them.

## 2D, 3D, and alternative presentations

Choose dimensionality based on readability and navigation. A 2D graph, a navigable layered canvas, a 3D spatial map, or a mixture of graph and focused diagrams can all satisfy the skill.

Use styles and spatial encoding meaningfully. Avoid decorative dimensions, rainbow colors without a legend, fine text that requires excessive zoom, and camera controls that overwhelm the subject.

Where practical, support keyboard navigation or a text/list alternative for critical project information. Maintain readable contrast, responsive layout, and interaction cues; the user should not need a powerful GPU just to ask a question.

## Evidence and explanation panel

Selecting a concept or relationship should make it possible to inspect:

- What it means, written in language appropriate to the user’s selected level of detail.
- Its nearest important connections and why they exist.
- The evidence and project locations supporting meaningful claims.
- Whether the information is verified, inferred, or stale.
- Suggested directions for further investigation, not a forced sequence.

Source links should open relevant files, paths, or read-only excerpts only when safe and supported. Show a fallback for evidence that cannot be navigated directly.

## AI connection status and error behavior

Make the status legible: for example **Connected**, **Manual handoff**, **Offline**, or **Unavailable**. A disconnected UI must not display synthetic typing indicators, made-up streaming tokens, or simulated answers as if a model were working.

For real connected analysis, show progress appropriate to the available interface, support error recovery, and distinguish an analysis failure from an empty result. A cancellation should not corrupt the knowledge store.

## Example acceptance journeys

### Journey A — Architecture orientation

Open the app -> see a few major subsystems -> select one -> read its evidence-backed purpose -> drill to a module -> return to the overview. The overview remains clear.

### Journey B — Trace behavior

Ask “What happens after a request fails authentication?” -> investigate sources -> explain the steps with citations -> highlight a path/sequence -> reveal adjacent dependencies on demand -> save the discovery. If no AI bridge exists, the user sees an explicit handoff rather than an invented answer.

### Journey C — Revisit

Close and reopen -> search for “authentication” -> restore the discovered summary and relationships -> identify stale parts after a source change -> refresh only the affected concepts.

### Journey D — New kind of subject

Ask “Which decisions in our docs explain the caching strategy?” -> locate relevant records -> connect the decision to components when evidence exists -> keep unsupported motives clearly unknown.
