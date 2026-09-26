# Cash Manager

An offline-first cash denomination and inventory manager. Single self-contained
static web app — HTML5, CSS3, vanilla JavaScript, IndexedDB. No build step,
no server, no login, no external API.

## Run it

Just open `index.html` in a browser — double-click it, or:

```
python3 -m http.server 8080
# then visit http://localhost:8080
```

Serving it (rather than opening the file directly) also lets the optional
service worker register, which caches the app shell for offline use and lets
it be installed as a PWA (`manifest.json` is already wired up). Everything —
data entry, inventory, transactions, reports, settings — works identically
either way, since all data lives in the browser's IndexedDB.

## What's included

- **Dashboard** — live total cash, notes/coins split, denomination cards, stats
- **Add Cash** — per-denomination quantity entry with live totals; toggle
  "Advanced" on a denomination to track individual notes (serial number,
  condition, torn/damaged) or per-coin condition, auto-generated as you type
  a quantity
- **Cash Inventory** — grouped by note/coin with condition breakdowns, plus
  a condition-count adjustment tool
- **Denominations** — add/edit/enable/disable; denominations with recorded
  history are archived rather than deleted, so past transactions stay valid
- **Transactions** — full audit trail (ADD/REMOVE/TRANSFER/ADJUSTMENT) with
  search, filters, and expandable before/after detail
- **Remove Cash** and **Transfer** — guarded against removing more than you
  have; transfer logs a paired TRANSFER OUT/IN entry for your own records
  without double-counting your tracked total
- **Reports** — current summary, denomination table, condition summary,
  daily net change, recent activity
- **Settings** — language (English/বাংলা, fully localized), light/dark theme,
  currency configuration (country, name, symbol, ISO code — defaults to
  Bangladeshi Taka), profile photo (stored locally), backup export/import
  (JSON), and clear-all-data
- **About** — app description and creator profile/branding

## Data & privacy

Everything is stored locally in IndexedDB. Nothing is sent anywhere — no
analytics, no tracking, no network calls for core functionality. Use
**Settings → Export Backup** to save a portable JSON copy, and
**Import Backup** to restore it (imports are validated before anything is
overwritten).

## File structure

```
cash-manager/
├── index.html          # the entire application (markup, styles, logic)
├── manifest.json        # PWA manifest
├── service-worker.js     # optional offline cache (only used when served over http)
├── assets/
│   ├── icon.svg
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

`index.html` is intentionally self-contained (rather than split into the
many small `js/*.js` files a larger team project might use) so the app is
guaranteed to work the moment it's opened, with zero path or CORS issues —
including directly from disk on a phone.

## Notes on scope

This is a functional prototype covering the full core workflow end to end
(add → inventory → remove/transfer → transactions → reports → settings/backup),
built and manually tested (including in headless Chromium across phone
breakpoints, both themes, and both languages). A few areas were deliberately
kept simple for this pass and are natural next steps:

- Transfer currently records movement history between locations you name,
  without maintaining separate running totals per location.
- Individual note/coin records are generated inline in the Add Cash flow;
  there isn't yet a dedicated full-screen ledger for editing a single note's
  serial number after the fact from the Inventory page.
- CSV export and full data-visualization charts were left out in favor of
  the JSON backup and the existing tables/summaries.
