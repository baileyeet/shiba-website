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

## Deploy

Any static host. For GitHub Pages: push this folder to a repo, then
Settings → Pages → deploy from branch, root. Point `shiba-ai.jp` at it by adding
a `CNAME` file containing `shiba-ai.jp` plus the DNS records GitHub shows.
