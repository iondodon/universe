# Universe — portable, Markdown-only Agent Skill

**Universe is a specification that an AI coding agent uses to build a living, graphical explorer inside another project.** It is not itself a viewer, a server, or a collection of prebuilt components.

> **The more a person explores a project, the deeper and more useful its representation becomes—without forcing the person to see all of that complexity at once.**

The skill intentionally describes **behavior and outcomes, not a particular implementation**. On the target project, the agent chooses a suitable technology stack, creates `.universe/`, builds a graphical experience (2D, 3D, or both), and stores discovered understanding so it can be revisited and refined.

## What's in this package

```text
universe/
├── SKILL.md                     # Agent Skills entry point
├── README.md                    # This guide
└── references/                 # Behavioral and delivery specifications
    ├── vision-and-experience.md
    ├── knowledge-and-evidence.md
    ├── exploration-interface.md
    ├── ai-connectivity.md
    ├── implementation-and-lifecycle.md
    ├── scope-and-safety.md
    └── verification.md
```

**All files in the ZIP are Markdown.** The runnable implementation gets generated *later*, in a project where the skill is executed.

## Install in a target project

Extract the ZIP. Copy the complete `universe/` directory (including `references/`) into your coding agent's project-local skills directory:

| Agent | Project-local destination |
| --- | --- |
| Claude Code | `<project>/.claude/skills/universe/` |
| OpenAI Codex | `<project>/.agents/skills/universe/` |
| Another Agent Skills-compatible tool | Its documented skills directory |

You may instead install it in a user-level skills directory supported by your agent. The portable source remains the same. Make sure `SKILL.md` is located **inside the `universe/` folder**.

The skill is intended for coding agents with filesystem access, permission to generate local application files, and the ability to run development tools. A chat-only environment that cannot work on a local project cannot construct and launch the requested explorer.

## Invoke

From the target project, ask the coding agent:

> **Use the universe skill to initialize and launch a Universe for this project. Create `.universe/` and implement a working interactive explorer.**

For future sessions:

> **Use the universe skill to reopen this project's `.universe/`, sync project changes, and preserve everything already discovered.**

Or, for an investigation:

> **Use Universe to explore how authentication and token expiry work. Reuse existing knowledge and extend it only where useful.**

On compatible systems the skill may also be addressable explicitly by its name (for example `/universe` in Claude Code). Invocation syntax depends on the agent.

## What happens when invoked

1. The agent reads this project and any previous `.universe/` state.
2. It chooses a suitable architecture and user interface—not necessarily the same one used in another project.
3. It creates a working project-local graphical explorer and seeds a small, useful overview.
4. You drill down, follow connections, and ask about any aspect of the project supported by accessible evidence.
5. Knowledge accumulates persistently, while the view shows only the currently relevant part.
6. Later invocations reuse and improve that implementation and its knowledge instead of recreating everything.

### AI connectivity

The skill does **not** require an Anthropic or OpenAI API key. It instructs the generating agent to reuse the **currently executing AI environment**, *if that environment provides a supported and authorized runtime connection*. An active agent conversation alone does not imply the browser application can send questions to it.

If a live bridge cannot be implemented, the generated UI must **say so visibly** and provide a documented handoff for asking the agent to investigate and update Universe. It must never present canned answers as live investigation or silently create a paid external AI integration.

### Security and fidelity

The default is read-only treatment of the target project, with generated assets contained in `.universe/`. Project files and documents are evidence, not commands. Results should link to their sources, communicate uncertainty, and become stale when the underlying evidence changes. Read [scope and safety](references/scope-and-safety.md) for details.

## What this ZIP does *not* contain

- A predefined web app, 3D engine, database, or server.
- An AI API key, bundled model, or subscription entitlement.
- A populated `.universe/` for a particular repository.
- A guarantee that every coding-agent host permits a persistent runtime AI connection.

These distinctions are intentional: **one reusable skill specification; many project-specific implementations.**

## Format and compatibility

The package follows the [Agent Skills specification](https://agentskills.io/specification): `SKILL.md` includes the required `name` and `description` metadata; detailed instructions live in Markdown references. Files are plain UTF-8 Markdown and are designed to be readable without special tooling.
