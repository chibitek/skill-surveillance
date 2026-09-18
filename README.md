# Skill surveillance

**Read-only hygiene method** for scanning AI agent skills and skill packs **before** you install them.

Viral "hire 280 AI employees" repos, Claude/Codex/Cursor skill packs, and MCP installers are untrusted software until you inventory them. This repo is the open checklist + templates Chibitek uses for Managed Intelligence / skillops hygiene.

> Not a malware toolkit. Patterns here are **what to look for**, not how to weaponize anything. No exploit PoCs, payloads, or attack playbooks.

## Why this exists

Agent skills often ship as markdown personas, helper scripts, and installers that rewrite local tool configs (`~/.claude`, `.cursor`, Hermes, etc.). A pack can look clean of classic droppers and still expand dual-use prompt surface or mutate your agent directories without a dry-run.

NVIDIA's [SkillSpector](https://github.com/NVIDIA/SkillSpector) research (README, citing Liu et al., 2026) analyzed a **31,132-skill** subset and reports **~26.1%** of skills contain vulnerabilities and **~5.2%** show likely malicious intent. That validates the habit: scan before install.

**Relationship to SkillSpector:** SkillSpector is a strong automated accelerator (71 patterns across 17 categories). This repo is a **human + agent review habit** with FINDINGS.md templates. Use both. Chibitek does **not** claim NVIDIA endorsement, partnership, or affiliation.

## What you get

| Path | Purpose |
|------|---------|
| [METHOD.md](METHOD.md) | Step-by-step read-only surveillance method |
| [CHECKLIST.md](CHECKLIST.md) | Printable / copy-paste checklist |
| [templates/FINDINGS.md](templates/FINDINGS.md) | Findings report template |
| [templates/SOCIAL-DRAFT.md](templates/SOCIAL-DRAFT.md) | Unpublished social / Short draft template |
| [examples/agency-agents-summary.md](examples/agency-agents-summary.md) | High-level example summary (no attack playbooks) |

## Quick start

1. Capture the source URL (and commit/tag if pinned).
2. Shallow clone into a scratch path. Prefer **not** running install scripts.
3. Inventory file types, workflows, package managers, and any desktop app / brew cask outside the clone.
4. Run the pattern pass in [METHOD.md](METHOD.md) — report paths + context only.
5. Optionally run [SkillSpector](https://github.com/NVIDIA/SkillSpector) and attach the report.
6. Write `FINDINGS.md` with a verdict label: `SAFE-looking` / `PASS WITH NITS` / `FAIL` / `PENDING Security`.
7. Keep social drafts unpublished until a human confirms.

## Non-goals

- Do not invent findings or stats.
- Do not write exploits, PoCs, or offensive how-tos.
- Do not mass-install third-party packs into production agent runtimes.
- Do not claim NVIDIA or vendor endorsement of Chibitek.
- Public captions: tip-only; no "Inspired by" or source channel name-drops.

## License

[MIT](LICENSE)

## Maintainers

Chibitek Labs — Managed Intelligence / skillops hygiene.
