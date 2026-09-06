# Daily Report Tables

Pre-built ad performance report tables — one self-contained HTML file per platform, each
speaking that platform's native metric vocabulary. Daily Log, Weekly Summary, Monthly
Summary, and Placement views, in the band-table format with a dark recomputed totals row.

| File | Platform | Headline efficiency metric | Notes |
|---|---|---|---|
| [amazon.html](amazon.html) | Amazon Ads | **ACOS** (spend ÷ sales × 100) | ROAS shown as its reciprocal |
| [flipkart.html](flipkart.html) | Flipkart Ads | **ROI** (total revenue ÷ spend, a multiplier) | includes indirect sales — Direct ROI shown beside it; impressions are called **Views**. No ACOS, no ROAS label |
| [meta.html](meta.html) | Meta Ads | **ROAS** (purchase value ÷ spend) | Meta has **no ACOS**. Clicks = link clicks; CTR/CPC on the link basis |
| [google.html](google.html) | Google Ads | **Conv. Value / Cost** (decimal ratio) | Google's own label — no column named ROAS, no ACOS |
| [shopify.html](shopify.html) | Shopify (store) | **CVR** (sessions completing checkout ÷ sessions) | store ledger, all channels — no ad-efficiency metrics on this table |
| [index.html](index.html) | All platforms combined | per-platform | the cross-platform log: every platform as a color band in one table |

## Rules every table follows

- **Each platform keeps its own vocabulary.** ACOS exists only on Amazon. Flipkart's number
  is ROI. Meta and Google use ROAS-style multipliers under their native labels.
- **Total rows recompute rates from summed counts** — never average the daily percentages.
- **Placement names are the platform's own** — Top of Search / Product Pages on marketplaces,
  Feed / Reels on Meta, Search / Display on Google.
- **Indian digit grouping and ₹ throughout** (`toLocaleString("en-IN")`).

## Wiring in real data

Each file has a `DAILY` array of base rows (spend, sales, orders, units, clicks,
impressions — plus `directSales` on Flipkart, `sessions`/`returning` on Shopify). Replace it
with API rows; every displayed column derives from those base fields via the formulas in
`COLS`, so rates stay consistent at any grain. The `WEEKS`/`MONTHS` arrays are demo scalers —
swap in real period rollups. All shipped numbers are synthetic sample data.

Open any file directly in a browser — no build step, no dependencies beyond a Google Fonts
stylesheet.

## Tailwind versions

The same five tables also exist as Tailwind CSS builds in [`tailwind/`](tailwind/) —
identical columns, data shape, and behavior, styled entirely with utility classes (Play CDN
for standalone use; copy the classes straight into a Tailwind project). The `COLS` and
`DAILY` structures are byte-identical between the two flavors, so a change in one ports to
the other mechanically.
