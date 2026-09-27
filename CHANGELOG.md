# Changelog

All notable changes to Cash Manager are documented here.

## [1.0.0] — Initial prototype

### Added
- Offline-first architecture: IndexedDB persistence, no server, no login, no
  external API required for core functionality.
- Dashboard with a live total-cash figure computed directly from denomination
  inventory, notes/coins split, and key stats (pieces, denominations, torn,
  new/old counts).
- Add Today's Cash flow with live per-denomination and grand-total
  calculation as quantities are entered.
- Advanced mode per denomination: optional individual note tracking
  (auto-generated rows for serial number, condition, torn/damaged) and
  per-coin condition tracking (no serial numbers for coins).
- Cash Inventory page grouped by Notes/Coins with condition breakdowns
  (New / Old / Medium Old / General) and torn-note counts.
- Denomination management: add, edit, disable/enable, and delete — with
  automatic soft-delete (disable) instead of destructive delete when a
  denomination has transaction history.
- Full transaction ledger (ADD, REMOVE, TRANSFER IN/OUT) with timestamps,
  before/after quantities, search, and filters by type, cash type,
  denomination, and date range.
- Remove Cash flow with insufficient-quantity guarding and confirmation
  before destructive changes.
- Transfer Cash flow recording paired TRANSFER OUT/IN entries between
  named locations for record-keeping.
- Reports: current cash summary, denomination table, condition summary,
  daily added/removed chart, and a torn-notes list.
- Settings: language switch (English / বাংলা) covering the entire interface,
  light/dark theme (with `prefers-color-scheme` support), editable currency
  configuration (defaults to Bangladeshi Taka), JSON backup export/import
  with validation before replacing data, and a clear-all-data action.
- About / branding page with the app description and creator profile,
  including a locally-stored, client-side-compressed profile photo.
- PWA scaffolding: `manifest.json` and an optional `service-worker.js` for
  offline shell caching when served over http(s).

### Known limitations (see README "Notes on scope")
- Transfers log movement history but do not maintain separate running
  totals per named location.
- No dedicated full-screen ledger for editing a single individual note's
  serial number after creation from the Inventory page.
- CSV export and richer charting were left out of this pass in favor of the
  JSON backup and the existing summary tables.
