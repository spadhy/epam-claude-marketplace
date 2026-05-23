---
description: >
  Build or refresh a live personal status page showing everything that needs the user's
  attention today. Trigger when the user asks "what needs my attention today", "what should
  I focus on", "show me my daily priorities", "build my attention page", or any similar
  request for a real-time view of their inbox, calendar, or chat backlog.
---

# Skill: attention-today

Build a live HTML artifact in the user's sidebar that pulls from their connected tools and
sorts today's items into four priority tiers. The page refreshes on every open or reload.

## Step 1 — Check connectors

Inspect which MCP tools are available in this session:
- Email: look for a tool matching `*outlook_email*` or `*email_search*`
- Calendar: look for a tool matching `*outlook_calendar*` or `*calendar_search*`
- Chat: look for a tool matching `*chat_message*` or `*teams*`

If NO Microsoft 365 tools are found at all, stop and tell the user:
> "To build your Attention Today page I need Microsoft 365 connected. Go to Settings →
> Connectors, connect Microsoft 365, then try again."

## Step 2 — Probe each connected source

Make real tool calls with empty queries to understand the response shape before building.
Fetch up to 20–30 items from each available source. If a call fails or times out, mark
that source as unavailable and continue — do not abort.

## Step 3 — Classify items into priority tiers

| Tier | Email criteria | Calendar criteria | Chat criteria |
|---|---|---|---|
| **Urgent** | importance=high OR subject contains: urgent, action required, approval needed, ASAP, EOD | Starts within 30 min | — |
| **Critical** | Unread from same domain (e.g. @epam.com) | Starts within 2 hours | Direct messages (1:1) |
| **Necessary** | Unread, not above | Later today | @mentions in channels |
| **Good to complete** | Newsletters, digests, FYI mail | — | FYI channel messages |

Assign each item to the highest tier it qualifies for.

## Step 4 — Build and create the artifact

Load the HTML template from `assets/artifact-template.html`. Substitute these placeholders
with the actual MCP tool names discovered in Step 1:

- `__TOOL_EMAIL__` → actual email tool name (or `__UNAVAILABLE__` if not connected)
- `__TOOL_CALENDAR__` → actual calendar tool name (or `__UNAVAILABLE__` if not connected)
- `__TOOL_CHAT__` → actual chat tool name (or `__UNAVAILABLE__` if not connected)
- `__USER_DOMAIN__` → user's email domain (e.g. `epam.com`)
- `__TODAY_DATE__` → today's date in `YYYY-MM-DD` format

Call `create_artifact` with:
- title: "Attention Today"
- the substituted HTML
- mcp_tools: list of all available tool names (omit unavailable ones)

## Step 5 — Confirm

Tell the user: "Your Attention Today page is live in the sidebar. It refreshes every time
you open it or hit Reload — no schedule needed."

Offer: "Want me to set up a morning briefing pushed to chat at a time of your choosing?"

## Graceful degradation rules

- Never fail hard because a connector is missing
- Render "(not connected)" banners for missing sources
- Only hard-stop if ALL Microsoft 365 tools are absent (see Step 1)
