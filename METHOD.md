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
- Do **not** require a paid PR-review SaaS to run this method (optional tools are accelerators only)

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

### 4. Read it back (plain English)

Do not skim titles and merge. Write a short **grouped** digest of what the pack *actually* does:

- Install / convert / setup
- Auth / credentials
- Network / webhooks / remote fetch
- Persistence / agent-home rewrite
- Personas / prompt packs
- Side installs ("also install X")

Group related pieces that belong together. Put this digest at the top of `FINDINGS.md` **before** pattern hits — so anyone reviewing knows what they shipped, not only what grep found.

### 5. Open-first queue

Decide which files to open first (highest blast radius). Default order:

1. Install / convert / setup scripts and lifecycle hooks
2. Anything that touches credentials, env, keychain, tokens, OAuth
3. Network / webhook / remote fetch / pipe-to-shell
4. Persistence / cron / agent-home config rewrite (`~/.claude`, `.cursor`, Hermes, etc.)
5. Security / offensive personas (dual-use depth)
6. Remaining `SKILL.md` / prompt packs

List the open-first queue in `FINDINGS.md` so the next reader does not start at a random markdown file.

### 6. Pattern pass (agent-bait hygiene)

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

Optional automated assist: [NVIDIA SkillSpector](https://github.com/NVIDIA/SkillSpector) (71 patterns). Cite their published rates only from their README/docs. Optional PR/diff reviewers can accelerate large packs — **never** a substitute for steps 4–7. This method stays human + agent review + `FINDINGS.md`.

### 7. Deep scan (foundation, not just the new wing)

Go wider than the files a Short or README highlights:

- Transitive deps and package lifecycle scripts
- Sibling skills / submodules / "also install" links the pack pulls in
- Recommended MCP servers / CLIs / desktop apps outside the clone
- CI workflows and release binaries that can rewrite machine state
- Assumptions about existing secrets, VPN/Tailscale, or signed-in browsers

Like a building inspector: check the **foundation**, not only the new extension.

### 8. Verdict labels

| Label | Meaning |
|-------|---------|
| `SAFE-looking` | No High classic agent-bait in this pass; still not a blank check to mass-install |
| `PASS WITH NITS` | Usable characterization with caveats (dual-use, installer hygiene, external binary) |
| `FAIL` | High severity agent-bait / malware-style patterns; do not install |
| `PENDING Security` | Needs Security Soft PASS before public claims |

High severity needs Security Soft PASS before public claims.

### 9. Write FINDINGS.md

Use [templates/FINDINGS.md](templates/FINDINGS.md):

- Plain-English digest + open-first queue
- Inventory table
- Findings with **path + why + patch pointer** (not exploit steps)
- Deep-scan notes (foundation / side installs)
- Constraints observed (e.g. no live secrets published, install scripts not executed)

### 10. Social (optional)

If Short-worthy: draft with [templates/SOCIAL-DRAFT.md](templates/SOCIAL-DRAFT.md). Digital avatar disclosure. Follow CTA. **Confirm with a human before any public post.**

## Output paths (suggested)

- Scan tree: `/workspace/<slug>-scan/`
- Findings: `FINDINGS.md` + optional `SOCIAL-DRAFT.md` (unpublished until confirmed)
- This OSS repo: checklist + templates only (do not commit third-party clones here)
