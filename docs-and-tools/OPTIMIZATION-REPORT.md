# Image re-encode — 2026-11-10

Same change as the Hebrew twin (`methodica-math-scale-01` `eb0921e`), per
`Documentation/reporting-and-resume/BOOT-AND-RESUME-HARDENING-2026-11-03.md` §2.4. Tool
`docs-and-tools/reencode-media.py` (identical to the Hebrew twin's), boxes in `media-display-boxes.json`, one row per
file in `reencode-rows.md`.

| | Before | After |
|---|---|---|
| Files re-encoded | 40 (all parts) | 40, every one renamed `<stem>-opt.<ext>`, references rewritten |
| Bytes | 42,874,041 | 10,994,025 |

- **Boxes** measured in Chrome on both twins (every screen, every zoom panel, object-fit applied); the `_ar` images
  sit in the same elements as the Hebrew ones and get their fitted size from their own pixels.
- **Type kept.** The Arabic text-bearing images are PNG (`*_ar.png`) and stay PNG: quantized to 256 colours where
  libimagequant reaches quality 70, otherwise 24-bit (`Gaming Festival_ar.png`, 2.0 MB: the banding guard).
- **Not touched:** `Character1.png` / `Character2.png` (built at runtime as `char + '.png'`), the two unreferenced,
  never-shipped files, files under 100 KB, SVGs, `unit-assets/`, part 05's two `VID Happy.mp4` end clips.
- **Runtime-built names** carry `-opt` by hand (01 / 05 `preloadImages`, 05 s43); `PRELOAD_VARIANTS` in
  `_test/verify-report.js` checks them. `package-allowlist.ps1` names part 04's two unreferenced workout poses by
  their `-opt` names so they still do not ship.
- **Visual pass** (Chrome, both characters): every image of every screen loads (`naturalWidth > 0`, no 4xx); the map
  zoom and part 05 images inspected: Arabic labels sharp, no banding.
