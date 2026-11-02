# Live verification — `selected` / learning-type on the part-01 choice, 2026-11-02

Package `../../deployments/2026-11-02` (commit `939aaa7`). Why: step 6 of the `selected` / learning-type
plan — Arabic twin of `methodica-math-scale-01` (live 02.11.26). Screen 2 already sent `selected`, but with
the card's label as `response`; it now sends the chosen path item's `mediaFormat` (guide
`Documentation/reporting-and-resume/ADDING-REPORTING-AND-RESUME.md` §6.3a), and the s3 / s4 mode toggles
report too.

## CDN upload

All 7 files are **byte-identical** to the package (cache-busted downloads compared with `cmp`):

| File | Bytes |
|---|---|
| `unit-js/20-xapi.js` | 21,482 |
| `-01/script.js` | 123,144 |
| `-01/index.html` | 200,139 |
| `-02/index.html` | 132,195 |
| `-03/index.html` | 22,908 |
| `-04/index.html` | 96,323 |
| `-05/index.html` | 79,725 |

The live metadata `metadata/methodica-ar-math-scale-01-01.json` (27,251 bytes) is unchanged and identical
to the package: 003 `video`, 004 `text` — the values the statement's `response` copies.

## Live part 01 (CDN page, `sendStatement720` captured in the page — nothing sent to Kata)

`https://lomdot.education.gov.il/metodica/720/ar/math/scale/01/methodica-ar-math-scale-01-01/index.html`

- Loads `../unit-js/20-xapi.js?v=9` and `script.js?v=23`; `XAPI_LEARNING_PATHS` = `video` → 003 `video`,
  `cards` → 004 `text`.
- Screen 2: two card clicks → **no** `selected`.
- The continue button on video → s4 and **one** statement: verb `selected`, objectType `onlinelesson` (the
  library uses the component id), `{ category: 'learning-type' }`, `result.response` = **`video`** (was
  the label).
- Back to s2, continue again → nothing (picks ledger).
- s4 cards toggle → s3 and **one** `selected`, `response` = **`text`**.
- s3 video toggle → s4 and nothing (already reported).
- Item statements unchanged: 002 on s2, 003 on s4 (with the YouTube `played` / `paused`), 004 on s3.

## Not checked here

- The statement as stored in Kata — a platform launch (`?slxapi=`) is needed; the platform team checks it
  after our notice (`Documentation/MOE/NOTE-TO-PLATFORM-selected-learning-type-2026-11-02.md`).
- How the platform / bot reads `response` = `mediaFormat` (agreed deviation from v2.7's `contentType`).
