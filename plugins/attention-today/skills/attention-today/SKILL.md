---
name: attention-today
version: 0.1.0
description: >
  Builds a live personal status page showing everything that needs the user's attention
  today across Outlook email, calendar, and Teams — sorted into Urgent, Critical,
  Necessary, and Good-to-complete priority tiers. Refreshes on every open or reload.
triggers:
  - "what needs my attention today"
  - "build my attention page"
  - "show me my daily status"
  - "what should I focus on today"
  - "attention today"
  - "daily briefing page"
required_connectors:
  - microsoft-365
optional_connectors:
  - atlassian-rovo
maintainer: siba_padhy@epam.com
---

# Skill: attention-today

## Purpose

Build a live, personal HTML artifact (rendered in the user's Claude sidebar) that aggregates
everything needing the user's attention today from their connected tools and sorts items
into four priority tiers.

## Priority tier definitions

| Tier | Criteria |
|---|---|
| **Urgent** | Meetings starting within 30 minutes; email/calendar items flagged high-importance; anything containing approval or action-required language |
| **Critical** | Meetings starting within 2 hours; unread email from direct EPAM colleagues; Teams direct messages |
| **Necessary** | Meetings later today; general unread email not in Urgent/Critical |
| **Good to complete** | Newsletters, digests, FYI bulletins, CC'd mail with no action implied |

## Steps to execute

### 1. Check connectors

Before doing any tool calls, check which MCP tools are available in the session:

- Look for tools matching `*outlook_email*`, `*outlook_calendar*`, `*chat_message*` — these are the Microsoft 365 connector tools.
- Look for tools matching `*jira*` or `*rovo*` — these are Atlassian tools.

If Microsoft 365 tools are **not** present, tell the user:
> "To build your Attention Today page I need Microsoft 365 connected. Go to Settings → Connectors, connect Microsoft 365, then come back and try again."

Stop. Do not proceed until Microsoft 365 is connected.

### 2. Probe each source

Make real tool calls to understand response shapes:

**Email** — call `outlook_email_search` with:
- query: `""` (empty, to get recent/unread)
- max results: 20

**Calendar** — call `outlook_calendar_search` with:
- query: today's date range (today 00:00 → today 23:59)
- max results: 20

**Chat** — call `chat_message_search` with:
- query: `""` or `"@me"` to get recent DMs and mentions
- max results: 20

If any call fails or times out, log "(not connected)" for that section — do NOT abort the whole skill.

### 3. Classify items

For each item returned, assign it to the highest-priority tier it qualifies for:

**Email classification:**
- Urgent: `importance == "high"` OR subject contains words like "urgent", "action required", "approval needed", "ASAP", "by end of day"
- Critical: sender domain matches user's own domain (e.g. `@epam.com`) AND email is unread
- Necessary: unread and not classified above
- Good to complete: newsletters (List-Unsubscribe header), digests, read emails

**Calendar classification:**
- Urgent: starts within 30 minutes of now
- Critical: starts within 2 hours of now
- Necessary: starts later today
- (No "Good to complete" for calendar items)

**Chat classification:**
- Critical: direct messages (1:1 conversations)
- Necessary: @mentions in group channels
- Good to complete: FYI channel messages

### 4. Build the artifact

Load the artifact template from `assets/artifact-template.html` and substitute:

| Placeholder | Replace with |
|---|---|
| `__TOOL_EMAIL__` | Actual MCP tool name for email search |
| `__TOOL_CALENDAR__` | Actual MCP tool name for calendar search |
| `__TOOL_CHAT__` | Actual MCP tool name for chat search |
| `__USER_DOMAIN__` | User's email domain (e.g. `epam.com`) |
| `__TODAY_DATE__` | Today's date in ISO format |
| `__UNAVAILABLE__` | Use for any connector that is not present |

If a connector is unavailable, set its tool name to `__UNAVAILABLE__` — the template renders a "(not connected)" banner for that section instead of making a broken tool call.

Then call `create_artifact` with:
- title: "Attention Today"
- the substituted HTML content
- mcp_tools: list all tool names that are available (omit unavailable ones)

### 5. Confirm to the user

After creating the artifact, tell the user:
> "Your Attention Today page is live in the sidebar. It refreshes every time you open it or hit Reload — no schedule needed."

Optionally offer:
> "Want me to set up a morning briefing that pushes a summary to chat each weekday at a time of your choice?"

## Graceful degradation

This skill must NEVER fail hard due to a missing connector. Rules:

- If email tools are missing → render "(Outlook email not connected)" in the email section
- If calendar tools are missing → render "(Outlook calendar not connected)" in the calendar section
- If chat tools are missing → render "(Teams not connected)" in the chat section
- If ALL Microsoft 365 tools are missing → stop and prompt the user to connect (see Step 1)

## Example prompts that trigger this skill

- "What needs my attention today?"
- "Build me a live page showing what I need to deal with"
- "Set up my attention today page"
- "Give me a daily briefing page I can keep open"
