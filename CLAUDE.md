# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a collection of standalone single-file web applications. Each app is a self-contained `.html` file with embedded CSS and JavaScript — no build step, no dependencies, no server required. Files can be opened directly in a browser.

## Architecture Pattern

All apps follow the same single-file pattern:

- **CSS** — embedded in `<style>` in `<head>`, using CSS custom properties (`:root` variables) for theming
- **HTML** — semantic structure in `<body>`
- **JavaScript** — embedded in a single `<script>` block at the bottom, organized into namespaced objects

### needle_tracker.html — JavaScript Namespace Structure

| Namespace | Responsibility |
|---|---|
| `SIZES` / `SUB_TYPES` | Static data constants (size lists, subtype options) |
| `InventoryDB` | Data access layer — all `localStorage` reads/writes; never touches the DOM |
| `FormController` | Add/edit form state machine (add mode vs. edit mode) |
| `FilterController` | Filter bar state and filtering logic |
| `ListRenderer` | Renders table rows (desktop) and cards (mobile) from a record array |
| `App` | Initialization, event wiring, calls `render()` after every mutation |

**Data** is stored in `localStorage` under key `knitting_inventory_v1` as a JSON array of flat record objects `{ id, toolType, subType, size, quantity, notes, createdAt, updatedAt }`.

**Responsive layout** uses a single breakpoint at `640px`. Both the `<table>` (desktop) and `<ul>` card list (mobile) are always in the DOM — CSS toggles visibility via `.desktop-only` / `.mobile-only`.

## GitHub Workflow

- All projects in this repo are tracked at **https://github.com/Grayrider2500/needle-hook-tracker**
- After completing any meaningful set of changes, commit and push to GitHub so edits are saved and tracked
- Use clear, descriptive commit messages summarizing what changed

## Conventions

- No external dependencies — everything must work fully offline
- `font-size: 16px` on all form inputs (prevents iOS auto-zoom)
- Use `crypto.randomUUID()` for IDs with a `Date.now().toString(36)` fallback
- All `localStorage` calls are wrapped in `try/catch` with a visible error banner on failure
- HTML is escaped via a local `escHtml()` helper before inserting user content into the DOM
