---
uuid: 019f1888-fcc8-7372-8c91-30500a7ab3df
---
# ai-agent-harness

The **routing / navigation layer** of this repo. This folder holds no answers — it holds **routes**: thin, self-describing files that tell an agent *where to look* for a given intent.

## How it works

- Each file here is a **route**, named to describe the intent or topic it serves (e.g. `how-to-reach-me.md`, `bio.md`). The filename is the signpost.
- A route is a **pointer, not the content** — it maps an intent to the file(s) that hold the actual data, which live in the **content layer** (e.g. `chitrang-shah/`). The harness knows *where* things are, not *what* they say.
- Route filenames plus `INDEX.md` together act as an **emergent router** — there is no separate router file. An agent reads the index, picks the route that matches the request, then follows it to the content.
- Thin routes keep ingestion small: a model loads one route file plus one content file — minimal context, no bloat.

## Conventions

- Route names may be **intent-style** (`how-to-reach-me.md`) or **topic-style** (`contact.md`), whichever fits.
- Routes are kept current through refinement over time (the DIKW process), including scheduled enrichment jobs — so `INDEX.md` should always reflect the real routes.

## Contents
_No routes captured yet — this folder currently holds only its index trio (`README.md`, `AGENTS.md`, `INDEX.md`). Add route files here and list them in `INDEX.md`._

> [!tip]
> See `INDEX.md` for the route listing and `AGENTS.md` for the agent entry point.
