# Method — GitHub skill / agent-pack surveillance

Reusable hygiene method for scanning public GitHub agent skills, Claude/Codex/Cursor skill packs, and viral "AI employee" repos **before** install.

## When to run

- Someone pastes a viral Short / GitHub link about a skill pack, agent roster, or AI installer
- Before dogfooding any third-party skill, MCP installer, or agent harness on managed machines
- When packaging a Managed Intelligence / skillops Short or internal hygiene note

## Non-goals

- Do **not** invent malware findings or stats
- Do **not** write exploits, PoCs, or attack playbooks
- Do **not** mass-install the pack into production runtimes
- Do **not** claim NVIDIA / vendor endorsement
- Public captions: tip-only; never "Inspired by" or source channel names

## Steps (read-only first)

### 1. Capture source

Record:

- Repo URL
- Commit SHA or tag if pinned
- Short / caption for idea-fit (**internal only**)

### 2. Shallow clone

```bash
git clone --depth 1 <repo-url> /workspace/<slug>-scan
```

Prefer **not** running install / convert / setup scripts during the scan.

### 3. Inventory

Count and note:

- `*.md` / `*.sh` / `*.py` / `*.ps1` / `*.json` / binaries
- Package managers (`package.json`, `requirements.txt`, etc.) and lifecycle scripts
- `.github/workflows`
- Desktop apps, GitHub Releases binaries, Homebrew casks **outside** the clone
- Files >100KB, long base64 blobs, unexpected binaries

### 4. Pattern pass (agent-bait hygiene)

Search and **report paths + short context**. Patterns = what to look for, not how to build attacks:

| Look for | Why it matters |
|----------|----------------|
| Ignore-previous / jailbreak / "disable safety" wording as instructions | Agent-bait |
| Exfil / webhook dump / paste-site secret shipping | Data loss |
| `curl \| bash`, remote pipe-to-shell, silent continue without TTY | Supply-chain |
| Env / keychain / credential harvest wording | Secret theft |
| Cron / persistence / config rewrite under `~/.claude`, `.cursor`, Hermes, etc. | Consent / persistence |
| Dual-use offensive technique depth in security personas | Bulk prompt surface |
| Live-looking keys vs labeled placeholders | Accidental secret leak |
| Zero-width / bidi unicode / hidden HTML comments in skill metadata | Concealment |
| Miners / botnet / C2 indicators | Classic malware |

Optional automated assist: [NVIDIA SkillSpector](https://github.com/NVIDIA/SkillSpector) (71 patterns). Cite their published rates only from their README/docs. This method stays human + agent review + `FINDINGS.md`.

### 5. Verdict labels

| Label | Meaning |
|-------|---------|
| `SAFE-looking` | No High classic agent-bait in this pass; still not a blank check to mass-install |
| `PASS WITH NITS` | Usable characterization with caveats (dual-use, installer hygiene, external binary) |
| `FAIL` | High severity agent-bait / malware-style patterns; do not install |
| `PENDING Security` | Needs Security Soft PASS before public claims |

High severity needs Security Soft PASS before public claims.

### 6. Write FINDINGS.md

Use [templates/FINDINGS.md](templates/FINDINGS.md):

- Inventory table
- Findings with **path + why + patch pointer** (not exploit steps)
- Constraints observed (e.g. no live secrets published, install scripts not executed)

### 7. Social (optional)

If Short-worthy: draft with [templates/SOCIAL-DRAFT.md](templates/SOCIAL-DRAFT.md). Digital avatar disclosure. Follow CTA. **Confirm with a human before any public post.**

## Output paths (suggested)

- Scan tree: `/workspace/<slug>-scan/`
- Findings: `FINDINGS.md` + optional `SOCIAL-DRAFT.md` (unpublished until confirmed)
- This OSS repo: checklist + templates only (do not commit third-party clones here)
