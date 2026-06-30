# AGENTS.md

Guidance for AI agents, LLMs, and models working in this repository. This is the **tool-agnostic source of truth** for how to work here. Tool-specific files (e.g. `CLAUDE.md`) import this file rather than duplicating it.

## read
+ README.md
+ INDEX.md

## What this repository is

This is **not a software project** — there is no build, test, lint, or run tooling, and no source code. It is a personal knowledge base / content repo that serves two purposes at once:

1. **GitHub profile repo.** The repo name matches the owner (`chitrangmshah/chitrangmshah`), so root `README.md` renders on the GitHub profile page at https://github.com/chitrangmshah. Changes to root `README.md` are public-facing.
2. **Obsidian vault.** The `.obsidian/` directory makes the whole repo an Obsidian vault. "Everything is markdown" is an explicit project principle — content is authored as interlinked markdown notes, not documents in other formats.

Because there is no code, the work here is editing and organizing markdown. There are no commands to build or test; **verification** means checking that links resolve, frontmatter is valid, and the conventions below hold.

## Repo conventions (the important part)

Each folder follows a three-file pattern. When creating a new folder, add all three:

- **`README.md`** — human-facing description of the folder's contents.
- **`AGENTS.md`** — entry point for AI agents/models; lists which files an agent should read (typically points to `README.md` and `INDEX.md`).
- **`INDEX.md`** — the index of that folder: a `## read` pointer list, a `## files` list, and a `## folders` list. **Every folder should have an `INDEX.md`.** Keep it current when adding or removing files/folders.

These three files cross-reference each other. When you add content to a folder, update its `INDEX.md` so the listing stays accurate, and check whether parent `INDEX.md` files need the new folder added.

### Naming

- Use **slugs** (kebab-case) for files and folders, e.g. `chitrang-shah`, `ai-agent-harness`.

### Rendering note (GitHub + Obsidian)

Content renders on **both** GitHub and Obsidian, which differ:

- GitHub callout/alert types are limited to `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION` (case-insensitive). Other types (e.g. `[!Purpose]`, `[!hint]`) render as plain blockquotes on GitHub even though Obsidian supports them.
- Prefer relative links with explicit extensions (e.g. `[AGENTS.md](AGENTS.md)`) so links resolve on GitHub.

### Guiding principles (from `chitrang-shah/SCRATCHPAD.md`)

- **Reuse over reinvent** — "do not reinvent the wheel; always think to reuse first before making something."
- **Everything is markdown.**
- `SCRATCHPAD.md` is for raw, unorganized thoughts that get refined into structured notes later.

## Structure

- Root — profile `README.md`, plus the `AGENTS.md` / `INDEX.md` index pair and the `CLAUDE.md` overlay.
- `chitrang-shah/` — personal notes, including `SCRATCHPAD.md`.
- `ai-agent-harness/` — notes related to AI agent harnesses.
- `.obsidian/` — Obsidian vault config (plugins, workspace, appearance). Editing tool config here changes the local Obsidian experience, not repo content.

## Licensing

Released into the public domain under the Unlicense (see `LICENSE`).
