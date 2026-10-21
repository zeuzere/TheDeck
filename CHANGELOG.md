# Changelog

## TheDeck 0.3.0 and A2AService 0.1.0 — 2026-10-20

- Added independent TheDeck-A2AService with SQLite retention, registered desktop
  identities, presence and queued requests for offline recipients.
- Added A2A Settings: per-profile connection/name, directory, request composer,
  retained inbox/outbox, manual replies and cancellation. No automatic AI execution.
- Added profile-scoped CLI/MCP commands for autonomous configuration and exchanges.
- Added an experimental A2A 1.0 JSON-RPC subset; the MVP has no authentication,
  streaming or claim of full protocol compliance, and listens on loopback by default.
- Expanded the public README into a self-contained agent installation guide with
  verified binary downloads, silent installation, two profiles and offline exchange.
- Added executable proof using two actual packaged desktops, a real service,
  closed-recipient delivery, replies and service-restart retention.
- TheTasks 1.1.0 and Capture 0.1.2 are included unchanged from delivery 0.2.0.

## TheDeck 0.2.0 — 2026-10-20

Changes since the published TheDeck 0.1.1 release.

### Added

- Task chat dialogs with maximize/restore, Markdown replies and preserved desktop layout.
- Explicit Task agent, provider, model and native MCP tool selection.
- Cooperative terminal requests and bounded reply-triggered Task resumes.
- Task schedules and categorized editable cron presets.
- About forms for reporting bugs and proposing ideas for TheDeck, TheTasks and Capture,
  submitted to TheDeck GitHub Issues with an explicitly selected GitHub account.

### Fixed

- Deleted Tasks no longer cause repeating `task_not_found` errors or stale selection.
- Task alerts are current-session notifications with Dismiss and Dismiss all;
  irrelevant waiting transitions and old read/unread rows no longer fill the list.
- Windows notification objects are retained and reconciled with dismissed alerts.
- An employer repository name was removed from a bundled example comment.

### Distribution

- TheTasks 1.1.0 is a separate standalone Windows executable. See its release notes
  for persistent Codex/Claude sessions and scoped Claude MCP corrections.
- Capture 0.1.2 records its own version in project metadata, and packaging reads
  that version independently of TheDeck. Screenshot behaviour is unchanged.
- Source code remains local; the public repository contains the distribution guide,
  changelog and release binaries only.

## TheTasks 1.1.0 — 2026-10-20

- Each Task continues its own native Codex or Claude session across turns.
- Turns answer the latest user message with bounded prior context and execution counts.
- Claude's explicitly granted MCP tools remain available; missing tools fail the
  execution instead of producing a false successful result.
- Standalone Windows single-file runtime startup is supported without a .NET installation.
- Public CLI/MCP contract remains 12.0. Claude Code 2.1.257 or newer is required
  for refreshing system instructions on resumed sessions.

## TheDeck 0.1.1 — 2026-10-19

- Workspace web tabs, terminal link history and shared Web/Links/Notes pane.
- Group-aware terminal maximize/restore and provider model/effort selection.
- Expanded CLI/MCP desktop controls and loading skeletons.
- Windows installer and standalone Capture 0.1.1.
