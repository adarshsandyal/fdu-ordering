# TWC FDU Order Calculator

A browser-based tool for **The Whole Cake** store managers to predict and plan **Fresh Daily Unit (FDU)** orders.

## 🔗 Live Site
**[Open the Order Calculator →](https://[your-username].github.io/fdu-ordering/)**

---

## What it does

1. **Select your store** from the dropdown (25 TWC locations)
2. **Pick the consumption date** — the date the FDUs will be served
3. **Set % growth** (default 2%) — applied to historical transaction averages
4. The tool instantly shows:
   - Projected Net Sales & Transactions (based on last 6 weeks of same weekday data)
   - Item-wise quantities to order, per store's own sales history
5. **Enter SOH** (Stock on Hand) per item — net need adjusts live
6. **Manager Override** — enter custom pack quantities for any item
7. **Export to CSV** or **Print** the order

## How quantities are calculated

```
Projected Transactions  = Historical Avg (same weekday) × (1 + growth%)
IPT (Items per Txn)     = Avg qty sold ÷ Avg transactions (same weekday)
Projected Units         = IPT × Projected Transactions
Net Need                = max(Projected Units − SOH, 0)
Order (Packs)           = ⌈ Net Need ÷ MOQ ⌉        ← packs to order
Final Order             = Manager Override (if set) else Order (Packs)
```

**Order date** = Consumption Date − 3 days (FDU lead time)

---

## Updating data each month

When you update the Excel file with new sales/transaction data:

1. Open the site in your browser
2. **Drag & drop the updated `FDU ORDERING .xlsx`** onto the upload bar at the top
3. The site re-processes everything instantly — no server, no code needed

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — HTML + CSS + JavaScript |
| `data.js` | Pre-aggregated data extracted from the Excel file |

## Tech

- Pure **HTML / CSS / JavaScript** — no framework, no build step
- [Tailwind CSS](https://tailwindcss.com/) via CDN for styling
- [SheetJS](https://sheetjs.com/) for in-browser Excel parsing
- Hosted on **GitHub Pages** (free, static hosting)
