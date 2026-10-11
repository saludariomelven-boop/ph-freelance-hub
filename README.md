# REALWORLD — Hyper-Realistic Business Simulation

REALWORLD is a text-first, single-file business management simulation. It uses a responsive HTML/CSS/JavaScript interface rather than 2D/3D scenes. The GitHub Pages build does not require a build system, external framework, database, or server.

## Current gameplay

- Three business models: online retail, cafe/food, and digital agency.
- Nominal in-game currency in Philippine pesos (PHP).
- Weekly time advancement, modeled customer demand, competitor pressure, economic changes, and random business events.
- Pricing, contribution margins, inventory orders, supplier credit, stockout tracking, and capacity constraints.
- Hiring and dismissing staff, wages, onboarding costs, labour capacity, and marketing.
- Owner capital injections, modeled term loans, principal repayments, interest, and overdraft mechanics.
- Accrual-based modeled revenue and expenses, cost of goods sold, depreciation, estimated tax reserves, balance sheets, and journal entries.
- Illustrative insurance, licensing, bookkeeping, compliance and risk controls.
- Bankruptcy/closure conditions for sustained financial distress, while preserving available reports and exports.
- Browser-local autosave, JSON save import/export, and CSV history export.
- Responsive desktop and mobile navigation.

## Data integrity and safer workflows

- Imported JSON saves are validated before they can replace the active company.
- Validation checks required fields, numeric ranges, inventory values, journal balancing, and balance-sheet reconciliation.
- Rejected imports should leave the current company unchanged; importing over a current company asks for confirmation.
- Closing a week and other destructive actions use in-app confirmation dialogs.
- Tax-reserve adjustment uses an in-app numeric input constrained to 5–40%, rather than a browser-native prompt.
- The close-week action is protected against accidental repeated processing.

These checks protect against malformed save files; they do not make the client-only game tamper-proof. The client and local saves remain under the player's control.

## QA status and known scope

The post-update QA report dated 2026-10-09 reported successful live tests for company creation, price changes, stock orders, close-week confirmation/cancellation, duplicate-click protection, save export, and navigation. Its Node.js harness reported 100+ simulated weeks across all three industries with balanced journal entries and a reconciled balance sheet. That report also identified a native browser prompt in the tax-reserve action. The current working update replaces that final native prompt with an in-app numeric modal.

Some reported results were code-audited or tested through a Node.js harness rather than a live browser, including file-picker import and mobile viewport behavior. Re-run those tests after publishing. This is not a guarantee that every browser/device combination is defect-free.

## Scope limitations

This is a playable prototype, not a complete real-world economy. Market conditions, competitor prices, customer demand, financing and business events are modeled assumptions, not live market data. Tax, employment, licensing, insurance, supplier-credit, and accounting rules are simplified abstractions; this game does not provide legal, tax, or accounting advice. It does not register a real business, make payments, or connect to banks.

Saves are stored in the browser's `localStorage`. Another device/browser has a separate save unless the player manually exports and imports a JSON file. GitHub Pages does not provide shared persistent multiplayer state or secure server-side game logic; those features require a backend.

## Publish on GitHub Pages

For this existing repository, keep `index.html` in the repository root.

1. Upload/replace the root `index.html` with the updated file and commit the change to the configured publishing branch (`main` in the current setup).
2. Upload/replace this README if you want the latest project notes in the repository.
3. GitHub Pages normally rebuilds automatically after the committed change.
4. If the site appears unchanged, check the Pages deployment status and hard-refresh the page to bypass stale browser cache.
5. Test the tax-reserve numeric modal, company creation, close-week confirmation, save export/import, and post-bankruptcy restrictions.

For a new repository, upload `index.html` to the top-level folder, then open **Settings → Pages** and select **Deploy from a branch**, `main`, and `/(root)`.

## Updating the game

Make changes to the existing `index.html`, commit them to the configured publishing branch, and check the Pages deployment status if the live URL does not update. Keep a backup of the working source and export important game saves before testing. If the internal save schema changes, explicitly consider compatibility with older JSON exports.

## Suggested next development steps

1. Formalize the deterministic regression harness as repeatable automated tests.
2. Add a proper cash-flow statement, aged receivables/payables, and documented period-close behavior.
3. Improve loan amortization schedules and financing options.
4. Add customer segments, price elasticity, more capable competitor strategies, supplier lead times, seasonality, inflation, interest-rate cycles, and labour-market effects.
5. Expand long-term decisions: locations, leases, equipment financing, capacity investment, contracts, and restructuring.
6. Only then consider cloud saves, accounts, multiplayer, and a server-authoritative economy.
7. For stronger realism, validate jurisdiction-specific assumptions against reliable sources and record model assumptions transparently.

## Run locally

Open `index.html` in a modern browser. No build command is required. For best compatibility, use a current Chrome, Edge, Firefox, or Safari browser.
