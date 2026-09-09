# Shiba AI website

Static site — plain HTML and one CSS file. No build step, no dependencies.
Layout and palette follow [robirahman.com](https://github.com/robirahman/robirahman.github.io)
(930px measure, Roboto, blue links, near-black dark mode).

```
index.html      Home: intro + latest news + recent papers
research.html   All publications
news.html       All news
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

**Add a person.** In `people.html`, add one `<li>` to the right group
(Director / Researchers and collaborators / Operations / Alumni), alphabetical by
first name. Nobody carries an individual job title — the group heading says it.
Alumni are the exception: each shows their current affiliation in a
`<span class="affil">`, which is why that list uses the wider `people-wide` grid.

**Add news.** Add one `<li>` at the top of the list in `news.html`, and mirror it
at the top of the homepage list (the homepage shows the three most recent; trim
the oldest one there when you add). For a paper, name the paper and link the
title to its arXiv page rather than writing "paper accepted at X".

**Change a colour or spacing.** Everything lives in the `:root` variables at the
top of `css/style.css`; dark mode is derived from the same names.

## Outstanding

- Slides PDF for the BIAS workshop paper (`assets/slides/`, then uncomment the
  link in `research.html`).
- Five of the nine ported news items were deleted on request (Why We Study
  Multi-Agent Coordination, Deconstructing Mythos, ICML Seoul, OpenAI Hackathon,
  TARA). Their article bodies still exist on the old Wix site if they are ever
  wanted back.
- Two possible news items could not be confirmed on the old site: an Apr 22, 2026
  item about Strahinja Janjusevic and maritime infrastructure security (MIT News),
  and a Feb 11, 2026 preprint announcement. Add them if they are real.

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
