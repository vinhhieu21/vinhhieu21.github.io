# Project Guide For Agents

## Overview
- This repo is the source for the user's personal website on the `vinhhieu21.github.io` GitHub Pages user domain.
- The site was converted from a single static `index.html` page into a SvelteKit app.
- The current site is a single-page landing page with a dark/light theme toggle and mostly placeholder personal content that the user will likely refine later.

## Stack
- Framework: SvelteKit
- Svelte version: `^5.51.0`
- Build tool: Vite
- Adapter: `@sveltejs/adapter-static`
- Type setup: JavaScript with `jsconfig.json`
- Runes mode is enabled through `svelte.config.js`

## Important Files
- [`package.json`](/Users/hieubuivinh/Dev/vinhhieu21.github.io/package.json): scripts and dependencies
- [`svelte.config.js`](/Users/hieubuivinh/Dev/vinhhieu21.github.io/svelte.config.js): static adapter configuration and Svelte runes compile option
- [`src/app.html`](/Users/hieubuivinh/Dev/vinhhieu21.github.io/src/app.html): early theme initialization before hydration
- [`src/routes/+layout.js`](/Users/hieubuivinh/Dev/vinhhieu21.github.io/src/routes/+layout.js): `prerender = true`
- [`src/routes/+page.svelte`](/Users/hieubuivinh/Dev/vinhhieu21.github.io/src/routes/+page.svelte): the main homepage, including markup, theme toggle logic, and page-specific styles

## Commands
- Install deps: `npm install`
- Start dev server: `npm run dev`
- Type and Svelte checks: `npm run check`
- Production build: `npm run build`
- Preview production build: `npm run preview`

## Build And Deployment Notes
- This project is configured for a static output and writes the built site to `build/`.
- This is a GitHub Pages user-site repo, so the site is expected to live at the domain root. Do not add a non-empty SvelteKit `paths.base` unless the deployment model changes.
- Do not reintroduce a root-level `index.html`. SvelteKit uses `src/app.html` and route files instead.

## Current UI Architecture
- The homepage is intentionally a single route and currently keeps all page markup and styling in `src/routes/+page.svelte`.
- The visual design uses:
  - CSS custom properties for light/dark themes
  - a persistent theme toggle using `localStorage`
  - an early inline theme bootstrap in `src/app.html` to reduce theme flash
  - responsive layout with a large hero, supporting right-column panel, and multiple content sections
- Theme state in `+page.svelte` uses Svelte 5 runes: `let theme = $state('light');`

## Content Notes
- Some content is still placeholder by design:
  - email address uses `hello@example.com`
  - project cards are examples rather than real portfolio entries
  - about/now text is polished placeholder copy
- If the user asks for content improvements, prefer replacing placeholders with their actual details rather than expanding more generic filler text.

## Working Rules For Future Agents
- Preserve the current SvelteKit structure unless the user explicitly asks for a framework change.
- Keep the site GitHub Pages compatible. Static output is the default assumption.
- Before finishing UI or content changes, run:
  - `npm run check`
  - `npm run build`
- If you move styles out of `src/routes/+page.svelte`, keep the theme system behavior intact.
- If you modify the theme logic, verify both:
  - initial theme before hydration
  - persisted theme after toggling
- Prefer small, clean component extractions only when they improve maintainability. Do not split the page into many tiny components without a clear reason.

## Known State
- The old plain `index.html` was intentionally deleted during the SvelteKit conversion.
- The project had successful `npm run check` and `npm run build` after the conversion.
- Git status may show a large migration diff because the repo changed from a static HTML site to SvelteKit. Treat that as expected unless the user says otherwise.

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:ca08a54f -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

## Session Completion

**When ending a work session**, you MUST complete ALL steps below. Work is NOT complete until `git push` succeeds.

**MANDATORY WORKFLOW:**

1. **File issues for remaining work** - Create issues for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **PUSH TO REMOTE** - This is MANDATORY:
   ```bash
   git pull --rebase
   bd dolt push
   git push
   git status  # MUST show "up to date with origin"
   ```
5. **Clean up** - Clear stashes, prune remote branches
6. **Verify** - All changes committed AND pushed
7. **Hand off** - Provide context for next session

**CRITICAL RULES:**
- Work is NOT complete until `git push` succeeds
- NEVER stop before pushing - that leaves work stranded locally
- NEVER say "ready to push when you are" - YOU must push
- If push fails, resolve and retry until it succeeds
<!-- END BEADS INTEGRATION -->
