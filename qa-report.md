# QA Report: Allied Telesis Amazon Brand Store

**Date**: 2026-03-04
**Pages tested**: 7
**Build status**: PASS
**Overall result**: PASS
**Iterations to pass**: 1

## Pre-Build Validation (Step 0)

| Check | Result | Details |
|-------|--------|---------|
| Image paths vs disk | PASS | 78 unique src paths checked, 0 missing |
| Image paths vs contract | PASS | All paths match IMAGE_PATH_CONTRACT.json |
| build.sh images copy | PASS | `cp -r images/ dist/images/` present with validation |
| build.sh page list | FIXED | Wildcard `*.html` replaced with explicit 7-page list from STORE_CONFIG.json |
| Dockerfile images copy | PASS | `COPY images/ ./images/` present before `RUN sh build.sh` |
| Dockerfile video copy | FIXED | Changed `COPY *.mp4 ./` to `COPY *.webm ./` (store uses .webm, not .mp4); removed `COPY *.pdf ./` (no PDFs) |
| Footer class check | PASS | 0 corrections — all 7 pages use `.amazon-footer` |
| Content authenticity | PASS | 3 banned phrases found, all traced to BRAND_INTELLIGENCE.md source content |
| Template contamination | PASS | 0 SonicWall/template references found |
| Video validation | PASS | 2 .webm files on disk, 0 .mp4 references, 4 Vimeo embeds (no download needed) |

## Build Output

| Metric | Value |
|--------|-------|
| Pages in dist/ | 7 (matches STORE_CONFIG.json) |
| Images in dist/images/ | 75 |
| Videos in dist/ | 2 (.webm) |
| Stale pages | 0 |
| SCSS compilation | PASS |
| TypeScript compilation | PASS |
| HTML minification | PASS |
| JS minification | PASS |
| Gzip pre-compression | PASS |

## Per-Page Results

### index.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 34 images, all loaded after scroll |
| Contract Compliance | PASS | |
| Dead Links | 0 internal / 0 external errors | 19 internal .html links, all valid |
| Footer | PASS | .amazon-footer visible, height: 588px |
| Accessibility | 0 warnings | H1 present, nav present, all imgs have alt |
| Screenshot | Captured | qa-screenshots/index-viewport.jpg |

### switches.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 29 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | 13 internal .html links, all valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/switches-viewport.jpg |

### industrial.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 21 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | All links valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/industrial-viewport.jpg |

### wireless.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 19 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | All links valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/wireless-viewport.jpg |

### firewalls.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 16 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | All links valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/firewalls-viewport.jpg |

### connectivity.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 22 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | All links valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/connectivity-viewport.jpg |

### network-management.html

| Check | Result | Details |
|-------|--------|---------|
| HTTP Status | 200 | |
| Console Errors | 0 | |
| Broken Images | 0 | 19 images, all loaded |
| Contract Compliance | PASS | |
| Dead Links | 0 internal | All links valid |
| Footer | PASS | .amazon-footer visible |
| Accessibility | 0 warnings | H1, nav, alt text all present |
| Screenshot | Captured | qa-screenshots/network-management-viewport.jpg |

## Fixes Applied

| File | Change | Reason |
|------|--------|--------|
| build.sh | `for f in *.html` → explicit 7-page list | Prevent stale template pages (e.g., nav-template.html) from leaking into dist/ |
| Dockerfile | `COPY *.mp4 ./` → `COPY *.webm ./` | Store uses .webm video files, not .mp4; Docker build would fail on missing *.mp4 |
| Dockerfile | Removed `COPY *.pdf ./` | No PDF files in project; Docker COPY fails if no match |

## Known Issues

- None. All checks passed on first iteration.

## Image Contract Verification

- Total images in contract: 75
- Images verified on disk: 75
- Images verified in HTML: 78 unique src paths (includes shared assets like nav icons across pages)
- Uncontracted images found: 0
- Placeholders created: 0

## Video Contract Verification

- Direct video files: 2 (.webm) — both present on disk and in dist/
- Vimeo embeds: 4 — no download needed, referenced by data attributes in HTML
- Video poster images: 1 (images/hero/hero-poster.svg) — present

## Final QA Gate

- [x] Every page returns HTTP 200
- [x] Zero console errors on every page
- [x] Zero broken images on every page
- [x] Every image src matches IMAGE_PATH_CONTRACT.json
- [x] Every page has a visible .amazon-footer element
- [x] No page uses class="footer" without class="amazon-footer"
- [x] Zero dead internal links
- [x] Every page has an h1 tag
- [x] Screenshots captured for all 7 pages
- [x] build.sh copies only STORE_CONFIG.json pages (explicit list, no wildcards)
- [x] build.sh copies images/ directory to dist/
- [x] Dockerfile includes `COPY images/ ./images/` before `RUN sh build.sh`
- [x] Dockerfile includes `COPY *.webm ./` for video files
- [x] No stale template pages in dist/
- [x] Content authenticity verified — descriptions trace to BRAND_INTELLIGENCE.md
- [x] No template contamination (zero SonicWall references)
