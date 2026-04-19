# Financial KPI Monitoring & Profitability Dashboard

## 📥 Download

| File | Description |
|---|---|
| [📊 Financial_KPI_Dashboard.pbix](https://github.com/atishey4/financial-kpi-dashboard-powerbi/raw/main/Financial_KPI_Dashboard.pbix) | Power BI Dashboard File |

> **Note:** Download the `.pbix` file and open it with [Power BI Desktop](https://powerbi.microsoft.com/desktop/) to explore the full interactive dashboard.

---

## Dashboard Overview

![Financial KPI Dashboard](screenshots/Screenshot%202026-04-19%20015756.png)

---

## Objective
To build a Power BI dashboard that monitors key financial KPIs (Revenue, Expenses, Profit Margin, ROI, Operating Costs) and provides profitability insights across products, regions, and time periods.

---

## Tools Used
- **Power BI Desktop** – Dashboard design, data modeling, and report building
- **Power Query Editor** – Data cleaning and transformation
- **DAX (Data Analysis Expressions)** – KPI and measure creation
- **Microsoft Excel / CSV** – Source dataset

---

## Dataset Description

A realistic financial dataset containing **500+ rows** with the following columns:

| Column | Description |
|---|---|
| Date | Transaction date |
| Month | Month name extracted from date |
| Quarter | Q1 / Q2 / Q3 / Q4 |
| Year | Fiscal year |
| Region | East, West, North, South |
| Department | Finance, Marketing, Operations, Sales |
| Product Category | Apparel, Electronics, FMCG, Software |
| Product Name | Individual product name |
| Revenue | Total revenue generated |
| Cost of Goods Sold (COGS) | Direct cost of products sold |
| Operating Expenses | Indirect business expenses |
| Gross Profit | Revenue minus COGS |
| Net Profit | Revenue minus all expenses |
| Profit Margin % | Net Profit / Revenue × 100 |
| Sales Volume | Units sold |
| Budgeted Revenue | Planned revenue target |
| Actual Revenue | Revenue actually achieved |
| Budget Variance | Difference between budgeted and actual revenue |
| Customer Segment | B2B / B2C / Enterprise |
| Sales Channel | Direct, Online, Partner, Retail |

---

## Power Query Steps

1. **Remove null and blank values** – Ensures no empty rows affect calculations
2. **Change data types** – Set Revenue, COGS, Profit as Currency; Date as Date type
3. **Create Month, Quarter, Year columns** – Extracted from the Date column for time-based filtering
4. **Handle duplicates** – Removed duplicate Transaction IDs to maintain data integrity
5. **Rename columns** – Made column names consistent and readable
6. **Format currency and percentage fields** – Applied proper number formatting for financial figures
7. **Create calculated columns** – Added Gross Profit and Net Profit directly in Power Query where needed

---

## DAX Measures

```dax
Total Revenue = SUM(FinancialData[Revenue])

Total Cost = SUM(FinancialData[COGS]) + SUM(FinancialData[Operating Expenses])

Gross Profit = SUM(FinancialData[Gross Profit])

Net Profit = SUM(FinancialData[Net Profit])

Profit Margin % = DIVIDE([Net Profit], [Total Revenue], 0) * 100

Budgeted Revenue = SUM(FinancialData[Budgeted Revenue])

Actual Revenue = SUM(FinancialData[Actual Revenue])

Budget Variance = [Budgeted Revenue] - [Actual Revenue]

Revenue Growth % =
    DIVIDE(
        [Total Revenue] - CALCULATE([Total Revenue], DATEADD(DateTable[Date], -1, YEAR)),
        CALCULATE([Total Revenue], DATEADD(DateTable[Date], -1, YEAR))
    ) * 100

Cost Ratio % = DIVIDE([Total Cost], [Total Revenue], 0) * 100
```

---

## Dashboard Features

- **KPI Cards** – Total Revenue, Gross Profit, Net Profit, Profit Margin %, Budget Variance displayed at the top
- **Column Chart** – Total Revenue by Region for regional performance comparison
- **Bar Chart** – Net Profit by Product Category to identify top-performing categories
- **Line Chart** – Monthly Revenue and Net Profit trend across the year
- **Donut Chart** – Revenue distribution by Sales Channel
- **Waterfall Chart** – Step-by-step breakdown from Revenue to Net Profit
- **Matrix Table** – Region-wise summary of Revenue, COGS, Net Profit, and Profit Margin %
- **Slicers & Filters** – Region, Department, Product Category, Sales Channel, Month, Quarter, Year

---

## Key Insights

- **West region** generates the highest revenue at ₹8.28 Cr, followed closely by East, North, and South
- **Apparel** is the most profitable product category by net profit contribution
- The company maintains an overall **Profit Margin of 32.71%**, indicating healthy profitability
- **Budget Variance of ₹1.08M** shows actual revenue is tracking above plan
- **Online and Direct** channels contribute the majority of revenue based on sales channel distribution
- Revenue remains relatively stable month-over-month with a slight dip mid-year, suggesting seasonal patterns
- Despite consistent revenue, margin fluctuations indicate varying cost structures across departments

---

## Conclusion

This Financial KPI Monitoring & Profitability Dashboard provides a comprehensive, interactive view of an organization's financial health. By consolidating revenue, cost, profit, and budget data into a single Power BI report, it enables finance teams and management to make faster, evidence-based decisions. The dashboard is suitable for use by Finance Analysts, FP&A Analysts, Business Analysts, and senior leadership who need a clear view of KPIs across regions, product categories, departments, and sales channels.
