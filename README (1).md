# 📊 Superstore Sales Dashboard — Excel Project

An end-to-end Excel analytics project: raw data auditing → data cleaning \& feature engineering → PivotTable-based analysis → KPI computation → single-page executive dashboard, built on the classic **Sample Superstore** retail dataset.

!\[Dashboard Screenshot](assets/dashboard-screenshot.png)

\---

## 📁 Repository Contents

|File|Description|
|-|-|
|`Sample - Superstore.xls`|Original, unmodified raw dataset as sourced|
|`Sample - Superstore\_Cleaned.xls`|Cleaned dataset with engineered date fields, ready for analysis|
|`Sample - Superstore\_Dashboard.xls`|Final workbook — PivotTables, KPI sheet, and the visual dashboard|
|`Superstore\_Dashboard\_Documentation.docx`|Full written project documentation|
|`assets/`|Dashboard screenshot(s) used in this README|

Each workbook contains three shared reference sheets — **Orders** (transaction line items), **Returns** (returned Order IDs), and **People** (region → manager mapping) — plus additional analysis sheets in the dashboard workbook.

\---

## 🎯 Project Objective

* Audit and clean a real-world style retail transactions dataset to make it analysis-ready.
* Engineer time-based fields to enable trend and seasonality analysis.
* Summarize business performance using core KPIs.
* Use PivotTables to analyze Sales \& Profit across Region, Category, Product, Customer, Ship Mode, and Month.
* Design a clean, single-screen executive dashboard.

\---

## 🛠️ Tools \& Techniques Used

* **Microsoft Excel** — the only platform used, end to end
* **Date formulas** (`DAY`, `MONTH`, `YEAR`, `TEXT`/`WEEKDAY`, date Extraction) for feature engineering
* **PivotTables** for multi-dimensional aggregation
* **Cell styling \& shape formatting** for the KPI-card dashboard layout
* **Manual data validation checks** (duplicates, blanks) for data quality auditing

\---

## 🔄 Project Workflow / Process

### Step 1 — Source the Raw Data

Started with `Sample - Superstore.xls`, containing **9,994 order records** across 21 columns in the `Orders` sheet, plus `Returns` (296 rows) and `People` (4 rows) reference sheets.

### Step 2 — Data Quality Audit

Before touching the structure, the raw data was checked for common issues:

|Check Performed|Result|
|-|-|
|Duplicate `Row ID` values|0 duplicates found|
|Blank `Postal Code` values|0 blanks found|
|Row count consistency|9,994 rows — no records needed to be dropped|

Since the raw data was already structurally clean, the cleaning phase focused on **feature engineering** rather than error correction.

### Step 3 — Feature Engineering (Cleaned Dataset)

Five new columns were derived from `Order Date` / `Ship Date` and inserted into the Orders table, producing `Sample - Superstore\_Cleaned.xls` (26 columns):

|New Column|Derived From|Purpose|
|-|-|-|
|`Day`|Order Date|Day-of-month component|
|`Month`|Order Date|Powers the monthly Sales/Profit trend Pivots|
|`Year`|Order Date|Enables year-wise filtering|
|`Weekdays`|Order Date|Day name, for weekday-pattern analysis|
|`No. of days`|Ship Date − Order Date|Shipping duration — a delivery-performance proxy|

### Step 4 — Build PivotTables

Eight PivotTables were built off the cleaned Orders table and placed on a dedicated **Charts** sheet inside `Sample - Superstore\_Dashboard.xls`:

1. **Sales by Region** (Max of Sales)
2. **Top 10 Products** (Sum of Sales)
3. **Bottom 10 Customers** (Sum of Sales)
4. **Sales by Region × Category** (matrix)
5. **Order Count by Segment × Ship Mode** (matrix)
6. **Sales Over Month** (trend)
7. **Profit Over Month** (trend)
8. **Max of Sales by Region** (supporting/cross-check pivot)

### Step 5 — Compute Headline KPIs

A dedicated **KPI** sheet consolidates five metrics computed directly from the full Orders table:

|KPI|Value|Formula Basis|
|-|-|-|
|Total Sales|2,297,200.86|`SUM(Sales)`|
|Total Profit|286,397.02|`SUM(Profit)`|
|Average Sales|229.86|`AVERAGE(Sales)`|
|Total Orders|9,994|`COUNT` of order lines|
|Total Customers|793|Count of unique Customer IDs|

### Step 6 — Design the Dashboard

On a dedicated sheet, the five KPIs were turned into **color-coded summary cards** under the title *"Superstore Sales Dashboard."* The layout deliberately keeps the executive view to a single screen — large, bold white numerals on a blue gradient card background — so the headline numbers are unmissable, while all detailed PivotTable breakdowns stay one click away on the Charts sheet.

### Step 7 — Document the Project

All of the above was written up in `Superstore\_Dashboard\_Documentation.docx`, and summarized here in this README for GitHub.

\---

## 📈 Key Insights

* **Overall:** 2,297,200.86 in total sales and 286,397.02 in profit across 9,994 orders from 793 customers (avg. sale value: 229.86).
* **Regional leader:** West region leads in total sales (725,457.82); South has the lowest total (391,721.90) despite holding the single highest individual sale (22,638.48).
* **Category strength:** Technology is the top category overall (836,154.03), ahead of Furniture and Office Supplies.
* **Top product:** A single SKU (`TEC-CO-10004722`) contributes 61,599.82 — more than double the next best-selling product.
* **Shipping:** Standard Class dominates (5,968 of 9,994 orders, \~60%) across every customer segment.
* **Segment mix:** Consumer is the largest segment by volume (5,191 orders, \~52%).
* **Seasonality:** Sales peak in November (352,461.07) and September (307,649.95); February is the slowest month.
* **Profit seasonality:** Profit peaks in December (43,369.19), suggesting stronger Q4 margins even though November has higher sales.

\---

## 🚀 How to Explore This Project

1. Clone/download the repo.
2. Open `Sample - Superstore.xls` to see the raw source data.
3. Open `Sample - Superstore\_Cleaned.xls` to see the engineered date fields.
4. Open `Sample - Superstore\_Dashboard.xls` and check the **Charts**, **KPI**, and **Dashboard** sheets to explore the full analysis and final dashboard.
5. Read `Superstore\_Dashboard\_Documentation.docx` for the complete narrative write-up.

\---

## 🔮 Possible Next Steps

* Add a Returns-rate KPI by joining the `Returns` sheet against `Orders`.
* Add slicers on Region, Category, and Segment for interactive filtering.
* Analyze Discount vs. Profit, since high discounts are a common driver of order-level losses.
* Turn the `No. of days` field into a delivery-performance KPI (avg. shipping duration by Ship Mode / Region).

\---

## 👤 Author

**Viswa Desikan**
B.Tech, Artificial Intelligence \& Data Science
Mahendra Engineering College (Autonomous), Namakkal, Tamil Nadu

