# Flyout notes and reminders

Flyout lets you search and read notes you explicitly share with this AI client, create notes
in approved locations, and manage permitted reminders through the local Mac app. macOS 14+
and Flyout 1.5.8 or later are required. A Flyout license or trial is required for the app.

Installing this plugin does not connect it to your notes. Open Flyout, enable Agent access,
add a connection for this client, choose its permissions and whether it can use all notes or
only the folders you select, and approve pairing in the native dialog. Permission to open
Flyout when it is closed is a separate choice. Locked notes remain inaccessible. A deletion request only
starts a native confirmation; the client cannot confirm deletion itself.

The bundled, signed helper runs locally as an MCP stdio server and talks to
Flyout over an encrypted local connection. It does not open the note database. Note content
returned by a tool becomes available to the configured AI client and model. This local
integration does not route note contents through Flyout servers. If iCloud sync is enabled,
Flyout's separate Apple private-database sync still applies. A saved receipt confirms local
persistence, not delivery to another device or notification display.

To stop access, revoke this client's connection in Flyout. Uninstalling the plugin alone
does not revoke the Flyout connection. Support: hello@getflyout.app. Product and policies:
https://getflyout.app/ · https://getflyout.app/privacy · https://getflyout.app/terms.

## Troubleshooting

When a Flyout tool returns an error, the code tells you what to do:

- `PAIRING_REQUIRED` or `CLIENT_REVOKED`: this client has no active connection. In Flyout, open
  Settings › Agent Access, choose Add connection, pick this client and pair it. When Flyout asks for
  the connection file, choose the signed `FlyoutAgentHost` inside this plugin's installed folder:
  `server/apple-silicon/` on Apple silicon Macs, `server/intel/` on Intel Macs (Claude Code),
  `bin/` (Codex). Press ⌘⇧. in the file dialog to show hidden folders.
- `ACCESS_DISABLED`: turn on Allow agent access in Settings › Agent Access.
- `APP_UNAVAILABLE` or `APP_NOT_INSTALLED`: open Flyout. A connection can open Flyout itself only if
  you allowed that when pairing.
- `SCOPE_DENIED` or `NOT_FOUND_OR_NOT_ALLOWED`: the note or action is outside this connection's
  permissions. Change them in Flyout; no new pairing is needed.
- `APP_UPGRADE_REQUIRED`: update Flyout to 1.5.8 or later.

If the Flyout tools do not appear at all, start a new session after installing the plugin; AI
clients load plugin servers when a session starts.

The plugin's installation and private-use rights are in `LICENSE`. Its bundled Swift
dependencies and their original license texts are in `THIRD_PARTY_NOTICES/`.
