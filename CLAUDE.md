# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

@AGENTS.md

## Commands

- `npm install` — install dependencies
- `npm run dev` — start the dev server at `localhost:4321` (see `@AGENTS.md` above for running it in the background)
- `npm run build` — build the production site to `./dist/`
- `npm run preview` — preview the production build locally
- `npm run astro -- <command>` — run any Astro CLI command, e.g. `npm run astro -- check` or `npm run astro -- add <integration>`

There is no test suite configured yet.

## Architecture

This is an Astro project using file-based routing:

- `src/pages/` — each `.astro` file becomes a route (`src/pages/index.astro` → `/`)
- `src/layouts/Layout.astro` — shared HTML shell (`<html>`/`<head>`/`<body>`) that pages wrap their content in via `<slot />`
- `src/components/` — reusable `.astro` components
- `src/assets/` — images and other assets that go through Astro's build pipeline (optimized, hashed); import these rather than referencing by path
- `public/` — static files served as-is at the site root (e.g. `favicon.ico`), not processed by the build

`astro.config.mjs` currently has no integrations or adapters configured. TypeScript config extends Astro's `strict` preset (`astro/tsconfigs/strict`).
