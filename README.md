# Workshop on Low-Cost Ocean Instrumentation — Website

Public website for the Workshop on Low-Cost Ocean Instrumentation, hosted at Woods Hole
Oceanographic Institution, October 19–22, 2026 (optional hands-on session October 23 & 26–28, 2026).

Plain static HTML/CSS — no build step, no framework. Meant to be easy to hand-edit as details
(speakers, agenda, logistics) firm up.

## Structure

- `index.html` — the whole site (single page with anchor-linked sections)
- `assets/css/style.css` — styling
- `assets/img/whoi-logo.png` — WHOI logo (site header)
- `assets/img/schmidt-sciences-logo.svg`, `assets/img/onr-logo.png` — funder logos, used twice:
  stacked in the banner's right margin (≥1240px wide; they fall back to a row under the title
  on narrower screens) and again at full size in the Funders section
- `agenda/` — latest agenda PDF, linked directly from the Agenda section rather than
  transcribed into HTML, so it can be swapped out as new drafts are released

## Registration links

The Registration section links two Google Forms:

- **Form 1 — general registration:** https://forms.gle/Mz2xuPREwdM4qZj18 (the main button)
- **Form 2 — foreign visitor information:** https://forms.gle/gMFsmdZwWJoPTxA79 (the note below it,
  for non-U.S. participants; also surfaced on Form 1's confirmation screen)

## Updating the agenda

Drop the new PDF into `agenda/` and update the `href` in the Agenda section of `index.html`
to point to it (or just overwrite the existing filename to avoid touching the HTML at all).

## Deploying with GitHub Pages

This site is deployed as the **root site of the `lowcostocean` GitHub organization**, so it lives at
`https://lowcostocean.github.io/` with no repo name in the path. That requires the repo to be named
**exactly** `lowcostocean.github.io` — any other name serves the site at
`lowcostocean.github.io/<repo-name>/` instead.

1. Create the free org at <https://github.com/organizations/plan> → **Free**, named `lowcostocean`.
2. Inside the org, create a **public** repo named exactly `lowcostocean.github.io`.
3. Point this clone at it and push:
   ```
   git remote set-url origin https://github.com/lowcostocean/lowcostocean.github.io.git
   git push -u origin main
   ```
4. In **Settings → Pages**, set **Source** to "Deploy from a branch," branch `main`, folder
   `/ (root)`. The root URL goes live within a minute or two.

All internal links in `index.html` are relative (`assets/…`, `agenda/…`), so the site works
unchanged at a root URL, at a repo path, or under a custom domain — no edits needed if the URL moves.

### Adding a custom domain later

A `whoi.edu` subdomain (e.g. `lowcost.whoi.edu`) can be layered on top at any time without
disturbing the org setup: add a `CNAME` file to this repo containing the bare domain, have WHOI IT
add a DNS `CNAME` record pointing to `lowcostocean.github.io`, set the domain in
**Settings → Pages → Custom domain**, then enable **Enforce HTTPS** once the certificate issues.
(An apex domain would need four `A` records instead, which is why a subdomain is simpler.)

## Known open items (not yet decided by the organizer)

- **Registration deadline / capacity:** no deadline or cap is stated on the page yet. Google Forms
  enforces neither automatically — responses have to be closed manually when registration should end.
  Add the date to the Registration section once decided.
- **Custom domain:** not yet requested. The plain `https://lowcostocean.github.io/` URL is the
  current plan; a `whoi.edu` subdomain would be shorter and more official (see above).
- **Funder acknowledgment wording:** currently generic ("made possible with generous support
  from Schmidt Sciences and the U.S. Office of Naval Research"), with both funders' logos shown
  beneath it. Confirm neither funder has specific required acknowledgment wording or logo-usage
  requirements before treating this as final.
