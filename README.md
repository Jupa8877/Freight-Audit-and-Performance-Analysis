# Shipment Tracking KPI Dashboard (Tableau)

Interactive logistics analytics dashboard built in Tableau to monitor shipment performance, delays, and documentation quality using CSV export data.

---

## Project Overview
This project turns a shipment tracking spreadsheet/CSV export into an executive-ready Tableau dashboard that supports daily operations: identifying late shipments, surfacing recurring delay drivers, and improving documentation accuracy.

**Domain:** Logistics / Supply Chain / Operations Analytics  
**Tools:** Tableau, Excel/CSV

---

## Business Problem
Logistics teams often manage shipments across carriers, lanes, and warehouses using spreadsheets. When delays and documentation issues occur, it’s hard to answer basic operational questions quickly:

- Which carriers are missing delivery targets most often?
- What lanes are producing the largest delays?
- Are documentation errors trending up or down over time?
- Where should ops teams focus first to reduce exceptions?

This dashboard consolidates shipment-level records into measurable KPIs and drill-down views to support faster decision-making and proactive exception management.

---

## Dataset Description
The dataset represents shipment tracking records exported from a tracking sheet (CSV). Each row is a shipment with dates, status fields, and operational attributes used for KPI calculations.

**Files**
- `data/shipment_tracking.csv` — shipment-level tracking data (source CSV)
- `data/data_dictionary.csv` — field definitions and expected formats

**Typical fields (examples)**
- Shipment identifiers (e.g., shipment_id / reference_no / BOL_no)
- Carrier, shipper, consignee/recipient (if available)
- Origin / destination (city, state, or lane)
- Key dates: pickup, ETA, delivery/ATA
- Status / exception notes
- Documentation fields (e.g., docs_received_date, missing_docs_flag)

> Note: Column names may vary depending on the export. The dashboard logic is based on shipment-level dates and flags.

---

## KPIs & Metrics
KPIs are calculated directly in Tableau from the CSV fields.

- **Total Shipments**
  - Count of shipment records in the selected filter scope

- **On-Time Delivery %**
  - % of shipments delivered on or before ETA  
  - Common logic: `Delivered_On_Time = (ATA <= ETA)` for delivered shipments

- **Avg Delay Days**
  - Average positive difference between ATA and ETA (late shipments only)  
  - Common logic: `Delay Days = max(0, datediff('day', ETA, ATA))`

- **Docs Error Rate**
  - % of shipments with missing/incorrect documentation flags  
  - Common logic: `Docs Error = (missing_docs_flag = 1 OR docs_issue = 'Yes')`

If your export uses different fields, update the calculated field mappings in Tableau.

---

## Dashboard Features
The Tableau dashboard is designed for quick operational triage and root-cause exploration:

- **Top KPI tiles** for shipment volume, on-time %, average delay, and docs error rate
- **Carrier performance** view to compare on-time delivery and delay severity
- **Lane analysis / heatmap** to identify problematic origin-destination pairs
- **Documentation trend** view to track error rate changes over time
- **Global filters** (typical)
  - Date range
  - Carrier
  - Warehouse / site (if present)
  - Shipper / customer (if present)

---

## Tableau Public Link
GitHub cannot render `.twb` directly. View the interactive dashboard on Tableau Public:

**Tableau Public:** *(add link here)*  
`https://public.tableau.com/views/<your-workbook>/<your-dashboard>`

---

## Key Insights
Use this section to summarize what the dashboard reveals once you publish it (keep it factual and tied to the visuals). Example structure:

- **Carrier variability:** A small number of carriers may account for most late shipments (Pareto pattern).
- **Lane concentration:** Delays often cluster on specific lanes, suggesting capacity constraints or handoff issues.
- **Delay severity vs frequency:** Some carriers miss deadlines less often but with larger average delay days.
- **Documentation reliability:** Docs error rate can be tracked over time to validate process changes.

> Replace the bullets above with your actual findings after reviewing the dashboard filters and trends.

---

## Skills Demonstrated
- KPI definition and operational metric design (on-time %, delay days, docs error rate)
- Data cleaning and validation using Excel/CSV exports
- Tableau dashboard development (calculated fields, filters, parameters as needed)
- Performance troubleshooting mindset: isolating drivers by carrier, lane, and site
- Communicating business value through measurable outcomes and drill-down views

---

## How to Use This Repository
### 1) Review the data
- Open `data/shipment_tracking.csv`
- Check `data/data_dictionary.csv` for field meanings and formats (dates, flags, IDs)

### 2) Open the Tableau workbook
- Install **Tableau Desktop** (or use Tableau Public app if applicable)
- Open: `tableau/shipment_kpi_dashboard.twb`
- When prompted, re-link the data source to:
  - `data/shipment_tracking.csv`

### 3) Publish to Tableau Public
- In Tableau: **Server → Tableau Public → Save to Tableau Public**
- Copy the share link and paste it into the **Tableau Public Link** section above.

### 4) Preview screenshots
- See `screenshots/dashboard_preview.png` for a quick visual overview (static)

---

## Repository Contents
- `data/` — CSV exports + data dictionary
- `tableau/` — Tableau workbook (`.twb`)
- `screenshots/` — dashboard previews for quick review
- `README.md` — project documentation (this file)
- `LICENSE` — MIT license

