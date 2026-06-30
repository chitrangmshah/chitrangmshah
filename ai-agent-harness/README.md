---
uuid: 019f1888-fcc8-7372-8c91-30500a7ab3df
---
# ai-agent-harness

The **operational layer** of this folder — the *harness*. Following the agent-harness model (**Agent = Model + Harness**), it holds everything an agent needs to **operate and evolve** this folder that isn't the content itself. It holds no answers; the answers live in content folders.

## What lives here

- **Navigation (routes)** — thin, self-describing *route* files that map an intent to *where* the content is (e.g. `how-to-reach-me.md`, `bio.md`). A route is a pointer, not the content. Route filenames plus `INDEX.md` act as an **emergent router** — no separate router file.
- **Development-steering** — how this folder / system is built and evolves:
  - `ROADMAP.md` — direction (Now / Next / Later).
  - `BACKLOG.md` — prioritized open work items.
  - `DECISIONS.md` — a lean log of decisions made and why.
- **Capture & enrichment** *(later)* — an inbox for raw capture; scheduled enrichment configs.

So the harness has two faces: **outward** (routes, for a visiting agent finding content) and **inward** (steering, for an agent building the system). For now both live here together; they can be split if the folder grows.

## Conventions

- Route names may be **intent-style** (`how-to-reach-me.md`) or **topic-style** (`contact.md`).
- Keep ingestion small: an agent loads one route file plus one content file — minimal context, no bloat.
- Added **on maturity**: a folder gains its own `ai-agent-harness/` only once it matures into a promotion candidate; small folders stay lightweight with just their README / AGENTS / INDEX trio.

> [!tip]
> See `INDEX.md` for the listing and `AGENTS.md` for the agent entry point.
