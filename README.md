# wayke — portfolio

Personal portfolio of a frontend developer. Vue 3 + TypeScript + Vite, deployed to GitHub Pages.

**Live:** [waykegoat.github.io](https://waykegoat.github.io/) · English version at [/en](https://waykegoat.github.io/en)

## Features

- Bilingual (Russian / English) with `vue-i18n`: language lives in the URL (`/` and `/en`), first visit is auto-detected from the browser language, manual choice is remembered
- Fully typed locale catalogs — TypeScript enforces key parity between languages at compile time
- Works catalog driven by a single `works.json` with per-language content and repo-hosted cover images
- Built-in admin panel (`/admin`) for editing works locally: bilingual editor, image compression, JSON + image export for redeploys
- Self-hosted variable fonts (Unbounded, Manrope) with per-script subsets
- Hero animation as an mp4 loop instead of a heavy gif, with `prefers-reduced-motion` fallback
- History routing with a 404 fallback for GitHub Pages, per-locale SEO meta, hreflang, Open Graph image, sitemap and robots.txt
- Custom cursor, scroll-reveal animations and marquee lines — all disabled for reduced-motion users

## Stack

Vue 3 (Composition API, `<script setup>`) · TypeScript · Vite · vue-router · vue-i18n · Vitest + Vue Test Utils · ESLint + Prettier

## Project structure

```
src/
  assets/img/works/   work cover images (referenced by imageKey)
  components/         layout, sections and UI components
  composables/        useScrollReveal, useSeoMeta
  data/               works.json + typed access helpers, static content
  i18n/               locale catalogs and locale utilities
  router/             routes and locale-aware navigation guard
  stores/             reactive works store persisted to localStorage
  views/              HomeView, AdminView
```

## Scripts

```bash
npm run dev         # dev server
npm run build       # type-check + production build
npm run preview     # preview the build
npm run test        # run unit and component tests
npm run lint        # eslint --fix
npm run type-check  # vue-tsc
```

## Content workflow

Works are edited in `/admin` (stored in the browser via localStorage). To publish changes:
press **Export**, put the downloaded `works.json` into `src/data/`, drop the downloaded
cover images into `src/assets/img/works/`, commit and push — GitHub Actions builds and
deploys automatically.
