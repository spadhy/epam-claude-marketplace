---
description: >
  Generate a weekly team progress digest. Trigger when the user asks for a "team progress
  report", "weekly digest", "what did the team complete this week", "sprint summary",
  "what's blocked on my team", or any request for a structured view of team activity
  across Jira, email, or calendar.
---

# Skill: team-progress

## Purpose
Produce a structured weekly digest showing completions, blockers, and upcoming deadlines
for the user's team, pulling from connected project management and communication tools.

## Steps

### 1. Determine time window
Default: current calendar week (Monday to today). If the user specifies a different period,
use that.

### 2. Gather data
Pull from available connectors:
- **Jira / Atlassian Rovo**: tickets resolved, in-progress, and blocked this week
- **Outlook email**: team update threads, status emails, escalations
- **Outlook calendar**: team meetings, deadlines, milestone events

If a connector is not present, note it as unavailable and continue.

### 3. Produce the digest

Structure the output as:

**✅ Completed this week**
List resolved tickets / shipped items with owner and date.

**🚧 In progress**
List active work items with owner and expected completion.

**🔴 Blocked / needs attention**
List anything stalled with blocker reason and who can unblock.

**📅 Coming up next week**
List upcoming deadlines, milestones, and planned work.

**💡 Observations**
1–2 sentences of synthesis: are we on track? Is there a pattern in the blockers?

### 4. Offer a saved artifact
Ask: "Want me to save this as a live digest you can re-open each week?"

## Graceful degradation
If no project management tool is connected, produce the digest from email and calendar
signals alone and note which sources were used.
