# TWC FDU Order Calculator

A browser-based tool for **The Whole Cake** store managers to predict and plan **Food Display Unit (FDU)** orders.

## 🔗 Live Site
**[Open the Order Calculator →](https://adarshsandyal.github.io/fdu-ordering/)**

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

When you update `FDU ORDERING .xlsx` with new sales and transaction data:

1. In the `FDU_ORDERING` directory, double-click `update_and_push.bat` (or run `python generate_data_js.py && git add data.js && git commit -m "Update data" && git push`).
2. The GitHub Pages site updates automatically within 60 seconds for all users!

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
