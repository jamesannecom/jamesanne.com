# jamesanne.com

Anne James's consulting site for tech companies, from startups to enterprises:
strategy and strategic insight, fractional CMO leadership, and AI governance.
It's a sister site to annejames.io, which covers museums and tourism, and uses
the same design, fonts and script. Plain static HTML/CSS, with no build step,
no framework and no third-party requests.

Code lives on GitHub (account: jamesacom@proton.me). Hosting is on
statichost.eu (Sweden, EU-only infrastructure, no visitor IP logging). DNS
stays at GoDaddy until the domain moves to Infomaniak.

All rights reserved. This repository has no licence, so the copy can't be
reused, even though the repo is public.

---

## Launch checklist

### 1. GitHub
- [ ] Sign in to GitHub as jamesacom@proton.me and turn on two-factor
      authentication
- [ ] New repository: `jamesanne-site`, **Public**, no README, no licence
- [ ] "uploading an existing file": drag in everything in this folder
      (including `css/`, `fonts/`, `images/`, `js/` and `statichost.yml`),
      then Commit

### 2. statichost.eu
- [ ] New site named `jamesanne`. Repository: the repo's HTTPS URL
      (`https://github.com/<username>/jamesanne-site.git`). Leave the build
      command empty. `statichost.yml` already says to publish the repo root
- [ ] Check the site at `jamesanne.statichost.page`
- [ ] GitHub → repo → Settings → Webhooks → Add webhook:
      `https://builder.statichost.eu/jamesanne`, content type
      `application/json`, "Just the push event"
- [ ] statichost → site → Settings → Domains: add `jamesanne.com` and
      `www.jamesanne.com`
- [ ] Ask statichost (hello@statichost.eu) about running two sites
      (annejames.io and this one) on the free plan

### 3. GoDaddy DNS (My Products → jamesanne.com → DNS)
- [ ] Delete GoDaddy's "Parked" A record for `@` and the existing `www` CNAME
- [ ] Add: A `@` → `95.217.26.94`; AAAA `@` → `2a01:4f9:c01f:8002::`;
      CNAME `www` → `jamesanne.statichost.page`
- [ ] Check `https://jamesanne.com` and `https://www.jamesanne.com` both show
      a Let's Encrypt certificate
- [ ] Don't touch any MX/TXT records (email)

### 4. Before telling anyone about it
- [ ] Read every page and correct the service details: durations,
      participants, deliverables and program steps are drafts
- [x] Email: buttons and email links use jamesacom@proton.me (stored
      reversed in `data-u` / `data-d` on `.js-email` links). Change it
      everywhere if you set up a jamesanne.com address
- [ ] Privacy and Cookies pages: synced with annejames.io on 19 October 2026
      (retention periods, meetergo/kMeet details). The Privacy page says this
      site's email is on Proton and the booking calendar and kMeet are on
      Infomaniak: check that's right, and update "Last updated" if you change
      anything
- [ ] Photos are reused from annejames.io. The home page ones have no visible
      credit yet (see the TODO comments in `index.html`). Replace any that
      look too much like a museum or community workshop
- [x] Testimonials: Jean Massad's and Jillian Hufnagel's approved quote are
      live, side by side (`testimonials--pair`), as on annejames.io
- [ ] Preview the share image in LinkedIn Post Inspector
      (linkedin.com/post-inspector)

### 5. Later
- [ ] Move the domain to Infomaniak in July–August 2027, before the
      15 September 2027 renewal (turn off GoDaddy auto-renew first)
- [ ] Projects / case studies for tech clients (the page layout is in the
      annejames.io repo: `projects.html`, `case-studies/`)
- [ ] Blog: "Writing" links straight to Substack for now. The blog layout from
      annejames.io can be copied over when there are tech-focused posts
- [ ] Spanish and Portuguese versions, plus the language switcher. `site.js`
      already has the ES/PT interface text; follow the annejames.io pattern
      (hreflang tags on every page, and in `sitemap.xml`)
- [x] A custom 404 page, `robots.txt` and `sitemap.xml`

---

## Structure

```
/                    index, services-growth, services-ai-governance,
                     about, contact, privacy, cookies
                     404.html: served by statichost for any missing page
/css/styles.css      shared stylesheet (same as annejames.io)
/js/site.js          mobile nav, dropdowns, service tabs, email address
                     (same as annejames.io)
/fonts/              self-hosted Newsreader + Inclusive Sans, with OFL licences
/images/             WebP in several widths; share-default.jpg is 1200×630
robots.txt, sitemap.xml
statichost.yml       publish the repo root as-is
```

`styles.css` and `site.js` are kept identical to annejames.io, so a fix on
one site can be copied straight to the other.

## House rules (same as annejames.io)

- **No third parties on the page.** No analytics, embeds, tracking pixels or
  outside fonts or scripts. Substack, LinkedIn and meetergo are plain links
  only. If that ever changes, update the privacy and cookies pages first.
- **Email address** never appears in the HTML. `site.js` assembles it from
  reversed parts on `.js-email` links.
- **Outside links open in a new tab** with `target="_blank" rel="noopener"`
  and a screen-reader "(opens in a new tab)" note.
- **Strategy comes before AI governance** in titles and copy.
- **Services by practice:** two service pages, Strategic Growth
  (`services-growth.html`) and AI Governance (`services-ai-governance.html`).
  Keep card ids unique across both pages so deep links stay unambiguous.
- **Service tabs:** each service page has tab groups and cards. Deep links
  work, e.g. `services-ai-governance.html#skills`. With JavaScript off, all
  cards show stacked.
- **Image credits.** Feature photos (home page, case studies) carry a
  visible credit (e.g. "Photo: … / Unsplash"). The decorative images on the
  services pages have no credit and `alt=""`. Before adding an uncredited
  image, check that its licence doesn't require attribution. Unsplash's
  licence doesn't; Creative Commons BY licences do.
- **Share images** are 1200×630 JPGs. Pages without their own use
  `images/share-default.jpg`.
- **Sitemap.** Add every new public page to `sitemap.xml`.
- **404 page.** It can be served at any depth, so every link and asset in
  `404.html` uses a root-absolute path (`/css/styles.css`, not
  `css/styles.css`).
- **Fonts.** Newsreader 600 (headings, variable optical size) and Inclusive
  Sans 400–700 plus italic 400 (body). They're subset to Latin plus the
  characters the pages use. If new text adds unusual characters (e.g. Polish
  or Greek), rebuild the font files from the originals.

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
