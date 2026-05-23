# Contributing

## Model: maintainer-per-plugin

Each plugin has one named maintainer in CODEOWNERS. That person owns the PR queue (3 business-day SLA) and bumps the version on each release.

## Adding a plugin

1. Open a GitHub issue: `[new plugin] <name>` — claim it to avoid duplicates
2. Create `plugins/<name>/` with this structure:
   ```
   plugins/<name>/
   ├── .claude-plugin/plugin.json   ← name + description only
   └── skills/<name>/
       ├── SKILL.md                 ← description frontmatter + instructions
       └── assets/                  ← optional templates
   ```
3. Add an entry to `.claude-plugin/marketplace.json` with `"source": "./plugins/<name>"`
4. Add yourself to CODEOWNERS: `/plugins/<name>/ @your-handle`
5. PR with a before/after example prompt in the description

## Updating a plugin

Branch, edit, PR to the plugin's maintainer. Version is managed via git SHA (no manual bump needed during active development).

## Naming convention

`<domain>-<verb>-<noun>` or `<domain>-<noun>`: e.g. `sf-draft-rfp`, `attention-today`, `team-progress`

## Weekly skill review

30 min weekly: demo in-progress skills, merge ready PRs, decide what to build next.
