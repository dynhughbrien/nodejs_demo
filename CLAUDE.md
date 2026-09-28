# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start Vite dev server
npm run build     # Type-check with tsc, then bundle with Vite
npm run preview   # Preview the production build locally
npx prettier --write src/  # Format source files
```

There is no test runner configured.

## Architecture

A minimal Vite + TypeScript browser app with no framework. Entry point is `index.html`, which loads `src/main.ts` as an ES module.

- `src/main.ts` — sole TypeScript source file; exports `setupCounter` and calls it immediately on `#counter-value`. The counter wraps at ±100 via `adjustCounterValue`.
- `public/` — static assets (SVGs, fonts, CSS) served verbatim by Vite.
- No bundler config file; Vite uses defaults with `index.html` as the entry.

TypeScript is in strict bundler mode (`noEmit: true`; tsc only type-checks, Vite handles bundling).

## Known intentional gap

The `-2` button (`#decreaseByTwo`) has no event listener wired up in `src/main.ts` — this is a deliberate tutorial exercise left incomplete. The `//TIP` comments throughout the file are WebStorm IDE tutorial hints and are not meaningful code documentation.

## Formatting

Prettier config: single quotes, 80-char print width, 2-space tabs.
