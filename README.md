# EPAM Salesforce Practice – Claude Marketplace

A shared library of Claude skills for the EPAM Salesforce practice. Install once and get all future skill updates automatically. Anyone on the team can contribute.

---

## Install

1. Open Claude desktop → Settings → Plugins → Add marketplace
2. Paste this URL: `https://github.epam.com/<your-org>/epam-claude-marketplace`
3. Click **Install all** (or pick individual plugins)

That's it. When skills are updated, your Claude pulls the changes on next restart.

---

## Available plugins

| Plugin | What it does | Trigger phrase |
|---|---|---|
| [attention-today](./plugins/attention-today/README.md) | Live status page: everything needing your attention today, sorted by Urgent / Critical / Necessary / Good-to-complete | "what needs my attention today" / "build my attention page" |

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full workflow. Short version:

- Each plugin has a named **maintainer** in its `MAINTAINERS.md`
- Submit a PR; the plugin maintainer reviews within 3 business days
- Skill naming convention: `sf-<verb>-<noun>` (e.g. `sf-build-account-brief`)
- Add your skill to the table above and bump the version in `marketplace.json`

---

## Roadmap (next plugins)

- `sf-build-account-brief` — one-click Salesforce account summary from CRM + email + news
- `sf-draft-rfp-response` — draft an RFP response from a template + account context
- `sf-weekly-pipeline-digest` — weekly pipeline health digest from Salesforce + Jira

Want to claim one? Open an issue or ping the #epam-claude-skills channel.
