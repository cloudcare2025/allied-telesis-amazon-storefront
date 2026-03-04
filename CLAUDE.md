# Allied Telesis Amazon Brand Store

## Quick Reference
- Build: `sh build.sh`
- Dev server: `cd dist && npx serve -p 3000`
- SCSS compile: `npx sass styles.scss styles.css --style=compressed --no-source-map`
- TS compile: `npx tsc`
- Deploy: `railway up --detach --service allied-telesis-amazon-storefront`
- Push: `git push origin main`

## Hosting
- GitHub: https://github.com/cloudcare2025/allied-telesis-amazon-storefront
- Railway project: allied-telesis-amazon-storefront
- Railway service: allied-telesis-amazon-storefront

## Architecture
- SCSS design system: styles.scss
- All JS behavior: script.ts
- Build pipeline: build.sh (SCSS + TS compile, minify, gzip)
- Server: nginx.conf (gzip_static, caching, security headers)
- Container: Dockerfile (node:20-alpine build -> nginx:stable-alpine serve)

## Key Rules
- ALL images must be local (external URLs get ORB-blocked)
- Footer class is `.amazon-footer` (renamed from `.footer` during init; SCSS and script.ts both use `.amazon-footer`)
- Amazon header uses position:relative, brand header becomes sticky via JS
- Never modify Amazon header/footer colors (#131921, #232f3e, #febd69)
- No HTML files were copied from template - ALL pages are generated fresh in Phase 5
- Template reference files are in template-reference/ (gitignored, not deployed)
- Product image subdirectories are created by Phase 4, not pre-created

## Template Reference
- `template-reference/nav-template.html` - Shared nav/header/footer structure
- `template-reference/index-excerpt.html` - Homepage structure (first 200 lines)
- `template-reference/category-page-example.html` - Full category page example
