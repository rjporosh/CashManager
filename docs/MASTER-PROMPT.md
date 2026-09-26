You are an autonomous senior frontend/product engineer, UI/UX designer, QA engineer, and Git workflow engineer.

Your task is to build a complete, professional, production-quality prototype called:

CASH MANAGER

A modern offline-first Cash Denomination & Cash Inventory Manager.

The application must be built as a single self-contained static web application using:

- HTML5
- CSS3
- Vanilla JavaScript
- IndexedDB for persistent local data
- No React
- No Angular
- No Vue
- No Node.js runtime requirement
- No .NET
- No backend
- No server/database
- No authentication
- No cloud dependency for core functionality
- No Tailwind dependency
- No build step required for the final application

The final application must work by simply opening the HTML application locally or serving the folder through a basic static web server.

It must be suitable for eventually packaging as an Android/iOS application.

---

1. CORE PRODUCT CONCEPT

Cash Manager allows a user to maintain an exact inventory of physical cash.

The user can record:

- How much cash they currently have
- How many notes of each denomination they have
- How many coins of each denomination they have
- Whether notes/coins are new, old, medium-old/general
- Individual note serial numbers when required
- Torn/damaged notes
- Cash additions
- Cash removals
- Cash transfers
- Complete transaction history
- Date/time of every change
- Current total cash
- Denomination-wise quantity
- Note-wise quantity
- Coin-wise quantity
- Detailed reports

The fundamental calculation is:

DENOMINATION VALUE × QUANTITY = TOTAL VALUE

The dashboard must always calculate the total current physical cash from the actual denomination inventory.

Never allow the displayed total cash to become inconsistent with the underlying denomination data.

---

2. OFFLINE-FIRST REQUIREMENT

This is an offline-first application.

All important functionality must work without internet access:

- Dashboard
- Add cash
- Remove cash
- Edit cash
- Denomination management
- Note management
- Coin management
- Serial number management
- Transactions
- Reports
- Settings
- Language switching
- User profile/branding
- Data persistence

Use IndexedDB as the primary persistent storage.

Do not depend on an online API.

Do not make CDN resources mandatory for the application to function.

If any external library is used, the application must have a graceful fallback or locally bundled alternative.

The application must continue functioning after:

1. Internet is disconnected
2. Browser is restarted
3. Device is restarted
4. Application is reopened

---

3. DESIGN PHILOSOPHY

The UI must look like a polished modern mobile application rather than a generic HTML demo.

Visual direction:

- Professional
- Elegant
- Premium
- Minimal
- Charming
- Modern
- Clean
- Highly readable
- Financial/productivity-app aesthetic
- Subtle animations
- Excellent spacing
- Strong visual hierarchy
- Professional typography
- Carefully designed cards
- Beautiful empty states
- Clear success/error feedback
- No unnecessary visual clutter

Do NOT create a generic Bootstrap-looking website.

Do NOT make it look like an admin template.

Do NOT use excessive gradients.

Do NOT overcrowd the interface.

Use a coherent professional design system.

Create a proper application icon/logo for Cash Manager using CSS/SVG where appropriate.

---

4. RESPONSIVE REQUIREMENT

This is extremely important.

The application must work beautifully on:

- Small Android phones
- Large Android phones
- iPhones
- iPads
- Tablets
- Desktop
- Large desktop monitors
- Landscape mobile
- Portrait mobile
- Landscape tablet
- Portrait tablet

There must never be:

- awkward blank areas
- broken cards
- horizontal overflow
- clipped buttons
- unreadable tables
- oversized empty sections
- broken navigation
- unusable forms
- tiny touch targets

The same design language should be preserved across screen sizes while adapting intelligently.

Use responsive CSS with:

- CSS Grid
- Flexbox
- CSS clamp()
- responsive breakpoints
- safe-area support
- dynamic viewport units
- mobile-first design

Support:

"env(safe-area-inset-top)"
"env(safe-area-inset-bottom)"
"100dvh"

The interface must feel native-like on mobile.

Touch targets should generally be at least approximately 44px.

---

5. PORTRAIT AND LANDSCAPE

Test and optimize both:

Portrait

Especially:

- 320px
- 360px
- 375px
- 390px
- 412px
- 430px

Landscape

Especially:

- mobile landscape
- iPad landscape
- desktop wide screens

Never solve landscape problems by simply leaving a large empty area.

Use the available screen intelligently.

---

6. APPLICATION STRUCTURE

Create a polished application with logical sections such as:

1. Splash Screen
2. Dashboard
3. Today's Cash
4. Add Cash
5. Cash Inventory
6. Denominations
7. Transactions
8. Reports
9. Individual Note Details
10. Settings
11. Language
12. Currency Configuration
13. Branding/Profile

Navigation can use a modern bottom navigation on mobile and an adaptive sidebar/navigation system on larger screens.

Do not blindly use both simultaneously.

---

7. SPLASH SCREEN

Create a short professional splash screen.

It should contain:

- Cash Manager logo
- Application name
- Short tagline
- Elegant subtle animation
- Branding identity

Example tagline:

"Know Your Cash. Down to Every Note."

The splash screen must be lightweight and should not delay application startup unnecessarily.

Allow the application to transition automatically into the dashboard.

---

8. DEFAULT COUNTRY AND CURRENCY

Default configuration:

Country:
Bangladesh

Currency Name:
Taka

Currency Short Name:
Tk

Currency ISO Code:
BDT

Currency Symbol:
৳

Currency Symbolic/Technical Name:
BDT

Display examples:

৳ 12,450
৳ 1,000
৳ 50

Do not use £ for Bangladeshi Taka.

However, the architecture must allow the user to edit currency configuration later.

---

9. CURRENCY CONFIGURATION

Create a currency configuration system.

Fields:

- Country
- Currency Name
- Short Name
- ISO Code
- Currency Symbol
- Currency Technical/Symbolic Code

The user must be able to edit these values.

The UI must update dynamically.

Do not hardcode ৳ everywhere.

---

10. CASH TYPES

Support two primary cash types:

Notes

Coins

Each type has configurable denominations.

---

11. DEFAULT BANGLADESH COINS

Initialize reasonable Bangladesh coin denominations.

For example:

- ৳1
- ৳2
- ৳5

The system must allow the user to:

- Add denomination
- Edit denomination
- Disable denomination
- Re-enable denomination
- Delete denomination where safe

Do not permanently hardcode the denomination list.

---

12. DEFAULT BANGLADESH NOTES

Initialize:

- ৳2
- ৳5
- ৳10
- ৳20
- ৳50
- ৳100
- ৳500
- ৳1000

The user must be able to add additional denominations.

For example:

- ৳2000

This means the application architecture must work for any denomination, not only Bangladesh.

---

13. DENOMINATION MANAGEMENT

Create a professional denomination management page.

Each denomination should show:

- Type: Note/Coin
- Value
- Currency
- Status
- Quantity currently available
- Total value
- New/Old tracking availability
- Individual tracking availability

Actions:

- Add
- Edit
- Disable
- Enable
- Delete where safe

Prevent accidental deletion when historical transactions depend on the denomination.

Instead of destroying historical references, use soft deletion/archiving.

---

14. ADD TODAY'S CASH

Create an extremely easy "Add Today's Cash" experience.

The user should see available denominations.

Example:

Notes

৳100
Quantity: [ 10 ]

৳500
Quantity: [ 4 ]

৳1000
Quantity: [ 2 ]

Coins

৳1
Quantity: [ 10 ]

৳2
Quantity: [ 5 ]

৳5
Quantity: [ 8 ]

Show live calculation:

৳100 × 10 = ৳1,000
৳500 × 4 = ৳2,000
৳1000 × 2 = ৳2,000

Total Added Cash:

৳5,000

The total must update instantly.

---

15. ADVANCED MODE

Each note denomination must have an:

"Advanced"

option.

Default:

OFF

When Advanced is OFF:

The user only enters quantity.

Example:

৳100
Quantity: 20

The application simply records 20 pieces.

When Advanced is ON:

Additional controls become available.

---

16. INDIVIDUAL NOTE DETAILS

When Advanced mode is enabled for a note denomination, provide:

"Add Individual Details"

checkbox.

Default:

OFF

If the user enters:

৳2
Quantity = 100

and checks:

Add Individual Details

automatically create 100 individual note records.

Do NOT make the user manually click "Add note" 100 times.

Create the 100 rows automatically.

Each row should have:

- Sequence number
- Serial number
- Condition/type
- Torn/Damaged
- Optional notes

Example:

#001
Serial: [____]
Condition: [General ▼]
Torn: [ ]

#002
Serial: [____]
Condition: [General ▼]
Torn: [ ]

etc.

---

17. NOTE CONDITION

Each individual note must support:

- New
- Old
- Medium Old
- General

Default:

General

Use a clean select/dropdown.

The wording and localization must be configurable.

---

18. TORN/DAMAGED NOTE

Each individual note must have:

Torn/Damaged

checkbox.

Default:

Unchecked

When checked:

- Mark the note as torn/damaged
- Reflect the status in inventory
- Include it in reports
- Maintain its value
- Keep the transaction history intact

Do not automatically delete a torn note.

---

19. COIN ADVANCED MODE

Coins do not have serial numbers.

When Advanced mode is enabled for coins:

Allow:

- New
- Old

Default:

General

For example:

৳5 coin

Quantity: 20

Advanced:

ON

Allow individual coin records such as:

Coin #001 → Old
Coin #002 → New
Coin #003 → General

etc.

Do not create serial number fields for coins.

---

20. CASH INVENTORY

Create a dedicated inventory page.

Group by:

Notes
Coins

Each denomination should display:

- Denomination
- Quantity
- New
- Old
- Medium Old
- General
- Torn/Damaged where applicable
- Total value

Example:

৳500

Total Pieces: 12

New: 4
Old: 3
Medium Old: 2
General: 3

Total Value:

৳6,000

---

21. DASHBOARD

Dashboard must immediately answer:

"How much physical cash do I have right now?"

Create a visually dominant total:

TOTAL CASH

৳ 24,850

Below it show:

Notes
Total note pieces
Total note value

Coins
Total coin pieces
Total coin value

Then show denomination cards.

Example:

৳1000
12 pieces
৳12,000

৳500
8 pieces
৳4,000

৳100
20 pieces
৳2,000

etc.

---

22. DASHBOARD SUMMARY

Also show useful statistics:

- Total Cash
- Total Notes
- Total Coins
- Total Pieces
- Number of Denominations
- Torn Notes
- New Notes
- Old Notes

Keep the dashboard uncluttered.

Use expandable sections if necessary.

---

23. CASH TRANSACTIONS

Every change to inventory must create a transaction record.

Transaction types:

- ADD
- REMOVE
- TRANSFER IN
- TRANSFER OUT
- ADJUSTMENT
- EDIT
- CORRECTION

Every transaction should record:

- ID
- Date
- Time
- Transaction type
- Denomination
- Cash type
- Quantity
- Total amount
- Previous quantity
- New quantity
- Source
- Destination where applicable
- Note/details
- Individual note references where applicable

---

24. DATE/TIME TRACKING

Every inventory change must record exact date/time.

Display human-friendly formats.

Example:

26 Sep 2026
1:42 PM

Store timestamps internally in a robust format.

Do not rely only on formatted strings.

---

25. TRANSACTION HISTORY

Create a professional transaction page.

Allow:

- Search
- Filter by date
- Filter by type
- Filter by Notes/Coins
- Filter by denomination
- Filter by Add/Remove/etc.

Each transaction should be expandable.

Show:

Before
Change
After

Example:

৳100 Notes

Before: 20
Added: 10
After: 30

Transaction:
ADD

26 Sep 2026
01:42 PM

---

26. REMOVE CASH

Provide a proper "Remove Cash" workflow.

Example:

Remove:

৳500 × 2

Total:

৳1,000

Before:

৳20,500

After:

৳19,500

Require confirmation before destructive changes.

Do not allow the user to remove more pieces than currently exist.

---

27. TRANSFER

Support transferring cash.

For example:

Wallet → Home Cash Box

Cash Box → Wallet

Bank-related physical cash can also be represented as a source/destination if the user chooses.

Each transfer must generate:

TRANSFER OUT

and

TRANSFER IN

records as appropriate.

Do not silently modify inventory without transaction history.

---

28. EDIT INVENTORY

Users must be able to edit existing cash records.

Any modification must:

- Recalculate totals
- Update dashboard
- Preserve history
- Create an audit transaction

Never silently overwrite historical information.

---

29. REPORTS

Create a Reports section.

Include:

Current Cash Summary
Denomination Summary
Notes Summary
Coins Summary
Condition Summary
Torn Notes
Transaction History
Daily Changes
Cash Flow

Provide date filters.

Use charts only where useful.

Do not overuse charts.

---

30. DATA CONSISTENCY

This is critical.

The application must have one reliable source of truth.

Do not maintain unrelated duplicate totals that can drift apart.

Calculate dashboard totals from inventory data or maintain derived values with proper transactional updates.

Test:

Add → total increases

Remove → total decreases

Edit → total recalculates

Delete/disable denomination → historical transactions remain valid

Refresh browser → data remains

Close browser → data remains

Restart device → data remains

---

31. LOCALIZATION

Support:

English
Bangla

Create a proper localization system.

Do NOT scatter hardcoded text throughout JavaScript.

Use translation keys.

Example:

"t.dashboard"
"t.totalCash"
"t.notes"
"t.coins"
"t.addCash"
"t.removeCash"
"t.transactions"

Provide a language switcher.

The entire interface should update.

Not only the dashboard.

---

32. BANGLA UI

Bangla must be natural and professional.

Avoid awkward machine-translated wording.

Examples:

Total Cash:
মোট নগদ

Notes:
নোট

Coins:
কয়েন

Quantity:
পরিমাণ

Transactions:
লেনদেন

Add Cash:
নগদ যোগ করুন

Remove Cash:
নগদ সরান

Settings:
সেটিংস

Reports:
রিপোর্ট

Use appropriate Bangla typography and spacing.

---

33. BRANDING

The application must contain professional personal branding.

Display:

MD. IKRAMUL ISLAM SIDDIQUE POROSH

Senior Software Engineer

Phone:
+8801672896992

Portfolio:
https://rjporosh.github.io

YouTube:
https://YouTube.com/@mdikramulislamsiddiqueporosh

LinkedIn:
https://www.linkedin.com/in/md-ikramul-islam-siddique-porosh-4393b333a

Do not invent any additional social links.

The user will provide a professional photo.

Create a profile/branding area where the photo can be uploaded and stored locally using IndexedDB or an appropriate local mechanism.

The photo should appear elegantly in:

- Profile/Branding section
- About section
- Optional dashboard/profile header if appropriate

Do not make the branding overpower the Cash Manager product.

It should look like a professional creator/developer signature.

---

34. BRANDING PHOTO

Support:

- Upload photo
- Preview
- Replace photo
- Remove photo

Persist the image locally.

Handle large images sensibly.

Resize/compress client-side if appropriate.

Never require a server upload.

---

35. ABOUT PAGE

Create a beautiful About section.

Include:

Cash Manager

Offline-first cash denomination and inventory management.

Created by:

MD. Ikramul Islam Siddique Porosh
Senior Software Engineer

Show professional profile image.

Show portfolio/social links.

---

36. SETTINGS

Settings should include:

- Language
- Currency
- Country
- Denominations
- Notes/Coins configuration
- Theme
- Branding/Profile
- Data management
- About

Data management:

- Export data
- Import data
- Backup
- Restore
- Clear all data

For destructive actions, require confirmation.

---

37. DATA BACKUP

Create a complete local backup/export mechanism.

Export all important IndexedDB/application data into a portable JSON file.

The user should be able to:

Export Backup

and later:

Import Backup

Validate imported data before replacing current data.

Never destroy existing data before successful validation.

---

38. OPTIONAL DATA EXPORT

If practical, support:

- JSON backup
- CSV transaction export

Do not compromise core functionality to implement unnecessary features.

---

39. PWA-READY ARCHITECTURE

Prepare the project so it can later become a PWA/mobile app.

Include, where appropriate:

- manifest.json
- service-worker.js
- icons
- offline caching
- installable metadata

The application should still work as a normal static HTML project.

Do not make PWA installation mandatory.

---

40. MOBILE APP READINESS

The architecture should be suitable for wrapping using technologies such as:

Capacitor

later.

Do not add Capacitor itself unless required.

The current prototype must remain simple and static.

Avoid browser-only desktop assumptions.

---

41. ACCESSIBILITY

Support:

- keyboard navigation
- visible focus states
- semantic HTML
- accessible labels
- sufficient contrast
- screen-reader-friendly controls
- reduced-motion preference

Respect:

"prefers-reduced-motion"

---

42. ERROR HANDLING

Every important operation must have graceful error handling.

Never allow:

- silent failures
- broken UI after an error
- unhandled promise rejection
- corrupted local data
- accidental destructive actions

Use professional toast/snackbar notifications.

Examples:

"Cash added successfully."

"2 notes removed."

"Backup exported successfully."

"Unable to import backup. The file appears invalid."

---

43. CONFIRMATION DIALOGS

Use custom application dialogs instead of browser alert() wherever practical.

For destructive operations:

- Remove cash
- Delete denomination
- Clear all data
- Restore backup

require explicit confirmation.

---

44. EMPTY STATES

Every list must have a beautiful empty state.

Examples:

No transactions yet.

No cash has been added yet.

No individual notes are being tracked.

Do not leave giant blank white areas.

---

45. LOADING STATES

Use lightweight loading/skeleton states when needed.

Do not create unnecessary artificial delays.

---

46. ICON SYSTEM

Create a consistent icon system.

Prefer:

- inline SVG
- local SVG assets

Avoid relying on remote icon CDNs.

Icons must have consistent size and stroke style.

---

47. THEME

Implement a polished light theme.

If practical, also support dark theme.

The light theme is mandatory.

Do not let dark mode compromise the light design.

---

48. SECURITY / PRIVACY

This is local financial information.

Do not send cash information anywhere.

No analytics.

No tracking.

No external API.

No remote storage.

Clearly keep data local.

---

49. FILE STRUCTURE

Use a clean professional structure, for example:

cash-manager/
│
├── index.html
├── manifest.json
├── service-worker.js
│
├── assets/
│   ├── icons/
│   ├── images/
│   └── logo/
│
├── css/
│   ├── app.css
│   ├── responsive.css
│   └── components.css
│
├── js/
│   ├── app.js
│   ├── db.js
│   ├── state.js
│   ├── localization.js
│   ├── currency.js
│   ├── denominations.js
│   ├── inventory.js
│   ├── transactions.js
│   ├── reports.js
│   ├── backup.js
│   ├── ui.js
│   └── utils.js
│
├── README.md
├── CHANGELOG.md
└── AI_HANDOVER.md

You may improve this structure if your engineering judgement suggests a better organization.

Do not unnecessarily split files into dozens of tiny files.

---

50. CODE QUALITY

Write maintainable code.

Use:

- clear naming
- modular functions
- constants
- reusable UI functions
- event delegation where appropriate
- defensive validation
- comments only where useful
- no duplicated business logic

Avoid:

- giant monolithic functions
- global variable pollution
- inline event handlers everywhere
- magic numbers
- duplicated calculation logic
- dead code
- placeholder implementations

---

51. NO FAKE FEATURES

Do not create buttons that do nothing.

Every visible primary feature must work.

If a feature cannot reasonably be completed in the prototype, either:

1. implement it properly, or
2. clearly mark it as planned/not implemented.

Never create fake UI pretending a feature works.

---

52. TESTING

Perform thorough manual/static testing.

Test at minimum: