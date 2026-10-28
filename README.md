# The Coffeehouse Lab

Independent, data-led analysis of British politics and policy, and what the evidence means for decisions. Plain HTML, CSS and JavaScript with no build step. Everything the site serves is in `public/`.

```
public/index.html                       Front page: the lead story and its number to take away
public/about/index.html                 About: independence, funding, how we check, corrections
public/corrections/index.html           Every correction, dated
public/data/index.html                  The data hub: one card per story
public/stories/<slug>/index.html        The story
public/stories/<slug>/data.html         Its data page: downloads, sources, definitions, checks
public/stories/<slug>/img/, data/       The story's photos, charts, CSVs, check workbook and R notebook
public/css/site.css                     Shared styles (story pages carry their own)
public/images/brand/                    Logo and icons
public/404.html                         Not-found page
wrangler.jsonc                          Cloudflare config: serve public/ as static assets
```

## Publishing

Deployed by Cloudflare Workers Builds, connected to this repository. Every push to `main` goes live, so changes go through a branch and pull request, and merge only on BDF's go-ahead. Other branches get their own preview URL, as long as Preview URLs are switched on in Cloudflare (Workers & Pages > the-politics-lab > Settings > Domains & Routes). Builds of `main` fail until the site is merged there, because `main` holds only a README.

Every page carries the cookie-free Cloudflare Web Analytics beacon just before `</body>`. Before the first deploy, replace `CF_BEACON_TOKEN` with the site's token from Cloudflare > Web Analytics; `grep -r CF_BEACON_TOKEN public` must print nothing.

## Adding a story

1. Add the story under `public/stories/<slug>/` (story page, `data.html`, `img/`, `data/`).
2. Add a card to the data hub (`public/data/index.html`).
3. Update the front page lead (and move the previous lead into a "More stories" row).
4. Log every new image in `CREDITS.md`.
5. Add the analytics beacon line before `</body>` on every new page.
