# Contributing to the EPAM Claude Marketplace

Thanks for helping grow the team's skill library. This doc explains how to add a new skill, update an existing one, and keep ownership clear.

---

## Governance model: maintainer-per-skill

Every plugin has exactly one **primary maintainer** listed in its `MAINTAINERS.md`. That person:

- Owns the PR review queue for their plugin (3 business-day SLA)
- Sets the direction for new features
- Bumps the version number on each release
- Can delegate or hand off ownership by updating `MAINTAINERS.md` and notifying the practice lead

The practice lead (`siba_padhy@epam.com`) is the fallback reviewer for any plugin with no active maintainer.

---

## Adding a new plugin

1. **Claim it first.** Open a GitHub issue titled `[new plugin] <plugin-name>` and describe what it does. Assign yourself as maintainer. This avoids duplicate work.

2. **Scaffold the folder.**
   ```
   plugins/<plugin-name>/
   ├── .claude-plugin/plugin.json
   ├── README.md
   ├── CHANGELOG.md
   ├── MAINTAINERS.md
   └── skills/<skill-name>/
       ├── SKILL.md
       └── assets/          ← optional: HTML templates, images, etc.
   ```

3. **Write the skill.** `SKILL.md` must include:
   - A `description:` frontmatter block (1–2 sentences; this is what users see in search)
   - A `triggers:` list (phrases that should activate the skill)
   - Step-by-step instructions Claude follows when the skill runs
   - A `graceful_degradation:` section explaining what happens when connectors are missing

4. **Add an entry to `marketplace.json`** at the repo root.

5. **Open a PR.** Include in the description:
   - What the skill does
   - Example prompt → example output (before/after)
   - Which connectors it needs
   - Who the maintainer is

6. **Two approvals required:** plugin maintainer (you, for new plugins) + one other practice member.

---

## Updating an existing plugin

1. Branch from `main`, make your changes, bump the version in `plugin.json` and `CHANGELOG.md`
2. PR to the plugin's maintainer
3. Maintainer merges; users get the update on next Claude restart

Version scheme: `MAJOR.MINOR.PATCH`
- PATCH: typo fix, wording tweak, no behaviour change
- MINOR: new feature, backward-compatible
- MAJOR: breaking change (e.g. different connector required, different output format)

---

## Skill naming convention

`sf-<verb>-<noun>` — all lowercase, hyphens only.

Examples: `sf-build-account-brief`, `sf-draft-rfp-response`, `sf-summarise-email-thread`

---

## Weekly skill review

Every week (day/time TBD by practice lead), contributors join a 30-minute call to:
- Demo any in-progress skills
- Merge PRs that are ready
- Decide what to build next

New contributors always welcome. No PR required to join — just show up with an idea.

---

## Code of conduct

- Be constructive in PR reviews
- Don't merge your own PR (except for trivial typo patches)
- If a skill doesn't work, open an issue — don't silently revert it
- Credit contributors in `CHANGELOG.md`
