# jamesanne.com

Source for jamesanne.com, Anne James's site for startups and AI teams:
growth strategy, Fractional CMO work and AI governance.

Plain static HTML/CSS, with no build step, no framework and no third-party
requests. Hosted on statichost.eu.

All rights reserved. This repository has no licence, so the text, images and
code can't be reused, even though the repo is public.

---

## Structure

```
/                    index, services-growth, services-ai-governance,
                     experience, about, contact, privacy, cookies
                     404.html: served by the host for any missing page
/css/styles.css      shared stylesheet
/js/site.js          mobile nav, dropdowns, service tabs, email links
/fonts/              self-hosted Newsreader + Inclusive Sans, with OFL licences
/images/             WebP in several widths; share-default.jpg is 1200×630
robots.txt, sitemap.xml
statichost.yml       publish the repo root as-is
```

## House rules

- **No third parties on the page.** No analytics, embeds, tracking pixels or
  outside fonts or scripts. LinkedIn and Calendly are plain links only. If
  that ever changes, update the privacy and cookies pages first.
- **Outside links open in a new tab** with `target="_blank" rel="noopener"`
  and a screen-reader "(opens in a new tab)" note.
- **Service pages:** Founding Marketer (`services-growth.html`) and AI
  Governance (`services-ai-governance.html`). Keep card ids unique across both
  pages so deep links stay unambiguous.
- **Service tabs:** deep links work, e.g. `services-ai-governance.html#policies`.
  With JavaScript off, all cards show stacked.
- **Image credits.** Feature photos carry a visible credit. Decorative images
  on the service pages have no credit and `alt=""`. Before adding an
  uncredited image, check that its licence doesn't require attribution.
- **Share images** are 1200×630 JPGs. Pages without their own use
  `images/share-default.jpg`. Spanish and Portuguese pages use the
  `-es` / `-pt` versions, which are the English images with the headline
  and subtitle re-set in the site fonts.
- **Sitemap.** Add every new public page to `sitemap.xml`.
- **404 page.** It can be served at any depth, so every link and asset in
  `404.html` uses a root-absolute path (`/css/styles.css`, not
  `css/styles.css`).
- **Fonts.** Newsreader 600 (headings) and Inclusive Sans 400–700 plus italic
  400 (body), subset to Latin plus the characters the pages use. If new text
  adds unusual characters, rebuild the font files from the originals.

## Design and accessibility

- **Colour:** an off-white base, near-black text, plum (`--plum`) as the
  single bold colour, and vermilion (`--spark`) for small marks only, never
  text. The tokens are at the top of `styles.css`.
- **Type:** 19px base size with generous line height, for comfortable reading
  on a phone.
- **Keyboard and focus:** visible focus rings, a skip-to-content link on every
  page, and menus that work with the keyboard and Escape.
- **Motion:** `prefers-reduced-motion` is respected.
- **Page weight:** WebP images in multiple sizes with `loading="lazy"`, and no
  frameworks.
