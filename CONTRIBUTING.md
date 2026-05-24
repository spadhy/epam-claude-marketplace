# Contributing to the EPAM SF Claude Plugin Marketplace

Thank you for helping grow the practice's agentic toolkit. This guide covers everything you need — from proposing an idea to getting your plugin merged and listed.

---

## Review model

Every change goes through a two-tier review before it reaches `main`:

| Change type | Required reviewers |
|---|---|
| New plugin or changes inside `plugins/<name>/` | Plugin maintainer (listed in CODEOWNERS for that folder) |
| `marketplace.json`, `README.md`, `CODEOWNERS`, root files | Marketplace owner (@spadhy) + at least one designated reviewer |

**Designated reviewers** — these people are empowered to approve PRs alongside the marketplace owner:

- @spadhy — Marketplace owner (all PRs)
- @[REVIEWER_2] — Add a second practice lead here
- @[REVIEWER_3] — Add a third practice lead here

> To nominate a reviewer, open a PR updating CODEOWNERS and tag @spadhy.

**Review SLA:** 3 business days. If you haven't heard back in 3 days, ping the PR thread and tag the reviewer directly.

---

## How to contribute a new plugin

### Step 1 — Open a GitHub Issue first

Before writing any code, open an issue titled `[new plugin] <your-plugin-name>`. This prevents duplicate effort and lets the team give early feedback on scope and naming.

### Step 2 — Fork and create a branch

Branch naming: `[your-epam-userid]/add-[plugin-name]`

```bash
git clone https://github.com/spadhy/epam-claude-marketplace.git
cd epam-claude-marketplace
git checkout -b spadhy/add-my-plugin   # replace with your userid and plugin name
```

### Step 3 — Build your plugin folder

Create `plugins/<your-plugin-name>/` with this structure:

```
plugins/<your-plugin-name>/
├── .claude-plugin/
│   └── plugin.json          ← name + description + trigger phrases (required)
├── skills/
│   └── <your-plugin-name>/
│       ├── SKILL.md          ← full skill instructions (required)
│       └── references/       ← optional supporting docs, templates, examples
├── README.md                 ← what it does, trigger phrases, screenshots
├── CHANGELOG.md              ← version history
└── MAINTAINERS.md            ← your name + email + GitHub handle
```

**`plugin.json` format:**
```json
{
  "name": "your-plugin-name",
  "description": "One sentence. Include trigger phrases so Claude activates it correctly.",
  "version": "1.0.0",
  "author": {
    "name": "Your Name",
    "email": "your_email@epam.com"
  }
}
```

**`SKILL.md` must include:**
- A clear description of what the skill does
- Step-by-step instructions Claude should follow
- Example trigger phrases
- Example output (what a good result looks like)

### Step 4 — Register in marketplace.json

Add an entry to `.claude-plugin/marketplace.json`:

```json
{
  "name": "your-plugin-name",
  "source": "./plugins/your-plugin-name",
  "description": "Short description for the marketplace listing — include trigger phrases.",
  "maintainer": "your_email@epam.com"
}
```

### Step 5 — Add yourself to CODEOWNERS

```
/plugins/your-plugin-name/   @your-github-handle
```

### Step 6 — Open a Pull Request

PR title: `Add [plugin-name] plugin`

Your PR description must include:
- [ ] Link to the GitHub issue you opened in Step 1
- [ ] One example prompt that triggers the skill
- [ ] One example of what the output looks like (paste or screenshot)
- [ ] Confirmation that `plugin.json` and `SKILL.md` are present
- [ ] Your entry added to `CODEOWNERS`
- [ ] Your entry added to `marketplace.json`

---

## How to update an existing plugin

Make changes in the plugin's folder, then open a PR. Branch naming: `[your-userid]/update-[plugin-name]`

If you are the plugin's maintainer (listed in CODEOWNERS), you can self-approve changes to your own plugin folder, but a second reviewer from the designated list is still required for `marketplace.json` or `CODEOWNERS` changes.

Bump the version in `plugin.json` and add an entry to `CHANGELOG.md` for every meaningful change.

---

## Naming conventions

Plugin names follow `<domain>-<noun>` or `<domain>-<verb>-<noun>`:

```
meeting-brief       ✅
attention-today     ✅
sf-draft-rfp        ✅
SalesforcePlugin    ❌  (no camelCase)
my_plugin           ❌  (no underscores)
```

---

## Plugin quality checklist

Before opening your PR, check all of these:

- [ ] `plugin.json` is valid JSON with `name`, `description`, `version`, `author`
- [ ] `SKILL.md` contains step-by-step instructions and example trigger phrases
- [ ] `README.md` explains what the plugin does and how to use it
- [ ] `CHANGELOG.md` has an entry for v1.0.0
- [ ] `MAINTAINERS.md` has your name, email, and GitHub handle
- [ ] Plugin name follows the naming convention
- [ ] `marketplace.json` entry added with correct `source` path
- [ ] `CODEOWNERS` entry added

---

## Proposing ideas without building

Not ready to build but have a great idea? Open a GitHub Discussion under the **Ideas** category. The team reviews these in the weekly plugin session and assigns them to volunteers.

---

## Weekly plugin session

**When:** Every [DAY] at [TIME] — 30 minutes
**Format:** Demo in-progress plugins → merge ready PRs → decide what to build next
**Where:** Teams channel **#sf-practice-claude**

Everyone on the practice is welcome. You don't need to have a plugin in flight to attend.
