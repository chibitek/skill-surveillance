# Skill surveillance checklist

Copy this into your scan notes. Tick items as you go.

## Pre-flight

- [ ] Source URL captured
- [ ] Commit / tag pinned (if available)
- [ ] Scratch clone path chosen (`*-scan/`)
- [ ] Agree: **no** production mass-install during scan
- [ ] Agree: **no** exploit PoCs / attack playbooks in write-ups

## Clone & inventory

- [ ] Shallow clone (`--depth 1`) completed
- [ ] File-type counts recorded (md / sh / py / ps1 / json / binary)
- [ ] Package managers + lifecycle scripts noted
- [ ] `.github/workflows` listed (not necessarily executed)
- [ ] External binary / app / brew cask called out separately
- [ ] Large files / opaque blobs flagged

## Pattern pass (look for — do not weaponize)

- [ ] Jailbreak / ignore-previous / disable-safety as **instructions**
- [ ] Exfil / webhook / paste-site secret shipping
- [ ] Remote pipe-to-shell / silent non-TTY continue
- [ ] Credential / env / keychain harvest wording
- [ ] Config rewrite / persistence under agent home dirs
- [ ] Dual-use offensive depth in security personas
- [ ] Live-looking secrets vs labeled placeholders
- [ ] Hidden unicode / deceptive metadata
- [ ] Classic malware indicators (miners, C2, etc.)

## Optional automation

- [ ] SkillSpector (or equivalent) report attached
- [ ] Stats cited only from vendor README/docs (no invented rates)

## Verdict & publish hygiene

- [ ] Verdict label set (`SAFE-looking` / `PASS WITH NITS` / `FAIL` / `PENDING Security`)
- [ ] `FINDINGS.md` written (path + why + patch pointer)
- [ ] Social draft marked **DO NOT PUBLISH** until human confirm
- [ ] No live secrets pasted into tickets, Shorts, or public issues
