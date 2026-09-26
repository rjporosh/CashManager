# AI Handover Notes

Context for whoever (human or AI) picks this project up next.

## What this is

Cash Manager is a single self-contained `index.html` (markup, CSS, and
vanilla JS all inline) plus a PWA manifest, an optional service worker, and
app icons. It is intentionally **not** split into `js/*.js` / `css/*.css`
files — that keeps it dependency- and path-free, so it runs identically
opened straight from disk or served over http(s). If you do split it up for
a larger team workflow later, keep the module boundaries implied by the
inline code's own section comments (state/DB, denominations, inventory,
transactions, reports, backup, UI/router, branding).

## Data model (IndexedDB, one database)

- **denominations** — `{ id, type: 'note'|'coin', value, status: 'active'|'disabled', advanced, trackIndividual }`
- **inventory** — one row per denomination id: `{ denomId, quantity, conditions: {new, old, mediumOld, general}, torn }`.
  This is the single source of truth the dashboard total is computed from —
  never maintain a separate cached grand total that could drift.
- **individualNotes** — created only when a denomination has `trackIndividual`
  on and the user opts in during Add Cash: `{ id, denomId, seq, serial, condition, torn }`.
- **transactions** — append-only ledger: every ADD/REMOVE/TRANSFER writes one
  (or two, for transfers) rows with prev/new quantity, so history is never
  silently rewritten.
- **meta** — small keyed rows: currency config, language/theme settings,
  branding photo (compressed client-side before storing).

## Known simplifications (intentional, documented in README)

1. **Transfers** record a paired TRANSFER_OUT/TRANSFER_IN entry with free-text
   source/destination, but there is no per-location running balance — the
   app tracks one physical total, and transfers are for your own record only.
2. **Individual note editing** happens inline when the notes are first
   created (Add Cash → Advanced → Individual Details). There isn't yet a
   standalone editor to change a specific note's serial number later from
   the Inventory page — it's a natural next feature.
3. **CSV export / advanced charts** were left out of this pass; the JSON
   backup (Settings → Export Backup) and the in-app summary tables cover the
   same data.

None of the above are stubbed buttons — every visible feature works. These
are simply areas flagged as good next steps rather than gaps pretending to
be finished.

## If you extend this

- Keep the "inventory is truth" rule: any new feature that changes cash on
  hand must (a) update the `inventory` row and (b) write a `transactions`
  row in the same logical step, so a browser refresh never shows numbers
  that don't reconcile.
- Localization strings live in one dictionary object near the top of the
  inline script — add new UI text there for both `en` and `bn` rather than
  hardcoding strings in render functions.
- Respect `prefers-reduced-motion` and the existing light/dark CSS custom
  properties rather than introducing new hardcoded colors.
