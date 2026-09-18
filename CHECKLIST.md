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

## Read it back

- [ ] Plain-English digest written (what the pack actually does)
- [ ] Related pieces grouped (install / auth / network / persistence / personas / side installs)
- [ ] Open-first queue listed (highest blast radius first)
- [ ] Did **not** skim titles and call it done

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

## Deep scan (foundation)

- [ ] Transitive deps / package lifecycle scripts reviewed
- [ ] Sibling skills / submodules / "also install" links listed
- [ ] Recommended MCP / CLI / desktop apps outside the clone noted
- [ ] CI / release binaries that rewrite machine state flagged
- [ ] Assumptions about existing secrets / VPN / signed-in browsers noted

## Optional automation

- [ ] SkillSpector (or equivalent) report attached
- [ ] Stats cited only from vendor README/docs (no invented rates)
- [ ] Any PR/diff tool used only as accelerator — steps above still done

## Verdict & publish hygiene

- [ ] Verdict label set (`SAFE-looking` / `PASS WITH NITS` / `FAIL` / `PENDING Security`)
- [ ] `FINDINGS.md` written (digest + open-first + path + why + patch pointer + deep scan)
- [ ] Social draft marked **DO NOT PUBLISH** until human confirm
- [ ] No live secrets pasted into tickets, Shorts, or public issues
