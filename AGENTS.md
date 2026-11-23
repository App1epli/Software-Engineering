# Agent instructions — Smart Campus Room Availability Checker

## Purpose and boundaries
This is the fictional, single-day Smart Campus Room Availability Checker from Software Engineering Assignment #04. The app checks whether a room is available; it must never create, edit, or delete bookings. Follow these instructions when contributing to Assignment #05.

## Architecture map
- `src/App.tsx`: top-level React form and state orchestration.
- `src/components/`: UI views and controls.
- `src/lib/types.ts`, `src/lib/data.ts`: domain model and fictional room/booking data.
- `src/lib/availability.ts`: booking availability and time validation rules.
- `src/lib/filterRooms.ts`: room capacity/equipment filtering.
- `src/lib/time.ts`: parsing/formatting/default time intervals.
- `tests/`: unit and React integration tests.
- `verification/`: Assignment #04 before/after comparison suite; this may require a separately provided original source.

## Environment and safe commands
Use Node.js 24 with npm. Inspect changes before executing commands.
```sh
npm ci
npm test
npm run typecheck
npm run typecheck:tests
npm run lint
npm run build
```
Only use `npm run dev` to inspect the local app. No real production or external services are needed for this fictional project.

## Invariants and acceptance criteria
1. Requests with start >= end, start in the past relative to simulated current time, or durations over 120 minutes are rejected.
2. Blocked rooms must never be returned as available.
3. Intervals overlapping existing bookings are unavailable; intervals touching endpoints without overlap are allowed.
4. Availability checks are read-only and never modify bookings.
5. Capacity and equipment filters remain inclusive for capacity and require all selected equipment; a room switch invalidates a stale result.

## Code conventions and change scope
- Prefer small and focused edits. Keep time/room rules in `src/lib` rather than duplicating business logic in UI components.
- Preserve TypeScript types, existing behavior, and consistent import/style conventions.
- Write or update targeted unit/integration tests for changed behavior.
- For Assignment #05, at most one focused architecture/design-pattern refactoring; do not introduce a pattern without a clear maintenance reason.
- Make changes on a separate branch and submit a human-reviewable diff.

## Prohibited operations
- Do not read, reveal, commit, or upload credentials, `.env` files, personal data, or sensitive tokens.
- Do not deploy to production or connect to live booking databases.
- Do not run destructive commands such as `rm -rf`, `git reset --hard`, or force-push.
- Do not add/update dependencies or modify lockfiles without specific human approval.
- Do not rewrite unrelated files, bypass failing tests, invent test results, or merge changes without human review.

## Review and completion gate
Before requesting approval: show `git diff`, identify files changed, list commands with exact exit statuses and test counts, and explain remaining risks. If a command cannot run, mark it **NOT RUN** with the reason. Human approval is mandatory before merge or deployment.
