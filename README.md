# AI For Engineering Faculty

Slides, demos and site for the Montana State faculty workshop, Nov 4 2026, NAH 137.

## Layout

```
slides/slides.md         Slidev deck
slides/styles/index.css  deck theme, imports site/tokens.css
slides/layouts/idea.vue  divider slide for each big idea
site/                    static landing page
site/tokens.css          shared colors and fonts
demos/                   one script per live demo
.github/workflows/       builds the deck and site to GitHub Pages
```

## Use

```bash
npm install
npm run dev       # present the deck
npm run build     # build the deck to dist/slides
npm run export    # PDF of the deck
```

To preview the site, run `npm run build`, copy `site/*` into `dist/`, then serve `dist/`.

## Deploy

1. Push to `main`.
2. In the repo settings, set Pages source to "GitHub Actions".

## After The Talk

In `site/index.html`, replace the `video-placeholder` div with the YouTube iframe in the comment above it.
