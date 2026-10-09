# Portable URL architecture

## Configuration
- `SITE_URL`: absolute currently deployed site origin and optional project base (canonical and sitemap).
- `BASE_PATH`: normalized path prefix for GitHub Pages project deployments, `/` for a custom domain.
- No hard-coded root domain. Candidate hosts are `fortune.evococoons.com` and `fortune.prince-in-wonderworld.com`; neither is activated.

## Proposed routes
- `/`, `/dreams/`, `/dreams/flying/`, `/saju/`, `/fortune/yearly/`, `/fortune/tojeong/`, `/lotto/`, `/lotto/draw/1/`, `/lotto/statistics/`, `/embed/`.
- Stable English lowercase slugs separated by hyphens. Preserve previously published URLs through aliases and a tested legacy map.
- For GitHub Pages, generate `path/index.html` files to guarantee deep links and refresh. Use data-driven templates; never depend on `history.pushState` alone.
- Generate sitemap, robots, unique title, description and canonical from `SITE_URL`. Do not canonicalize to an unconfigured future domain.
- Historical draw pages require verified official data. Do not fabricate draw records.
- Personal birth-derived result pages must be noindex and should avoid storing birth data.
- Existing query URLs and iframe links must remain functional if later introduced.

## Pilot acceptance criteria
- Deep link and refresh return HTTP 200.
- All internal links work with both `/` and repository base paths.
- Canonical and sitemap agree on deployed origin; no thin duplicate pages.
- Source and public builds remain separated; build time and deployment limits measured.

## Future DNS plan (not active)
- Verify ownership and chosen domain; configure host-specific DNS records and Pages custom domain only after approval.
- Update SITE_URL, verify HTTPS, canonical, sitemap, and redirects or legacy compatibility before cutover.
