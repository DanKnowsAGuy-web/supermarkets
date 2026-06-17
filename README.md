# Energy Plus: Hotel Landing Page

Conversion-focused landing page for Energy Plus, an Independent Energy Solutions
Partner for hotels. Built with [Astro](https://astro.build).

**Live:** https://danknowsaguy-web.github.io/energy-plus-hotels/

## Develop

```bash
npm install
npm run dev      # local dev server
npm run build    # production build to dist/
npm run preview  # preview the production build
```

## Deploy

The live site is served from the `gh-pages` branch (the built `dist/` output).
After editing source on `main`, publish an update with:

```bash
npm run deploy
```

This builds the site and force-pushes `dist/` to `gh-pages`. GitHub Pages is
configured to serve that branch at the root.

## Content placeholders

Several values are intentional placeholders, marked in source with `PLACEHOLDER`
comments and a `.ph` class in the markup. Replace before publishing for real:

- Verified floor rate (`[X]%`), held blank until the methodology is locked
- Calculator floor rate constant (`src/components/Calculator.astro`)
- Case studies (`src/components/Proof.astro`)
- The booking CTA link (currently an in-page anchor)
