---
uuid: 019f19dc-c930-725a-8122-bb9e2c419f13
---
# PRIVACY

Some values in this repository appear as `🔒{private}` — the data exists but is intentionally withheld.

- **What it means.** The key stays visible so you can see *that* the information exists; only the value is redacted.
- **The marker.** The canonical token is `{private}` (a substring); it is displayed as `🔒{private}` — the 🔒 and the surrounding backticks (code styling) are cosmetic. Detection should match the token `{private}`.
- **Why.** This is a public-first space; sensitive or personal data — especially third parties' and minors' — is kept out of the public layer.
- **For AI agents.** Treat a `{private}` value as withheld: do not reveal, guess, or fabricate it. Tell the requester it is private. (See the redaction rule in `AGENTS.md`.)
- **Requesting access.** An authenticated way to request private values is planned but not yet available (see `ai-agent-harness/ROADMAP.md`).
