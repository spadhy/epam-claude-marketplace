# EPAM Salesforce Practice — Claude Plugin Marketplace

A shared library of Claude plugins built specifically for the EPAM Salesforce Practice. Each plugin extends Claude with practice-specific capabilities — pre-meeting research, solution design, team tracking, and more.

---

## For Practice Members: Get Started in 3 Steps

### Prerequisites

- **Claude Desktop** installed on your Mac or Windows machine ([claude.ai/download](https://claude.ai/download))
- **Claude Code** installed — open Terminal and run:
  ```bash
  npm install -g @anthropic-ai/claude-code
  ```
- A Claude account with access to the EPAM team workspace

---

### Step 1 — Add the EPAM SF Marketplace

Open Terminal and run:

```bash
claude plugin marketplace add spadhy/epam-claude-marketplace
```

This registers the EPAM Salesforce Practice marketplace in your Claude installation. You only need to do this once.

---

### Step 2 — Install a Plugin

```bash
claude plugin install meeting-brief
```

Replace `meeting-brief` with any plugin name from the list below. Repeat for each plugin you want.

---

### Step 3 — Use It

Open Claude Desktop (Cowork mode) and trigger your plugin naturally:

- **meeting-brief** → *"Prepare a meeting brief for [Name] at [Company]"*
- **attention-today** → *"What needs my attention today?"*
- **salesforce-solution-design** → *"Help me design a Salesforce solution for [use case]"*
- **team-progress** → *"Show me this week's team progress"*

---

## Available Plugins

| Plugin | What it does | How to trigger |
|---|---|---|
| `meeting-brief` | AI-powered pre-meeting research — pulls from EPAM internal systems, Outlook, and public sources to produce a 12-section intelligence brief and Word document | "Prepare for a meeting", "Generate a meeting brief", "Brief me on [Name]" |
| `attention-today` | Live personal status page showing everything that needs your attention today, sorted by priority tier (Urgent / Critical / Necessary / Good-to-complete) | "What needs my attention today?", "Show me my daily status" |
| `salesforce-solution-design` | Scopes, architects, and documents Salesforce implementations using EPAM practice standards | "Help me design a Salesforce solution", "Scope this Salesforce project" |
| `team-progress` | Weekly team digest — surfaces blockers, completions, and upcoming deadlines across Jira and email | "Show team progress", "What's the team working on this week?" |

---

## Keeping Plugins Up to Date

To pull the latest version of all plugins:

```bash
claude plugin update --all
```

To update a specific plugin:

```bash
claude plugin update meeting-brief
```

---

## Getting Help

| Need | Contact |
|---|---|
| Plugin not working | Post in the **#sf-practice-claude** Teams channel |
| Suggest a new plugin idea | Open a [GitHub Discussion](https://github.com/spadhy/epam-claude-marketplace/discussions) |
| Want to build a plugin | See [CONTRIBUTING.md](./CONTRIBUTING.md) |
| Marketplace admin | Siba Padhy — siba_padhy@epam.com |

---

## For Contributors: Build a Plugin

Want to contribute a new plugin or improve an existing one? See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full guide — plugin structure, branch naming, the review process, and how to get your plugin listed here.

---

## Marketplace Structure

```
epam-claude-marketplace/
├── .claude-plugin/
│   └── marketplace.json        ← plugin registry
├── plugins/
│   ├── attention-today/        ← plain folder plugin
│   ├── team-progress/          ← plain folder plugin
│   ├── salesforce-solution-design/   ← plain folder plugin
│   └── meeting-brief-agent/    ← git submodule → github.com/spadhy/meeting-brief-agent
├── README.md
├── CONTRIBUTING.md
└── CODEOWNERS
```

## Local foundation skill

The `architect-foundation` skill is a **local user skill**, not a plugin in this marketplace.
Install it separately following the setup guide in your onboarding docs. It provides the
five-domain architecture checklist that `salesforce-solution-design` references.
