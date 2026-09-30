---
name: flyout-reminders
description: Read and create reminders stored by the paired local Flyout app.
---

Use Flyout reminder tools only when the user asks to inspect or set a Flyout reminder.

- Check flyout_ping before making a request.
- A reminder linked to a note or quick page requires that target to be accessible to this client.
- Confirm an ambiguous date or local time zone with the user. Send an RFC 3339 due_at value and
  its matching IANA timezone; do not infer a repeat rule.
- Keep reminder label content limited to what the user requested.
- Report the stored reminder result separately from notification permission or delivery. A
  saved reminder does not prove that macOS displayed a notification.
- Retry creation only with the same request_id UUID and exactly the same request fields.
- For an error code such as `PAIRING_REQUIRED` or `ACCESS_DISABLED`, give the user the matching
  step from the flyout-notes skill instead of guessing.

The current MCP contract is recorded in contract/tools-v1.json.
