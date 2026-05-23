# EPAM Salesforce Practice — Claude Marketplace

Shared Claude skills for the EPAM Salesforce practice. Install once; get all future updates automatically.

## Install

```bash
/plugin marketplace add spadhy/epam-claude-marketplace
```

Then install individual plugins:

```bash
/plugin install attention-today
/plugin install team-progress
/plugin install salesforce-solution-design
```

## Plugins

| Plugin | What it does | Trigger |
|---|---|---|
| `attention-today` | Live status page sorted by Urgent / Critical / Necessary / Good-to-complete | "what needs my attention today" |
| `team-progress` | Weekly team digest — completions, blockers, upcoming deadlines | "team progress this week" |
| `salesforce-solution-design` | Scope, architect, and document Salesforce implementations | "design a Salesforce solution" |

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). Each plugin has a named maintainer in its folder.
PRs require maintainer approval (enforced by CODEOWNERS).

## Local foundation skill

The `architect-foundation` skill is a **local user skill**, not a plugin in this marketplace.
Install it separately following the setup guide in your onboarding docs. It provides the
five-domain architecture checklist that `salesforce-solution-design` references.
