# Live verification — item split in part 01, 2026-10-27

Package `../../deployments/2026-10-27` (commit `4287795`). Why: `QA/2026-10-26` — the bot answered about
the learning path the learner had not chosen; same change as the Hebrew twin `methodica-math-scale-01`
(002 the choice, 003 video, 004 cards, old 003–009 → 005–011).

## CDN upload

All 3 files are **byte-identical** to the package (cache-busted downloads compared with `cmp`):
`metadata/methodica-ar-math-scale-01-01.json` 27,251 · `-01/index.html` 200,119 · `-01/script.js` 123,273.

## KATA send — Arabic component 01 only, parent unit read-only

`send-metadata.ps1 -MetadataDir <unit json + component 01 json>` (parent-unit mode, key from
`KATA_API_KEY`).

    Parent unit : methodica-math-scale-01 (read-only, not modified)
    UPDATED component 01, items 001–009 (HTTP 200)
    CREATED items 010, 011 (HTTP 201)
    Done. created=2 updated=10 failed=0

## Read back (raw `GET /api/v1/content-units/methodica-math-scale-01`)

Before: `../../deployments/kata-snapshots/2026-10-27-before-split/_raw-content-unit.json`; after:
`../../deployments/kata-snapshots/2026-10-27-after-split-raw-content-unit.json`.

- **Hebrew unit record unchanged** (title `ar` / `he` / `Hebrew` intact).
- **The other 9 components unchanged** (the 5 Hebrew ones and Arabic 02–05). Still 10 components — no
  second Arabic component was created (no `720active` Arabic key).
- **Arabic component 01**: `published`, "هيا نتعلم شيئاً جديداً", `estimatedTimeInMinutes` 24, 11 items;
  every item matches `metadata/` (title, informationToBot, contentType, mediaFormat, questions). 002 has
  no questions — the empty-list fix in the sender worked on the first send.

## Not checked here

- The bot's answers on each path — the platform team checks that after our notice.
- A live xAPI run inside KATA — covered locally by `verify-report.js`, `statement-flow.js` and the browser
  walk of both paths.
