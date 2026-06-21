# Architecture (high level)

> Sanitized overview only. No source, no config, no real data.

## Components

- **Schedule source** — a personal work schedule (input; kept private).
- **Sync automation** — parses the schedule and creates/updates calendar events.
- **Notifier (optional)** — sends concise shift summaries via email/SMS (opt-in).

## Flow

```
personal schedule ──> sync automation ──> personal calendar (events)
                              │
                              └──(opt-in)──> summary email / SMS
```

## Principles

- **Personal use** — operates on one person's private schedule.
- **No secrets in code** — recipients and credentials in private config only.
- **Concise, ASCII-safe** summaries for SMS.

## Boundaries

- No personal schedule data, employer/location details, recipients, or
  credentials in this repo.
- Real implementation and history remain private.
