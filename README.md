# B2B Sales Funnel Analysis & KPI Visualization

## 🔗 Live File
[View the Google Sheets analysis here](https://docs.google.com/spreadsheets/d/1h0XJVs7ifAXexont5ak5eY6mV_8r-EjRN5fvz92Hi3s/edit?gid=2051915783#gid=2051915783)

## 📌 Project Overview
This project analyzes a B2B sales funnel using Google Sheets.
The goal is to give the sales team visibility into their funnel performance
and track key conversion KPIs over time.

## 🎯 Business Problem
The sales team had no visibility into their lead funnel.
They couldn't tell what was working or not, making it hard to improve their process. 

## 📊 Data Sources
Two tables from the Greenweez dataset:

| Table | Description |
|---|---|
| `funnel` | Sales process stages for each prospect (customer_id, deal stage, dates) |
| `prospect` | Priority level of each prospect (High / Medium / Low) |

**Key relationship:** Both tables are joined via `customer_id` using XLOOKUP.

## 🔧 Methodology

### Step 1 - Data Import
- Imported `funnel` and `prospect` tables as separate sheets in Google Sheets

### Step 2 - Data Enrichment (XLOOKUP)
- Added `priority` and `priority_name` columns to the funnel sheet
- Used XLOOKUP to join the two tables on `customer_id`

### Step 3 - KPI Calculation
Added 6 new columns to calculate individual KPIs per prospect:

**Conversion rate columns (0 or 1):**
- `Lead2Customers` → Did this prospect become a customer? (1=yes, 0=lost)
- `Lead2Opportunity` → Did this prospect become an opportunity? (1=yes, 0=lost)
- `Opportunity2Customers` → Did this opportunity become a customer? (1=yes, 0=lost)

**Conversion time columns (days):**
- `Lead2Customers_time` → Days from lead to customer
- `Lead2Opportunity_time` → Days from lead to opportunity
- `Opportunity2Customers_time` → Days from opportunity to customer

### Step 4 - Visualization (sales_deliverable sheet)
- Pivot table: funnel status by deal stage and priority
- Bar chart: funnel visualization
- Pivot table: KPIs by priority (conversion rates and times)

## 📈 Key Results

| Priority | Conversions | L2C Rate | L2O Rate | O2W Rate |
|---|---|---|---|---|
| High | 1279 | 28.92% | 69.61% | 50.66% |
| Low | 1251 | 30.82% | 69.09% | 55.76% |
| Medium | 1279 | 29.29% | 67.90% | 53.40% |

## 💡 Key Insights
1. **L2O rate is high (~69%)** — the team is good at getting prospects to demo stage
2. **O2W rate is around 50%** — half of demos convert to customers, room for improvement
3. **Priority levels show similar conversion rates** — prioritization may need revisiting
4. **Average sales cycle is ~12-13 days** — relatively fast

## 🛠️ Tools & Techniques
- Google Sheets
- XLOOKUP — joining two tables
- ARRAYFORMULA — applying formulas to entire columns
- IF / nested IF — conditional KPI calculation
- Pivot tables — aggregating KPIs by priority
- Charts — funnel visualization
