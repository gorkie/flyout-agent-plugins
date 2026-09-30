# Flyout plugins for Codex, Claude Code and Claude Desktop

Let your AI client search, read and create notes in [Flyout](https://getflyout.app/), and set
reminders, through the Flyout app running on your Mac. Nothing leaves your Mac through Flyout's
servers. Access is off until you turn it on in Flyout and approve the connection there.

Requirements: macOS 14 or later, Flyout 1.5.8 or later (license or trial), and one of the
clients below.

## Install

Codex:

```sh
codex plugin marketplace add gorkie/flyout-agent-plugins
codex plugin add flyout-notes@flyout-agents
```

Claude Code:

```sh
claude plugin marketplace add gorkie/flyout-agent-plugins
claude plugin install flyout-notes@flyout-agents
```

Claude Desktop: download
[`claude-desktop/Flyout-Claude-Desktop-0.1.0.mcpb`](claude-desktop/Flyout-Claude-Desktop-0.1.0.mcpb)
and install it from Settings → Extensions → Advanced settings → Install Extension.

## Connect to Flyout

Installing a plugin does not give it access to your notes. In Flyout, open Settings → Agent
Access, turn on **Allow agent access** and click **Add connection**. Choose your client, its
permissions (read, create, reminders, delete requests) and whether it can use all notes or only
selected folders. When Flyout asks for the connection file, pick the signed helper that the
client installed:

| Client | Connection file |
|---|---|
| Codex | `~/.codex/plugins/cache/flyout-agents/flyout-notes/0.1.0/bin/FlyoutAgentHost` |
| Claude Code | `~/.claude/plugins/cache/flyout-agents/flyout-notes/0.1.0/bin/apple-silicon/FlyoutAgentHost` (Apple silicon) or `…/bin/intel/FlyoutAgentHost` (Intel) |
| Claude Desktop | `server/FlyoutAgentHost` inside the Flyout extension folder in `~/Library/Application Support/Claude/Claude Extensions/` |

Press ⌘⇧. in the file dialog to show hidden folders. Then approve the pairing prompt. Locked notes are never available. A delete request only opens a confirmation in
Flyout; the AI client cannot confirm it.

Note content returned to the client is available to that client and its model provider, under
their terms.

## Remove

Revoke the connection in Flyout first. Removing a plugin does not revoke it.

```sh
codex plugin remove flyout-notes@flyout-agents
codex plugin marketplace remove flyout-agents
claude plugin uninstall flyout-notes@flyout-agents
claude plugin marketplace remove flyout-agents
```

In Claude Desktop, uninstall the extension from Settings → Extensions.

## What's in this repository

| Path | Contents |
|---|---|
| `.agents/plugins/marketplace.json` | Codex marketplace catalog |
| `.claude-plugin/marketplace.json` | Claude Code marketplace catalog |
| `plugins/codex/flyout-notes/` | Codex plugin: skills, MCP config, universal helper |
| `plugins/claude-code/flyout-notes/` | Claude Code plugin: skills, MCP config, per-architecture helpers (`bin/apple-silicon`, `bin/intel`) and the `bin/flyout-mcp` launcher |
| `claude-desktop/` | Claude Desktop extension (`.mcpb`) |
| `package-report.json` | Helper hashes and Apple notarization job |

The helper (`FlyoutAgentHost`) is a local MCP stdio server, signed with Developer ID
(team 4F9YKYL69Q) and notarized by Apple. It talks to the Flyout app over an encrypted local
connection and never opens the note database itself.

Support: hello@getflyout.app · [Privacy](https://getflyout.app/privacy) ·
[Terms](https://getflyout.app/terms). Published by Depfloy LLC; see `LICENSE`.
