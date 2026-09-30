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

The plugin's installation and private-use rights are in `LICENSE`. Its bundled Swift
dependencies and their original license texts are in `THIRD_PARTY_NOTICES/`.
