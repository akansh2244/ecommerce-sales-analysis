# E-commerce Customer Segmentation & Sales Analysis (RFM)

An end-to-end data analysis project on a UK-based online retailer's transactional data — from raw data cleaning to RFM (Recency, Frequency, Monetary) customer segmentation, SQL business analysis, and an interactive dashboard.

## Problem Statement

The business needs to understand its customer base at a deeper level than total sales — specifically, which customers are most valuable, which are loyal but average spenders, and which are at risk of churning — so that marketing and retention efforts can be targeted effectively instead of applied equally to everyone.

## Dataset

- **Source:** Online Retail Dataset (UCI) — UK-based online retailer
- **Time period:** December 2010 – December 2011
- **Records analyzed:** 392,732 transaction line items across 4,339 unique customers and 37 countries
- **Total revenue represented:** ~$8.89M

## Tools Used

- **Python** (Pandas, NumPy) — data cleaning and RFM feature engineering
- **SQL** (PostgreSQL) — business question analysis
- **Power BI / Tableau** — interactive dashboard

## Process

1. **Data Cleaning** — Removed rows with missing `CustomerID`, separated out returns (negative `Quantity`), dropped duplicates, and engineered a `TotalPrice` column (`Quantity × UnitPrice`).
2. **RFM Feature Engineering** — For each customer, calculated:
   - **Recency** — days since their last purchase
   - **Frequency** — number of distinct purchases
   - **Monetary** — total amount spent
3. **RFM Scoring & Segmentation** — Scored each customer 1–4 on each RFM dimension and combined them into segments: **Champions**, **Loyal Customers**, **At Risk / Lost**, and **Others**.
4. **SQL Analysis** — Business-question queries in PostgreSQL on the cleaned transactional data.
5. **Dashboard** — Interactive visualization of revenue trends, top countries/products, and customer segments.

## Key Findings

1. **The UK dominates revenue** — United Kingdom customers generate **~$7.29M** of the total ~$8.89M revenue (82%), with Netherlands, Ireland (EIRE), Germany, and France as the next largest markets, each well under $300K.

2. **Segments are unevenly sized but revenue is heavily concentrated** — Out of 4,339 customers: 1,267 fall into "Others," 1,114 are "Loyal Customers," 1,084 are "At Risk / Lost," and 874 are "Champions." Despite being the smallest segment by count, **Champions alone account for ~$5.89M — roughly 66% of total revenue.**

3. **Loyal Customers are the second-largest revenue driver** — contributing ~$1.46M, reinforcing that a relatively small share of customers (Champions + Loyal, ~46% of the base) drives the large majority of revenue.

4. **"At Risk / Lost" customers still represent meaningful value** — this segment contributed ~$705K historically, making win-back campaigns (targeted discounts, re-engagement emails) a worthwhile investment rather than writing these customers off.

**Business recommendation:** Retention and loyalty efforts should be prioritized around Champions and Loyal Customers to protect the ~72% of revenue they generate, while a separate, lower-cost win-back campaign should target the At Risk / Lost segment before they fully churn.

## Dashboard Screenshot

![Dashboard](dashboard_screenshot.png)

## Repository Structure

```
├── README.md                          # Project overview (this file)
├── notebooks/
│   └── 01_data_cleaning.ipynb         # Data cleaning and RFM feature engineering
├── sql/
│   └── queries.sql                    # Business-question SQL queries
├── dashboard/
│   ├── ecommerce_dashboard.pbix       # Power BI dashboard file
│   └── dashboard_screenshot.png       # Dashboard preview image
└── data/
    ├── cleaned2.csv                   # Cleaned transactional dataset
    └── rfm_segments.csv               # RFM scores and customer segments
```

## How to Reproduce

1. Clone this repository
2. Open `notebooks/01_data_cleaning.ipynb` to see the data cleaning and RFM feature engineering steps
3. Run `sql/queries.sql` against a PostgreSQL database loaded with `cleaned2.csv`
4. Open `dashboard/ecommerce_dashboard.pbix` in Power BI Desktop to explore the interactive dashboard
