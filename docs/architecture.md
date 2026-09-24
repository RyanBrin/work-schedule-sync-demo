# Architecture (high level)

> Sanitized overview only. No source, no config, no real data.

## Components

- **Schedule sources** — two jobs, handled differently: one is posted as text,
  the other is read automatically on a timer. Both inputs are private.
- **Bridge endpoint** — a token-authenticated `doPost` that accepts the posted
  text from the Nexus operator surface. The project's original HTML form is
  retired and no longer served.
- **Parser** — deterministic. No OCR, no image processing, no model inference;
  input it does not recognise is rejected rather than approximated.
- **Sync automation** — creates and updates calendar events, duplicate-safe on a
  re-post.
- **Notifier** — sends concise shift summaries via email/SMS on a fixed daily
  cadence.

## Flow

```
posted schedule text ──(token-authed bridge)──┐
                                              ├──> parser ──> sync ──> personal calendar
timed read of the other job ──────────────────┘                 │
                                                                └──> summary email / SMS
```

## Principles

- **Personal use** — operates on one person's private schedule.
- **Deterministic over clever** — a bad paste fails loudly instead of inventing a
  shift.
- **No secrets in code** — the bridge token, recipients, and calendar identifiers
  live in private config only.
- **Concise, ASCII-safe** summaries for SMS.

## Boundaries

- No personal schedule data, employer/location details, recipients, or
  credentials in this repo.
- Real implementation and history remain private.
