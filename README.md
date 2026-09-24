# Work Schedule Sync — Project Overview (Demo)

> Public overview of a **private** project. This repository is documentation only —
> it contains **no source code, no configuration, and no real data**. The real
> implementation is kept in a private repository.

A **private schedule-automation tool** that turns posted work-schedule text into
calendar events and summary reminders. It is the headless automation engine for
two jobs with different sync strategies — deterministic by design, with no OCR,
no image processing, and no model inference.

## What it does

- Parses posted schedule text and **syncs shifts to a personal calendar**,
  without duplicating events on a re-post.
- Accepts that text over a **token-authenticated endpoint**, so the paste happens
  in the [Nexus](https://github.com/RyanBrin/nexus-demo) operator surface rather
  than in this project's own web page. The original HTML form is retired; the
  automation engine is what remains.
- Runs on **time-based triggers**, so the job that can be read automatically
  stays current with no paste at all.
- Sends **SMS/email summaries** of upcoming shifts on a fixed daily cadence.

## Key features

- Schedule → calendar automation with duplicate-safe writes.
- **Deterministic parsing** — input it does not recognise is rejected rather than
  approximated, so a bad paste fails loudly instead of inventing a shift.
- Shift-summary notifications (ASCII-safe, concise).
- Runs as a lightweight scheduled automation with a token-authenticated bridge
  endpoint.

## Privacy & security posture

- **No personal schedule data, employer/location details, phone numbers, or email
  addresses** are included in this overview.
- Recipients and any credentials live only in private config — never committed,
  never shown publicly.
- The concept (e.g. retail shift sync) is described generically; real schedule
  data is private.

## Technologies

- JavaScript / Google Apps Script (deployed by `clasp`, not by git)
- Google Calendar automation; email/SMS summaries
- Token-authenticated `doPost` bridge consumed by the Nexus platform

## Notes

- The real source code and commit history are **private**.
- Any examples are **sanitized/mock** — no real shifts, dates, locations, or
  contact details.

See [`docs/architecture.md`](docs/architecture.md) for a high-level architecture summary.
