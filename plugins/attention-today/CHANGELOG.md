# Changelog – attention-today

All notable changes to this plugin are documented here. Follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and [Semantic Versioning](https://semver.org/).

---

## [0.1.0] – 2026-05-19

### Added
- Initial release
- Live artifact with four priority tiers: Urgent, Critical, Necessary, Good-to-complete
- Outlook email integration (unread mail, importance flags, approval detection)
- Outlook calendar integration (today's meetings with time-to-start awareness)
- Microsoft Teams chat integration (DMs and @mentions)
- Graceful degradation: "(not connected)" banners for missing connectors
- Parameterised artifact template — works with each user's own MCP tool IDs, not hard-coded to the creator's account
- "Open ↗" deep-links into Outlook/Teams from each item card

---

## Planned

### [0.2.0] – Atlassian Rovo / Jira support
- Add a Jira section showing tickets assigned to you, sorted by due date and priority
- Respect Jira priority labels (Blocker → Urgent, Critical → Critical, etc.)

### [0.3.0] – Slack support
- Add a Slack section (pending Slack MCP connector availability)
- Unread DMs → Critical; @channel mentions → Necessary

### [0.4.0] – Configurable priority rules
- Let each user override the default priority classification rules via a simple config block
- E.g. "emails from my manager are always Urgent"

### [1.0.0] – Stable release
- Full test coverage across connector combinations
- Evaluated against 20+ real-user scenarios
- Ready for practice-wide rollout announcement
