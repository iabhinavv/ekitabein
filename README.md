# ekitabein — e-ink readers for India

**ekitabein pvt. ltd.** · 5257, Sector 38 West, Chandigarh 160036
orders@ekitabein.com · WhatsApp +233 257319254

---

## 1. What this is

We import white-label e-ink readers from Chinese OEMs, put our own brand on them, and sell them in India through two channels:

| Channel | Site | How money is made |
|---|---|---|
| **Direct to consumer** | `ekitabein.com` | Storefront, cart, checkout, prepaid and COD |
| **Corporate gifting** | `ekitabein.com/business` | No cart. Quantity-based quotes, engraved and boxed, invoiced against a PO |

The commercial idea is narrow and worth stating plainly: **we do not sell a bookstore.** Kindle and Kobo sell an ecosystem and lock the library to it. We sell a device that opens EPUB, PDF, MOBI and CBZ off a USB-C cable with no account, no registration and no store. That is the only thing we compete on, alongside price and an India-serviced warranty.

The corporate site exists because gifting is the fastest route to volume for an unknown hardware brand: one buyer, one purchase order, two hundred units, and no cost of acquiring two hundred individual customers.

---

## 2. Files in this folder

| File | What it is |
|---|---|
| `ereaders.xlsx` | The original sourcing sheet — 19 Alibaba quotes and 12 months of Google Trends data. Source of truth for FOB costs. |
| `ekitabein-spec.html` | Build specification and wireframes for the retail store. Stack, database, payments, logistics, and the India import-compliance map. |
| `ekitabein-demo.html` | Working retail storefront prototype. Browse, filter, compare, cart, checkout, GST invoice, ops console. |
| `ekitabein-corporate.html` | Working corporate gifting site. Range pricing, MOQ 1, branding, inquiry flow. |
| `ekitabein-financial-model.xlsx` | Landed cost, price list, startup costs, 24-month P&L, cash flow, unit economics. |
| `finance-templates/` | Accounting and planning templates copied from `Basic Formats`, listed in §7. |

All three HTML files are single, self-contained files. Open them directly in a browser; there is no build step and no server.

---

## 3. The SKU tally — which reader is which

**This is the table to check against the sourcing sheet.** Our product names are house-brand names; the right-hand columns are the actual units they are built on.

| Our name | Inches | Built on (sourcing sheet row) | Supplier | FOB ₹ | Landed ₹ | List ₹ | Gross margin |
|---|---|---|---|---|---|---|---|
| **Nukta 3.5** | 3.5 | `Xuezhiyou` | — | 2,938 | 4,598 | 6,999 | 34.3% |
| **Girah 4.3** | 4.3 | `Yuesheng Tong X4` | Guangzhou Xingyuangang | 5,478 | 8,006 | 9,999 | 19.9% |
| **Safha 7** | 7.0 | `E-Reader Multimedia` | Shenzhen VansDisplay | 4,872 | 7,193 | 10,999 | 34.6% |
| **Varak 5.7** | 5.7 | `BK577A` | — | 6,283 | 9,087 | 11,499 | 21.0% |
| **Panna 6** | 6.0 | `Black Eink` | — | 5,578 | 8,141 | 11,999 | 32.2% |
| **Panna Max 6** | 6.0 | `EReader HD` | — | 7,201 | 10,319 | 14,999 | 31.2% |

Names are Hindi/Urdu words from the world of books, which is the one thing tying the range together:
*nukta* — a dot · *girah* — a knot · *safha* — a page · *varak* — a leaf · *panna* — a page/emerald.

### Gift sets (corporate site only)

| Set | Built around | List ₹ |
|---|---|---|
| The Conference Pack | Nukta 3.5 | 7,999 |
| The Welcome Kit | Panna 6 | 13,499 |
| The Executive Set | Girah 4.3 | 13,999 |
| The Milestone Box | Panna 6 | 14,999 |

### What we dropped, and why

| Dropped | Reason |
|---|---|
| Boox Tab X, Bigme B7 Pro, Bigme B751C, Bigme 6-inch, HamGeek M3, Duokan/MiReader | **Third-party trademarks.** Bought from Alibaba traders with no authorisation letter: counterfeit risk, no warranty channel, and customs exposure if the mark is recorded. 6 SKUs across 4 brands. |
| `V3` and `Xteink X3` (both 3.7-inch) | **The economics are inverted.** They land at about ₹11,400 — more than any 6-inch and ₹4,200 more than the 7-inch. A smaller, lower-resolution screen that costs more than a 6-inch cannot be priced below it and still make money. |
| `Wholesale Open E-book` (the old "Panna Lite") | It lands at ₹8,786 against the Black Eink's ₹8,141. A "lite" model that costs *more* than the standard model is not a product. There is no cheaper 6-inch in the sheet. |
| `Xteink X4` as the 4.3-inch base | Re-based onto **Yuesheng Tong X4** at ₹5,478 FOB instead of ₹7,097. Same screen size, ₹2,173 less landed. This is what makes a sub-₹10,000 pocket model possible at all. |

That leaves **13 usable OEM units** in the sheet, of which **6** make a coherent ladder.

---

## 4. Pricing — how it is built, and the fix that was needed

### The problem you spotted

The first pass priced the pocket models *above* the 6-inch: the 3.7-inch at ₹13,499 and the 4.3-inch at ₹14,499 against a 6-inch at ₹10,999. No consumer pays more for a smaller screen, and you were right to push back.

The cause is real and sits in the sourcing data: **small e-ink panels cost more per unit than mainstream 6-inch panels**, because 6-inch is the volume size the whole industry is tooled for. Landed cost, cheapest first:

```
Xuezhiyou 3.5in      FOB 2,938   ->  landed  4,598
E-Reader Multi 7in   FOB 4,872   ->  landed  7,193
Yuesheng Tong 4.3in  FOB 5,478   ->  landed  8,006
Black Eink 6in       FOB 5,578   ->  landed  8,141
BK577A 5.7in         FOB 6,283   ->  landed  9,087
EReader HD 6in       FOB 7,201   ->  landed 10,319
Xteink X4 4.3in      FOB 7,097   ->  landed 10,179   <- dropped as a base
V3 3.7in             FOB 8,010   ->  landed 11,404   <- dropped entirely
```

### The fix, in three parts

1. **Drop the 3.7-inch.** It cannot be made to work at any sane price.
2. **Re-base the 4.3-inch** onto the cheapest 4.3-inch in the sheet (Yuesheng Tong X4).
3. **Take the margin down on the small screens.** The two sub-6-inch models now run at **~20% gross margin** against **32–35%** on the mainstream units. We earn less per pocket unit on purpose, because the price ladder has to make sense to a buyer.

Resulting ladder — price now rises with screen size, with the two specialists sitting below the 6-inch:

| Price | SKU | Inches | Margin |
|---|---|---|---|
| ₹6,999 | Nukta 3.5 | 3.5 | 34.3% |
| ₹9,999 | Girah 4.3 | 4.3 | **19.9%** |
| ₹10,999 | Safha 7 | 7.0 | 34.6% |
| ₹11,499 | Varak 5.7 | 5.7 | **21.0%** |
| ₹11,999 | Panna 6 | 6.0 | 32.2% |
| ₹14,999 | Panna Max 6 | 6.0 | 31.2% |

**Safha 7 is the SKU to push.** Biggest screen in the range, best margin, and the lowest FOB of any full-size unit. It should be the hero product.

### Volume slabs (corporate)

The original 8/14/20% discount ladder was too deep. At 20% off, the 20%-margin SKUs sold at a loss. Revised:

| Quantity | Discount | Worst-case margin (Girah 4.3) |
|---|---|---|
| 1 – 24 | list | 19.9% |
| 25 – 99 | −4% | 16.6% |
| 100 – 499 | −8% | 12.9% |
| 500+ | −12% | 9.0% |

**Minimum order is one unit** on both sites. On the corporate side that is a deliberate sales tool, not a concession: nobody signs off 200 engraved units without holding one first, and a sample that takes three weeks kills the timeline.

> ⚠ Do not push the two low-margin SKUs to the 500+ slab without renegotiating FOB first. At 9% gross they do not cover fulfilment and warranty.

---

## 5. What changed in this round

| Change | Where |
|---|---|
| Removed the custom sleep screen | Dropped from branding options, product gallery, and the branding page. Engraving is now the single branding mechanism. |
| Removed all demo tagging | Top banner, footer disclaimer, legal page notice, and every stray "demo" in copy. |
| Real company details | `ekitabein pvt. ltd.`, Chandigarh address, WhatsApp `+233 257319254`, `orders@ekitabein.com`. **All fabricated GSTIN, CIN and staff names deleted rather than replaced** — inventing a tax identifier on a live site is worse than having none. Warranty servicing moved from Delhi to Chandigarh. |
| Gift set layout rebuilt | Artwork on top, text beneath, price and CTA baseline-aligned across all four cards via `margin-top:auto`. Was a side-by-side grid with ragged text. |
| Pricing rebuilt | See §4. |
| Volume slabs reduced | 8/14/20% → 4/8/12%. |
| Mobile layout fixed | Added the missing `<meta name="viewport">` (without it a phone rendered the page at ~980px and shrank everything). Rebuilt the `≤720px` styles: one product card per row, larger type, full-width CTAs, 2×2 KPI grid, and horizontal scroll kept on wide tables. Corporate site only. |
| CSR / book-donation programme added | New **"CSR & book donation"** occasion tile (shown on the home and occasions grids and its own detail page) plus a dedicated CSR section on the home page. Companies donate readers to government schools and public libraries across India; every unit ships pre-loaded with the full **NCERT set, classes 1–12** and a shelf of **open-publication / public-domain books**, working offline with no account. Framed against Schedule VII (education) CSR spend and added to the inquiry occasion list. Donation picks lead with the **Safha 7** (a 7-inch page holds an NCERT textbook column without reflowing). Corporate site only. |

Untouched: the retail store (`ekitabein-demo.html`) and the spec (`ekitabein-spec.html`). Those still carry the older 8-SKU range and the demo framing.

**Still to do:** apply the same SKU and pricing changes to the retail store; add a real GSTIN once registration completes; confirm NCERT / open-publication redistribution terms and line up school and library partners before the CSR programme goes live.

---

## 6. The financial model

`ekitabein-financial-model.xlsx`. Every green cell is an input; everything else is a live formula. Sheets in dependency order:

| Sheet | What it does |
|---|---|
| **Inputs** | Every assumption in one place — duty, freight, CAC, RTO, growth, channel mix. |
| **Landed Cost** | FOB → CIF → duty → landed, per SKU. |
| **Price List** | List price and margin at each quantity slab. |
| **Startup Costs** | One-time spend to first sale, low and high case. |
| **Operating Costs** | Monthly fixed cost, year 1 and year 2. |
| **Sales Forecast** | 24 months, seasonality taken from the Google Trends sheet. |
| **P&L** | Monthly and year-1 totals. |
| **Cash Flow** | Monthly, with inventory bought 3 months ahead. |
| **Unit Economics** | Contribution per retail order vs per corporate order. |
| **Scenarios** | Conservative / base / optimistic drivers. |

### Base case at a glance

| | Year 1 |
|---|---|
| Revenue | ₹1.24 crore |
| Gross profit | ₹34.7 lakh (28.1%) |
| Net profit | ₹9.9 lakh |
| Contribution per retail order | ₹2,296 |
| Contribution per corporate order (85 units) | ₹1.72 lakh |
| Retail orders/month to cover fixed cost | 33 |
| **Funding needed** | **₹55 lakh** |
| Lowest cash point | +₹8.5 lakh (month 20) |

### The finding that matters most

**The business is profitable in year 1 and still runs out of cash.** Those are not contradictory. At ₹22 lakh of funding the model bottoms out at **−₹24.5 lakh** around month 20, because stock is paid for roughly three months before it is sold and corporate buyers pay half up front and half later.

Working capital, not profitability, is the binding constraint on an import business. **Fund for the trough, not the P&L.** That is why the model defaults to ₹55 lakh of opening cash against a startup cost of roughly ₹14–24 lakh.

### Costs included

Import: FOB, freight and insurance, basic customs duty, social welfare surcharge, CHA and port, inland freight. Compliance amortised: BIS CRS, WPC ETA, e-waste and battery EPR, Legal Metrology. Per unit: retail packaging, BIS-registered Indian pin adapter, cable, QC and serialisation. Selling: courier, outer packing, payment gateway, COD RTO losses, returns, warranty reserve, marketing per order acquired, corporate selling cost per order won. Fixed: warehouse, platform, apps, support, ops staff, accounting, corporate salesperson, insurance, bank charges, annual compliance.

IGST paid at import is **excluded** — it is creditable against output GST and is not a cost. Basic customs duty and the surcharge are not creditable and are included.

### The one number to verify before trusting any of this

**Basic customs duty — `Inputs!C12`, currently 20%.** Every landed cost, every price and the entire P&L hang off it. E-book readers are commonly classified under HS 8543 70 99, but the rate must be confirmed by a customs house agent. The Scenarios sheet shows the swing: 15% versus 25% moves gross margin by roughly 6 points across the whole range.

---

## 7. Templates copied from `Basic Formats`

Copied into `finance-templates/` because they map to work this project actually needs:

| File | Why |
|---|---|
| `business-startup-costs.xlsx` | Cross-check against the Startup Costs sheet. |
| `profit-and-loss-projection.xlsx`, `income-statement.xlsx` | Annual statutory-format P&L. |
| `sales-forecast.xlsx` | Alternative 3-year forecast layout. |
| `cash-flow-statement.xlsx` | Formal cash flow for a lender or investor. |
| `balance-sheet.xlsx`, `00.copy of BS PL FORMAT.xlsx` | Year-end statements. |
| `business-budget.xlsx` | Departmental budgeting once there is a team. |
| `business-plan-workbook.xlsx`, `Business model canvas.pdf`, `swot-analysis.xlsx` | Narrative documents for funding conversations. |
| `GST Reconciliation Sheet.xlsx` | **Directly needed.** Monthly GSTR-1 / GSTR-3B / books reconciliation. |
| `MSME/` | Udyam registration and the 43B(h) payment-terms rules that apply once you buy from MSME vendors. |

Left behind: auditor's report formats, 269SS/269T and 40A(3) certificates, Clause 44, DSC authorisation, audit trail notes, LLP agreement (we are a private limited, not an LLP), and the personal finance calculators. Those belong to a statutory audit, not to setting the business up.

---

## 8. What happens next, in order

1. **Confirm the HS code and duty rate with a customs house agent.** Everything else is guesswork until this is fixed.
2. **Ask every supplier whether they hold a BIS R-number** for the model, and whether they will apply. This is the 6–14 week critical path and the manufacturer has to do it, not you.
3. Register the entity, GST, IEC and Udyam. File the trademark in classes 9 and 35.
4. Order one sample of each of the six SKUs and live with them for a week before committing.
5. **Confirm the blank Wi-Fi cells in the sourcing sheet.** Nine SKUs have Wi-Fi unrecorded; it changes both the product story and whether WPC approval is required.
6. Re-run the model with real numbers, then decide the funding amount off the cash trough.

---

*Figures in this document are planning estimates built from the sourcing sheet and standard Indian import assumptions. Duty rates, certification fees and courier rates must be confirmed with a customs house agent, a company secretary and a 3PL before committing money.*
