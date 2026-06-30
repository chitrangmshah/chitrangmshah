---
uuid: 019f189a-fccc-76e4-9851-aec06f3df7ba
---
# CONCEPT.md — what this system is

> [!NOTE]
> This document is the **authoritative scope** of this system — the single place that explains the whole idea and the reasoning behind it. If an agent's memory or prior conversation context is lost, read this file together with `AGENTS.md` to reconstruct what this repository is and how it works. It is written for humans **and** AI agents (including small / local models), so it is organized into short, self-contained sections that can be read on their own.

## TL;DR

This repository is a **digital clone** — a personal presence for the AI era. Instead of a website, a person publishes their information as a graph of small, interlinked markdown files that **AI agents can traverse and humans can read**. People "talk to" the person by pointing their own AI agent (Claude Code or similar) at this repository; the agent reads only the files it needs to answer. The same content also renders for humans on GitHub and in Obsidian. It begins with public information and is designed to add authenticated, private information later. The whole pattern is meant to be **forked** so anyone can build their own.

This repository (`chitrangmshah`) is the **prototype** — patient zero for a replicable, open-source concept.

## Why this exists

Communication is shifting. People increasingly ask an AI agent about things rather than browsing pages themselves. A static website is built for human eyes; it is awkward for an agent to consume and reason over.

This system reframes a personal presence as something an **agent** reads first and a human reads too:

- **Agent-native.** The primary reader is an AI agent acting on someone's behalf ("tell me about this person", "how do I reach them", "what do they work on").
- **Human-readable.** The exact same markdown is browsable on GitHub and navigable in Obsidian — no separate build required.
- **A new channel.** Over time this becomes a way to *communicate with* the person through agents, not just read about them.

## How people use it

1. **Point an agent at it.** Modeled on [tiny.place](https://tiny.place): a person tells their agent to read an entry file and follow it. The agent then traverses the graph to answer.
2. **Clone and run.** Two reasons: (a) copy the *idea* to build your own; (b) clone the "brain" locally so an agent reads from disk instead of pulling over the network.
3. **Learn now, communicate later.** Today the agent *learns about* the person from public content. Real two-way channels (e.g. Telegram, Slack, Discord) come later, gradually and on demand.

## Core principles

- **Everything is markdown.** Every thought is captured as markdown; no other formats.
- **Granular files + pointers.** Many small files, each holding limited information and linking to others, form a graph. This keeps ingestion small so even a tiny model loads **only what is required** — avoiding context bloat.
- **Reuse over reinvent.** Look to reuse before building something new.
- **Public first, private later.** Start with public information; sensitive information (the kind kept off a public site) goes behind an authentication mechanism designed later.
- **Dual readership.** Optimize for AI *and* human readers at once; where they diverge, serve both deliberately.

## Architecture

### Fractal scaffolding

The same shape repeats at every level. Every folder carries the **trio** — `README.md` (human description), `AGENTS.md` (agent entry point), `INDEX.md` (index of the folder) — so any tool (Claude Code, Obsidian, VS Code) can operate on just that folder in isolation. A folder gains an `ai-agent-harness/` routing layer only once it **matures** into a promotion candidate, so small folders stay lightweight.

### Content vs. routing (the harness)

The system separates **content** from **navigation**:

- **Content folders** hold the data / answers.
- **`ai-agent-harness/`** is the **routing layer**: thin, self-describing *route* files that say *where to look* for a given intent — pointers, not answers. It is also the folder's **interface** (its import/export boundary). Route filenames plus the folder's `INDEX.md` act as an **emergent router**; there is no separate router file.

### DIKW promotion ladder (a process)

Thoughts **mature by promotion**, climbing this ladder as they grow — and everything stays markdown at every rung:

```
line item in a list  →  a list  →  a section  →  heading promoted up (H3 → H2 → H1)
   →  its own file  →  a folder of files  →  (eventually) its own repository
```

DIKW (Data → Information → Knowledge → Wisdom) is the **refinement process**, not a fixed folder layout: raw data is captured first and refined over time (the way scratch notes graduate into structured notes). Scheduled enrichment jobs can keep this moving so the graph stays current.

### Repo reproduction (offspring)

When a content folder matures into something independent (a research collection, articles, a book-in-markdown), it can **graduate into its own repository** with its own harness, which external people connect to directly. The default mechanism is a separate repo referenced by a canonical URL in the harness; git submodules are used when the child must stay physically nested. A **forwarding stub** is left at the old location so inbound references keep resolving and the graph does not break.

> Metaphor: the clone is a living organism that matures thoughts and reproduces offspring as repositories.

## Key files and their roles

| File / folder | Role |
|---|---|
| `README.md` (root) | Human-facing profile. On a `owner/owner` repo this renders as the GitHub profile page. |
| `AGENTS.md` | The **operating manual** — tool-agnostic rules and conventions for any agent. Written generically so it clones unchanged. |
| `INDEX.md` | The folder's index: `read` / `files` / `folders` lists; the navigable map. |
| `CLAUDE.md` | Thin Claude Code overlay that imports `AGENTS.md` (`@AGENTS.md`); holds only Claude-specific notes. |
| `ai-agent-harness/` | The routing / navigation layer (added on maturity). Routes point to content. |
| `CONCEPT.md` | This document — the scope and rationale of the whole system. |
| `SCRATCHPAD.md` | Raw, unorganized capture, refined into structured notes later. |

## Projection surfaces

The same markdown is *projected* onto multiple surfaces, no rebuild required:

- **AI agents** — read the raw markdown graph (the primary surface).
- **GitHub** — renders the profile and files for humans.
- **Obsidian** — treats the repo as a vault (graph view, backlinks).
- **VS Code** — editing.
- **SSG** — a possible future surface (a generated website).

## Conventions (summary)

`AGENTS.md` is the authoritative operating manual. In brief:

- **Trio always; harness on maturity** (see Architecture).
- **Naming:** kebab-case slugs.
- **Identifiers:** every markdown file has a stable `uuid:` (UUIDv7) in frontmatter — except the root profile `README.md` (frontmatter would render as a table on the public profile).
- **Rendering:** mind GitHub vs Obsidian differences (alert types, anchors, frontmatter tables).
- **Concurrency:** read before write; prefer targeted edits over full rewrites; append for capture; let git arbitrate. Markdown is the source of truth and may be edited in parallel.

## Status & roadmap

**Status:** early prototype. Scaffolding and conventions are largely in place; content is still thin.

**Open items being designed:** cross-boundary linking strategy; the forwarding-stub convention; the repo-promotion mechanism; the folder maturity threshold; the agent-assisted capture flow; an entry instruction for visiting agents; authentication for private information; a name for the open-source concept; and packaged skills for steering agents.

## Glossary

- **Digital clone** — a person's information published as an agent-traversable, human-readable markdown graph.
- **Harness** — the routing/navigation layer (`ai-agent-harness/`); the interface that points to content.
- **Route** — a thin file naming an intent/topic and pointing to where the content lives.
- **Trio** — the `README.md` + `AGENTS.md` + `INDEX.md` present in every folder.
- **Projection surface** — a place the same markdown is rendered/consumed (agent, GitHub, Obsidian, VS Code, SSG).
- **Promotion** — a thought maturing up the ladder (line → list → section → file → folder → repo).
- **Forwarding stub** — a small pointer left where content used to be, so references still resolve after promotion.
