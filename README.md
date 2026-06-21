# Work Schedule Sync — Project Overview (Demo)

> Public overview of a **private** project. This repository is documentation only —
> it contains **no source code, no configuration, and no real data**. The real
> implementation is kept in a private repository.

A **private schedule-automation tool** that turns a personal work schedule into
calendar events and optional summary reminders.

## What it does

- Reads a personal work schedule and **syncs shifts to a personal calendar**.
- Automates calendar entries so the schedule stays current without manual entry.
- Sends optional **SMS/email summaries** of upcoming shifts (opt-in).

## Key features

- Schedule → calendar automation.
- Optional shift-summary notifications (ASCII-safe, concise).
- Runs as a lightweight scheduled automation.

## Privacy & security posture

- **No personal schedule data, employer/location details, phone numbers, or email
  addresses** are included in this overview.
- Recipients and any credentials live only in private config — never committed,
  never shown publicly.
- The concept (e.g. retail shift sync) is described generically; real schedule
  data is private.

## Technologies

- JavaScript / Google Apps Script
- Google Calendar automation; optional email/SMS summaries

## Notes

- The real source code and commit history are **private**.
- Any examples are **sanitized/mock** — no real shifts, dates, locations, or
  contact details.

See [`docs/architecture.md`](docs/architecture.md) for a high-level architecture summary.
