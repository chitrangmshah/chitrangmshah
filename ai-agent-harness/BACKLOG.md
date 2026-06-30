---
uuid: 019f195a-ce73-7746-bdb1-8ad3c6eeda29
---
# BACKLOG

> [!NOTE]
> Prioritized open work items, delivered in small chunks (AGILE). Each carries its question, our current leaning, and status. When an item is resolved, its rule codifies into `../AGENTS.md` / `../CONCEPT.md` and its rationale into `DECISIONS.md`, then it is checked off here. The Claude Code session task list mirrors this file; **this file is the durable source.**

## Open

- [ ] **Cross-boundary linking strategy.** How links survive folder isolation and promotion. *Leaning:* relative links down / internal; declare up / out references in the folder's harness via canonical URLs; defer a stable-`uuid` resolver until promotion actually breaks a path link.
- [ ] **Forwarding-stub-on-promotion convention.** The stub left at the old location when something is promoted, so inbound references still resolve. *Leaning:* a small pointer (file or section) to the new location via canonical URL / `uuid`.
- [ ] **Repo-promotion mechanism.** How a matured folder graduates into its own repo. *Leaning:* default = separate repo + canonical-URL pointer in the harness; git submodule only when physical nesting is needed; pair with a forwarding stub.
- [ ] **Folder maturity threshold.** When a folder earns its own `ai-agent-harness/`. *Leaning:* TBD — define concrete criteria (independence / size / promotion-candidacy).
- [ ] **Agent-assisted capture flow.** How thoughts get captured. *Leaning:* triage-later via an append-only inbox (safest under parallel writes; matches DIKW). Open: `INBOX.md` vs `SCRATCHPAD.md`. Finding: the Socratic dialogue is the refinement engine; the inbox / backlog is the parking lot.
- [ ] **Entry instruction in root `AGENTS.md`** *(gated)*. "To answer about the owner, start in `ai-agent-harness/`." Do once real routes exist.
