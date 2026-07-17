# IM8 Operations Tool

A self-contained, single-file HTML tool for IM8 Limited's daily operations — production planning, fulfillment, shipping, and forecasting. No installation required; runs entirely in Chrome using client-side JavaScript (SheetJS/xlsx-js-style for Excel generation).

## 🔗 Live version (recommended)

Open directly in your browser — no download needed:

**https://sammiyip-ops.github.io/-IM8-Operations-Tool/**

*(If this link 404s, GitHub Pages may still be deploying — wait 1–2 minutes after the first push, or check the repo's Settings → Pages tab.)*

## 📥 Offline / local version

1. Click `index.html` above → **Download raw file** (or `Code → Download ZIP`)
2. Open the downloaded `index.html` file directly in **Google Chrome**
3. Works fully offline once loaded — only the two Excel-writing CDN scripts require an initial internet connection

## Tabs

| Tab | Purpose |
|---|---|
| **1. Production Calculator** | Upload sales data → explodes bundle SKUs into components via BOM → shows grand total per component to produce. Optional inventory upload nets off on-hand stock (including bundle stock deduction). |
| **2. Fulfillment Generator** | Batch-assigns orders to inventory batches for warehouse fulfillment. Flags orders with blank AWB/tracking numbers. |
| **3. GPS Generator** | Builds the courier import file for GPS shipments, matching the exact column format required. |
| **4. Production Forecast** | Combines colleague's forecast + actual sales (weighted average or exponential smoothing) + inventory → next week's production forecast. Includes a "Send to Production Calculator" bridge. |
| **5. Gift Tracker** | Explodes multi-item gift order rows into one row per item. |
| **6. Courier Splitter** | Assigns each D365 order line to a courier (SF / FEDEX / DHL / GPS) based on configurable per-country rules, flags AUS customs 3-month-supply violations, and generates the daily 8-sheet pivot Excel file. Includes 31-day history with charts. |

## Data & privacy

Everything runs locally in your browser — no data is uploaded to any server. Uploaded files never leave your machine. Production/courier history is stored in your browser's `localStorage`, so it's per-device (clearing browser data will clear history too).

## Requirements

- Google Chrome (recommended) or any modern Chromium-based browser
- Internet connection on first load (to fetch the xlsx-js-style library from CDN)

## For developers

This is a single HTML file (`index.html`) with:
- Inline `<style>` for all CSS
- Inline `<script>` for all logic (vanilla JS, no build step, no framework)
- Two external CDN scripts: `xlsx-js-style` (Excel read/write with cell styling)

To make changes, edit `index.html` directly and push. No build/compile step needed — GitHub Pages serves it as-is.
