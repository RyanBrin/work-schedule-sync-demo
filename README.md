# Work Schedule Sync — Project Overview (Demo)

> Public overview of a **private** project. This repository is documentation only:
> it contains **no source code, configuration, credentials, or real schedule data**.

Work Schedule Sync is a deterministic automation engine that converts posted schedule
text and calendar-feed updates into duplicate-safe calendar events and concise status
notifications. Its visual entry point lives in Nexus; the automation continues to run as
a headless Google Apps Script service.

## What it does

- Parses supported schedule text and rejects unrecognized input instead of guessing.
- Accepts text through a token-authenticated bridge used by the Nexus operator surface.
- Imports a separate calendar source on time-based triggers.
- Creates or updates calendar events without duplicating existing shifts.
- Reports overlaps without deleting, merging, or silently changing either event.
- Rechecks saved source text during automatic syncs and flags stale entries.

## Notification delivery

Sync results are delivered by email and through a short-message channel governed by a
stored notification policy:

1. Telegram Bot API is the preferred short-message transport when configured.
2. Twilio SMS is used when Telegram is not configured and Twilio is configured.
3. Legacy carrier email-to-SMS gateway settings are intentionally ignored because that
   transport is no longer reliable.

Quiet, unchanged runs are suppressed except for the scheduled heartbeat, while conflicts
and meaningful changes remain visible. Credentials and recipient identifiers stay in
private Script Properties and are never logged or committed.

## Architecture

```text
Nexus operator surface -> authenticated Apps Script bridge -> deterministic parser
                                                            -> calendar reconciliation
Scheduled source check -------------------------------------^          |
                                                                       +-> email
                                                                       +-> Telegram / Twilio
```

## Technologies

- JavaScript on Google Apps Script, deployed with `clasp`
- Google Calendar and time-based triggers
- Telegram Bot API with Twilio SMS fallback
- Token-authenticated `doPost` bridge consumed by Nexus

## Privacy and security posture

- No employer, location, shift, recipient, phone, email, or calendar identifiers are
  included in this repository.
- Parsing is deterministic; no OCR, image processing, or model inference is used.
- Notification and bridge credentials live only in private configuration.
- Any examples are sanitized or synthetic.

See [`docs/architecture.md`](docs/architecture.md) for a high-level architecture summary.
