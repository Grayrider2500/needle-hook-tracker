# Needle & Hook Stash Tracker

A mobile-friendly web app for cataloguing your knitting needle and crochet hook collection. No account, no server, no install — just open the file and start tracking.

**Live app:** https://grayrider2500.github.io/needle-hook-tracker/needle_tracker.html

---

## Features

- **Track two tool types** — knitting needles and crochet hooks, each with their own size lists and sub-types
- **Rich per-item fields** — type, sub-type, size, brand, length, quantity, on-loan status, and free-text notes
- **Filter & search** — filter by tool type, sub-type, or loan status; full-text search across size, brand, and notes
- **Duplicate detection** — warns before adding an entry that matches an existing type/size/brand combination
- **Editable dropdown lists** — add or remove sizes, sub-types, and brands to match your actual stash via the "Manage Lists" dialog
- **Export / Import** — back up your inventory as JSON or restore it on another device
- **On-loan tracking** — mark items as loaned out so you know what's missing from your collection
- **Responsive layout** — table view on desktop, card view on mobile (breakpoint at 640 px)
- **PWA / installable** — add to your iOS or Android home screen for an app-like experience; works fully offline after first load

---

## Data Storage

All data is saved locally in your browser's `localStorage` under the key `knitting_inventory_v1`. Nothing is sent to a server. Clearing your browser's site data will erase your inventory, so use the **Export** button to keep a backup.

---

## Files

| File | Purpose |
|---|---|
| `needle_tracker.html` | Main app — completely self-contained, no dependencies |
| `tictactoe.html` | Bonus standalone game |
| `manifest.json` | PWA manifest (name, icons, display mode) |
| `sw.js` | Service worker — network-first for HTML, cache-first for assets |
| `icon.svg` | Home screen / favicon icon |

---

## Running Locally

Open `needle_tracker.html` directly in any modern browser. No build step or local server required.

---

## PWA Notes

- The service worker caches assets so the app works offline after the first visit.
- If you're stuck on a stale version on an iOS home screen icon: delete the icon, go to **Settings → Safari → Clear History and Website Data**, then re-add to home screen.
