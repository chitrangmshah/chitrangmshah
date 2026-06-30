---
uuid: 019f195a-ce74-716b-93a9-a9571d65be3d
---
# DECISIONS

> [!NOTE]
> A **lean** log of significant decisions already made, and why. Open questions live in `BACKLOG.md`, not here. Kept deliberately light for now — we can adopt a fuller ADR format (context / options / consequences) when decisions get more contested.

- **`AGENTS.md` is the tool-agnostic, zero-edit-generic source of truth; `CLAUDE.md` imports it via `@AGENTS.md`.** Why: one place for conventions, no duplication, clones cleanly into any repo or folder.
- **Every markdown file carries a stable `uuid:` (UUIDv7, unquoted); the root profile `README.md` is the exception.** Why: an identity that survives promotion up the ladder; the profile stays clean because GitHub renders frontmatter as a table.
- **Separate *content* from the *harness*; `ai-agent-harness/` is the operational layer, not routing-only.** Following *Agent = Model + Harness*, the harness holds navigation + development-steering (this file, `BACKLOG`, `ROADMAP`) + future capture. Why: keeps root lean (identity / manual / scope), gives the harness a clear purpose, and scales fractally to every folder.
- **Keep this log lean (no full ADR template yet).** Why: too early; the ceremony isn't worth it until decisions get contested.
