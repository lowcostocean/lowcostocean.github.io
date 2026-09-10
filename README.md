# Workshop on Low-Cost Ocean Instrumentation — Website

**Live at <https://lowcostocean.github.io/>**

Public website for the Workshop on Low-Cost Ocean Instrumentation, hosted at Woods Hole
Oceanographic Institution, October 19–22, 2026 (optional hands-on development session
October 23 & 26–28, 2026).

Plain static HTML/CSS — no build step, no framework, no dependencies. Meant to be easy to
hand-edit as details (speakers, agenda, logistics) firm up.

## Making a change

Edit the files and push. GitHub Pages rebuilds automatically and the change is live in 1–2 minutes.

```
git add -A && git commit -m "..." && git push
```

The remote is SSH (`git@github.com:lowcostocean/lowcostocean.github.io.git`), authenticated with
the maintainer's SSH key.

## Structure

- `index.html` — the whole site: one page, anchor-linked sections
  (Overview · Dates & Venue · Registration · Agenda · Workshop Themes · Funders · Contact)
- `assets/css/style.css` — all styling; the palette and content width are CSS custom properties
  at the top of the file
- `assets/img/whoi-logo.png` — WHOI logo (banner)
- `assets/img/schmidt-sciences-logo.svg`, `assets/img/onr-logo.png` — funder logos, used twice:
  stacked in the banner's right margin at ≥1240px wide (they fall back to a row under the title
  on narrower screens) and again at full size in the Funders section
- `agenda/` — latest agenda PDF, linked directly from the Agenda section rather than transcribed
  into HTML, so it can be swapped out as new drafts are released

All internal links are **relative** (`assets/…`, `agenda/…`) with no hardcoded `github.io` URLs,
so the site works unchanged at a root URL, at a repo path, or under a custom domain. Keep it that way.

### Layout notes worth knowing before editing CSS

- The content column is capped at 860px (`--max-width`).
- The **1240px** breakpoint for the banner's margin logos is where the space outside that 860px
  column first becomes wide enough to hold a logo plate without colliding with the title. Lowering
  it causes overlap.
- Banner logos sit on **white plates** because the WHOI and Schmidt wordmarks are both
  dark-on-transparent and disappear against the navy header. The plates are a fixed height with
  independently sized images — the Schmidt wordmark is wide and light while the ONR seal is a dense
  round mark, so at equal heights Schmidt looks shrunken.
- Reusable classes: `.button` (navy CTA, used by Agenda and Registration), `.note` (light panel
  with a blue left border), `.card`, `.logo-plate`.

## Updating the agenda

Drop the new PDF into `agenda/` and update the `href` in the Agenda section of `index.html`
to point to it — or just overwrite the existing filename to avoid touching the HTML at all.

## Registration links

The Registration section links two Google Forms:

- **Form 1 — general registration:** https://forms.gle/Mz2xuPREwdM4qZj18 (the main button)
- **Form 2 — foreign visitor information:** https://forms.gle/gMFsmdZwWJoPTxA79 (the `.note`
  callout below it, for non-U.S. participants; also surfaced on Form 1's confirmation screen)

To take Form 2 off the public page, delete that `.note` paragraph.

## Hosting

Deployed as the **root site of the `lowcostocean` GitHub organization**, which is why it lives at
`https://lowcostocean.github.io/` with no repo name in the path. This depends on the repo being
named **exactly** `lowcostocean.github.io` — renaming it moves the site to
`lowcostocean.github.io/<repo-name>/` and breaks the URL.

Pages is configured as **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.

A custom domain was considered and deliberately declined; the `github.io` URL is the intended
permanent address.

## Known open items (not yet decided by the organizer)

- **Registration deadline / capacity:** no deadline or cap is stated on the page. Google Forms
  enforces neither automatically — responses have to be closed manually when registration should
  end. Add the date to the Registration section once decided.
- **Funder acknowledgment wording:** currently generic ("made possible with generous support
  from Schmidt Sciences and the U.S. Office of Naval Research"), with both funders' logos shown
  beneath it. Confirm neither funder has specific required acknowledgment wording or logo-usage
  requirements before treating this as final.
- **Speakers / program section:** none exists yet; add if and when the agenda firms up.
