# Shiba AI website

Static site — plain HTML and one CSS file. No build step, no dependencies.

```
index.html      Home: overview + research topics + recent papers
research.html   All publications
people.html     Members
contact.html    Email, address, joining
css/style.css   All styling for every page
assets/slides/  Slide decks (PDF) linked from research.html
```

## Preview locally

Open `index.html` in a browser, or:

```sh
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Common edits

**Add a paper.** In `research.html`, copy one `<li class="pub">` block, paste it
at the top of the right section (conference/workshop or preprint) and edit the
title, arXiv link, authors, and venue.

**Add slides.** Put the PDF in `assets/slides/` and add a link inside that
paper's `<span class="pub-links">`. There is a commented-out example on the
BIAS workshop paper.

**Add a person.** In `people.html`, add one `<li>` to the right group.

**Change a colour or spacing.** Everything lives in the `:root` variables at the
top of `css/style.css`; dark mode is derived from the same names.

## Outstanding

- Application form URL (`contact.html`).
- Slides PDF for the BIAS workshop paper (`assets/slides/`, then uncomment the
  link in `research.html`).

Dashed boxes on the rendered page mean draft content. None should remain when
the site goes live.

## Staging preview

Live at **https://baileyeet.github.io/shiba-website/** — safe to share for
review. Every push to `main` redeploys it within a minute or so.

This is a staging URL, so the site is currently marked `noindex` (a meta tag in
each page, plus `robots.txt`) to keep it out of search results while
shiba-ai.jp is still the real site.

## Going live on shiba-ai.jp

Only do this when the content is signed off — it replaces the current site.

1. Delete the `noindex` meta tag from all four HTML pages (each is flagged with
   a `STAGING ONLY` comment) and delete `robots.txt`.
2. Resolve anything left in **Outstanding** above.
3. `echo shiba-ai.jp > CNAME`, commit, push.
4. GitHub repo → Settings → Pages → Custom domain → `shiba-ai.jp`, then add the
   DNS records GitHub shows at the domain registrar. Wait for the certificate,
   then tick "Enforce HTTPS".

Until step 3, shiba-ai.jp keeps serving the old site — nothing is swapped over.
