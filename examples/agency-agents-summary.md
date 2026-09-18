# Example summary — agency-agents (high-level)

**Source pack:** [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)  
**Scan style:** Read-only shallow clone + pattern pass (Chibitek method)  
**Scan date:** 2026-09-06 (America/New_York)  
**This file:** High-level summary only. No attack playbooks, no exploit steps, no full offensive excerpts.

## Fair characterization

SAFE-looking **markdown skill pack** with:

- Dual-use offensive-security **persona** content (education / authorized red-team framing in security division docs)
- A local setup helper that can copy/symlink agents into user tool directories and may rewrite Hermes-style config

Classic malware / silent-exfil / jailbreak-to-steal-secrets patterns were **not** evidenced in that pass.

**Executor label:** SAFE-looking markdown pack + dual-use security skills + installer hygiene caveats.  
**Security tip (same day):** PASS WITH NITS — characterization only. Not a Chibitek runtime adopt. Hold public claims until a human confirms.

## Inventory (high level)

- Mostly persona markdown across many divisions (~280-employee framing in README)
- Local convert / install / lint helpers; CI workflows present
- No package.json in the scanned tree; no binary blobs called out in the markdown scan
- README also points at a separate desktop app / Homebrew cask (binary **outside** the markdown clone — attest separately)

## What mattered (defensive pointers only)

| ID | Sev | Theme | Defensive takeaway |
|----|-----|-------|--------------------|
| F-001 | Med | Dual-use depth in security personas | Gate security division enablement; stronger out-of-scope refusal |
| F-002 | Med | Install helper mutates local agent dirs / config | Dry-run default; explicit confirm before config rewrite |
| F-003 | Info/Med | External app / cask | Separate binary attestation |
| F-004 | Info | Didactic API-key-shaped string | Treat as placeholder; prefer clear EXAMPLE_ labeling |
| F-005 | Info | Anti-injection wording in some personas + SECURITY.md | Positive control — keep |

## Negative checks (that pass)

Jailbreak-as-attack-instruction, webhook exfil URLs, remote pipe-to-shell in helpers, long obfuscation, zero-width tricks, live cloud/private keys, miners/C2, and hide-from-user bait were **not found** as High classic malware-style hits in that pass.

## Lesson for skillops

Viral bulk-load stories are a **hygiene test**, not a free hiring spree. Inventory first. Diff the prompts. Gate dual-use packs. Confirm before you let a helper rewrite `~/.your-agent`.

For the reusable method, see [METHOD.md](../METHOD.md) and [CHECKLIST.md](../CHECKLIST.md).
