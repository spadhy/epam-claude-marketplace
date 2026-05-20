# attention-today

A Claude skill that builds a **live, personal status page** showing everything that needs your attention today — sorted into four priority tiers. The page lives in your Claude sidebar and refreshes every time you open it or hit Reload.

---

## What it does

1. Probes your connected tools (Outlook email, Outlook calendar, Teams)
2. Classifies each item into a priority tier:
   - **Urgent** — meetings starting within 30 min, high-importance flagged items, anything requiring your approval or explicit action
   - **Critical** — meetings within 2 hours, unread email from direct colleagues, Teams DMs
   - **Necessary** — later-today calendar items, general unread email
   - **Good to complete** — newsletters, digests, FYI-only mail
3. Renders a live HTML artifact in your sidebar with source, sender/organiser, time, and a direct "Open ↗" link into Outlook or Teams
4. Falls back gracefully: if a connector isn't present for a section, that section shows "(not connected)" rather than erroring

---

## Trigger phrases

Say any of these to activate the skill:

- "What needs my attention today?"
- "Build my attention page"
- "Show me my daily status"
- "What should I focus on today?"

---

## Requirements

| Connector | Required? | What it provides |
|---|---|---|
| Microsoft 365 | **Yes** | Outlook email + calendar, Teams chat |
| Atlassian Rovo | Optional | Jira tickets assigned to you |

If Microsoft 365 is not connected, the skill will walk you through connecting it before building the page.

---

## Maintainer

See [MAINTAINERS.md](./MAINTAINERS.md)

## Changelog

See [CHANGELOG.md](./CHANGELOG.md)
