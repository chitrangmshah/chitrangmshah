---
uuid: 019f1888-fcc8-7372-8c91-304da8535797
---
# AGENTS.md

Guidance for AI agents, LLMs, and models working in this repository. This is the **tool-agnostic source of truth** for how to work here; tool-specific files (e.g. `CLAUDE.md`) import this file rather than duplicating it. It is written to be **generic and reusable** — it names no specific owner, repo, or content, so it can be cloned into any repo or folder unchanged.

## read
+ README.md
+ CONCEPT.md
+ INDEX.md

## What this repository is

This is **not a software project** — there is no build, test, lint, or run tooling, and no source code. It is a **personal knowledge base** authored as interlinked markdown, meant to be read and traversed by AI agents *and* humans. Depending on how it is published it may also be:

- a **GitHub profile repo** — if the repo is named `<owner>/<owner>`, the root `README.md` renders on that owner's public GitHub profile, so changes to it are public-facing;
- an **Obsidian vault** — a `.obsidian/` directory, if present, makes the whole repo a vault.

"Everything is markdown" is an explicit principle. Because there is no code, the work here is editing and organizing markdown; **verification** means checking that links resolve, frontmatter is valid, and the conventions below hold.

## Working rules

These apply to every agent and tool operating in this repo.

- **Read before write.** Markdown files are the source of truth and may be edited in parallel — by another agent, by a projection tool such as Obsidian, or by the owner directly — without this agent's knowledge. Always read a file's current content immediately before writing it.
- **Prefer targeted edits over full rewrites.** A precise, exact-match edit fails loudly when the surrounding text has changed (catching a concurrent edit) instead of silently overwriting it. Rewrite a whole file only when necessary.
- **Append for capture.** Adding a new item is safest as an append; appends rarely collide and merge cleanly. Don't rewrite a file just to add to it.
- **Let git arbitrate.** Commit in small, frequent units so concurrent changes can be detected and merged rather than lost.
- Avoid parallel access where possible; a locking/claim convention will be added only if collisions actually occur.
- **Verify fast-moving terms.** In fast-moving domains (AI, agents, tooling, standards) training may be stale or miss recently-coined terms. For a load-bearing term you cannot recall crisply, state your working definition in one line and invite correction, and do a quick web search before building on it — don't silently assume.

## Repo conventions

### Three-file trio (always present)

Every folder carries three files:

- **`README.md`** — human-facing description of the folder's contents.
- **`AGENTS.md`** — entry point for AI agents/models; lists which files to read (typically `README.md` and `INDEX.md`).
- **`INDEX.md`** — the folder's index: a `## read` list, a `## files` list, and a `## folders` list. **Keep it current** when files or folders are added or removed.

These cross-reference each other. When you add content, update the folder's `INDEX.md`, and check whether parent `INDEX.md` files need the new folder listed.

### Operational layer — the harness (added on maturity)

A folder may also contain an **`ai-agent-harness/`** subfolder — its **operational layer** (the *harness*). Following the agent-harness model (*Agent = Model + Harness*), it holds everything needed to operate and evolve the folder that isn't the content itself, and it holds no answers. It has two faces: **navigation** (thin, self-describing *route* files pointing to where content lives; route filenames + `INDEX.md` form an emergent router) and **development-steering** (`ROADMAP.md`, `BACKLOG.md`, `DECISIONS.md`); later, **capture** (an inbox) and enrichment configs. It is the folder's interface (import/export boundary). It is added only once a folder has *matured* into a promotion candidate — not from birth — so small folders stay lightweight. The repo thus separates **content** (the data/answers, in ordinary folders) from the **harness** (the operational layer that navigates and evolves them).

### Naming

- Use **slugs** (kebab-case) for files and folders.

### Identifiers

- Every markdown file carries a stable **`uuid:`** in YAML frontmatter — a **UUIDv7** (RFC 9562; time-ordered, so sortable by creation), generated **once** and never changed. Write it as an unquoted plain scalar; a UUID is always a safe YAML string.
- Exception: the **root profile `README.md`** carries none, because GitHub renders frontmatter as a visible metadata table and that file is the public profile.

### Rendering (GitHub + Obsidian)

Content renders on both, which differ:

- GitHub callout/alert types are limited to `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION` (case-insensitive). Other types render as plain blockquotes on GitHub even though Obsidian supports them.
- GitHub auto-generates heading anchors in lowercase, and `[[wikilinks]]` are Obsidian-only (they do not render on GitHub). Prefer relative links with explicit extensions (e.g. `[INDEX.md](INDEX.md)`) for links that must work in both.
- GitHub renders YAML frontmatter as a metadata table at the top of a file (hence the root profile `README.md` exception above).

## Principles

- **Reuse over reinvent** — do not reinvent the wheel; look to reuse before making something new.
- **Everything is markdown.**

## Structure

- **Root** — the profile `README.md`, the `AGENTS.md` / `INDEX.md` trio, and optionally a tool overlay (e.g. `CLAUDE.md`).
- **Content folders** — the data/answers, each carrying its own trio.
- **`ai-agent-harness/`** — a routing layer, at root and inside any matured folder.
- **`.obsidian/`** — Obsidian vault config, if present; editing it changes the local Obsidian experience, not repo content.

## Licensing

See `LICENSE`.
