# Findings — \<pack-name\>

**Repo:**  
**Scan path:**  
**Scan date:** (America/New_York)  
**Scope:** Read-only inventory + pattern scan for agent-bait / coding hygiene.  
**Constraints observed:** e.g. Did not run install scripts. No live secrets published. No PoCs.

## Verdict

**Label:** `SAFE-looking` | `PASS WITH NITS` | `FAIL` | `PENDING Security`

One-paragraph fair characterization.

**High severity:** none / list  
**Final PASS/FAIL:** …

## Read it back (plain English)

Grouped digest of what this pack *actually* does — not a skim of titles:

- **Install / setup:**
- **Auth / credentials:**
- **Network / remote:**
- **Persistence / agent-home:**
- **Personas / prompts:**
- **Side installs ("also install"):**

## Open-first queue

Files / paths to open first (highest blast radius → lowest):

1.
2.
3.

## Inventory

| Item | Result |
|------|--------|
| Total non-git files | |
| `*.md` | |
| Scripts (sh / py / ps1) | |
| `package.json` / other PM | |
| Binary blobs | |
| Files >100KB | |
| `.github/workflows` | |
| External app / cask / releases | |

### Structure notes

Benign shape vs surprising shape (short).

## Deep scan (foundation)

| Area | Notes |
|------|-------|
| Transitive deps / lifecycle scripts | |
| Sibling skills / submodules / also-install | |
| MCP / CLI / desktop outside clone | |
| CI / release binaries | |
| Existing secret / VPN / browser assumptions | |

## Findings

### F-001 \<Sev\> — \<title\>

- **Path:**
- **Pointer:** (what you saw — no exploit steps)
- **Why:** (hygiene / consent / dual-use / supply-chain)
- **Patch pointer:** (gate / dry-run / refuse / attest — defensive only)

<!-- Repeat F-00N as needed -->

## Negative pattern results

| Check | Result |
|-------|--------|
| Jailbreak as attack instruction | |
| Disable safety / hidden instruction | |
| Webhook exfil URLs | |
| Remote fetch piped to shell | |
| Long base64 / obfuscation | |
| Zero-width / bidi unicode | |
| Live private keys / cloud keys | |
| Miners / botnet C2 | |
| Hide-from-user / escalate-without-consent bait | |

## Top items for Security review

1.
2.
3.

## Recommendation

Do-not-run blindly into production agent runtimes? Clone/read/diff reasonable?

**Label:** …
