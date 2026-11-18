# E-commerce Cash Flow Control — Shopify + Amazon demo

A browser-based cash flow dashboard for e-commerce brands. It shows **how sales turn into cash, a 12-month rolling forecast that includes the Black Friday inventory build, and budget vs actual**, built from bank, Shopify and QuickBooks CSV exports.

**Live demo:** https://dariabusova.github.io/ecommerce-cashflow-dashboard/

The demo brand is a fictional US skincare company selling on Shopify and Amazon (about $3M in annual gross sales). All figures are generated and invented.

## What it shows

| View | What it answers |
|---|---|
| **Overview** | How much cash is there, where does it go, and where is it heading through the next holiday season? |
| **Sales → cash** | How do gross sales become deposits? It breaks down refunds, payment fees, Amazon referral and FBA fees, sales tax collected and remitted, money in transit, and days to cash by channel. |
| **Cash flow statement** | Monthly statement of cash flows (direct method), with actual and forecast months side by side. |
| **Forecast** | A 12-month forecast with live assumptions: sales growth by channel, Black Friday strength, ad spend (% of sales and implied ROAS), refund rate, product cost, supplier deposit, lead time, freight and duties, a new hire, a one-off investment and the minimum cash floor. It also lists open and planned purchase orders. |
| **Budget vs actual** | Year-to-date cash variance by category against the December budget, with the lines that explain the gap. |
| **Transactions & import** | The transaction journal plus CSV import. |

## The e-commerce cash mechanics it models

- **Shopify payouts:** paid twice a week at T+2, net of payment fees and refunds, and including sales tax. About 90% of a month's sales land in the same month.
- **Amazon settlements:** paid every 14 days, net of referral and FBA fees. About half of a month's sales land the following month. Amazon remits sales tax itself.
- **Sales tax:** collected through Shopify and remitted to the states the following month. It passes through the bank but is not revenue.
- **Inventory:** ordered from the manufacturer before the sales month (lead time + 1). A deposit is paid at order, the balance on shipment, and freight and import duties on arrival. Holiday stock is paid for in August–October, before the November payouts arrive.
- **Advertising:** Meta, Google and Amazon Ads as a percentage of channel sales, with higher spend during Black Friday and Cyber Monday.
- **Shopify Capital:** an advance repaid by withholding 12% of each payout until the fixed amount is repaid.
- **Fulfillment (3PL):** charged per order, plus storage, the month after the sales.

## Importing your own data

Drag one or more CSV files onto the import panel. Three formats are recognised automatically:

1. **Standard:** `Date, Amount, Description, Counterparty, Category`, with signed amounts.
2. **Shopify payouts:** the export from *Finances → Payouts* (`Payout Date, Status, …, Total`). Only paid payouts are imported.
3. **QuickBooks:** a Transaction Detail export (`Date, Name, Memo/Description, Split, Amount`).

Duplicates are skipped and unknown categories are created automatically. Reports run through the last **closed** month. Rows dated after it are kept in the journal as the open period. See the `samples/` folder for examples.

## Privacy

There is no backend. Data stays in the visitor's browser (`localStorage`). **Reset demo data** restores the sample brand.

## Visual styles

Three switchable presets: **Midnight Luxe**, **Brutalist Signal** and **Vapor Clinic**. They share one fixed design system: a grain overlay, 2–3rem radii, magnetic buttons and GSAP entrance animations.

## Tech

A single `index.html` file. It uses React 18 with `htm` (no build step), GSAP and hand-drawn SVG charts. It runs on GitHub Pages, Vercel or any static host.

## Publish on GitHub Pages

1. Create a public repository and upload `index.html`, `README.md`, `LICENSE` and the `samples/` folder.
2. Go to **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, then click **Save**.
3. The site goes live at `https://<your-username>.github.io/<repository-name>/`.

---

Built by **Daria Busova**, Financial Controller · FP&A and cash flow forecasting for e-commerce brands.
