# NovaBridge Financial Performance & Variance Analysis Dashboard

**Domain:** Corporate Banking Analytics · Nigerian FMCG Sector
**Tools:** Power Query · PowerPivot · DAX · Power BI

---

## The Business Problem

Nigerian Tier 1 banks collectively hold billions of naira in loan exposure to FMCG companies. When a macro shock hits, a currency devaluation, a fuel subsidy removal, a spike in inflation, relationship managers and credit analysts need to answer one urgent question fast:

> *Is our client still healthy enough to service their debt?*

The problem is that most banks still answer this question manually. A relationship manager emails the client requesting management accounts, waits days for a response, copies numbers into a spreadsheet, and builds a report. By the time the report reaches a credit committee, the data is weeks old. In a volatile macroeconomic environment like Nigeria's, weeks can be the difference between early intervention and a loan default.

This project builds the tool that solves that problem — an automated financial monitoring dashboard that tracks a corporate client's performance against budget in real time, flags early warning signals, and gives a banking team the visibility they need to act before problems escalate.

---

## The Client — NovaBridge Consumer Goods Plc

NovaBridge is a fictional mid-to-large Nigerian FMCG company modelled on the operational structure of listed consumer goods companies on the NSE. It operates across:

- **4 Divisions:** Beverages · Personal Care · Home Care · Packaged Foods
- **5 Regions:** Lagos · Abuja · Rivers · Kano · International

The company has an existing term loan with a Nigerian Tier 1 bank. The corporate banking team has tasked their Business Analyst with building a dashboard to monitor NovaBridge's monthly P&L performance against its annual budget — and to surface any deterioration in financial health early.

---

## The Nigerian Macro Context — Why This Project Matters

In mid-2023, the Nigerian government removed the longstanding fuel subsidy, triggering one of the most significant macroeconomic shocks to Nigerian businesses in recent years. The immediate effects were severe:

- Fuel prices more than doubled overnight, directly increasing logistics and distribution costs for FMCG companies across the country
- Consumer purchasing power dropped sharply as transportation costs fed into the price of everyday goods
- Manufacturing and distribution margins were squeezed from both sides — higher input costs and lower consumer demand simultaneously

Every major Nigerian FMCG company reported significant earnings pressure in the quarters that followed. Corporate banking teams at GTCO, Zenith Bank, Access Bank, UBA, and FBN Holdings were actively stress-testing their FMCG portfolios during this period.

This project models that exact scenario for FY 2024, as the sector navigates the aftermath of that shock and begins its recovery.

---

## Why Simulated Data?

Granular monthly management account data broken down by division and region is **internal and confidential** — no Nigerian FMCG company publishes this level of detail publicly. Data sources like Kaggle, the NBS, and the NSE provide annual or quarterly summaries at best, not the month-by-month divisional P&L data needed for meaningful variance analysis.

The dataset was therefore **purposefully simulated** to mirror verified real-world conditions:

- Revenue seasonality based on actual Nigerian FMCG consumption patterns — Q4 festive peak, Q1 post-holiday slowdown
- Q3 2024 revenue variance of **-16.2%** and EBITDA variance of **-39.6%** calibrated to the documented impact of fuel subsidy removal on Nigerian consumer goods companies
- Logistics cost spike in Q3 reflecting the real-world increase in PMS prices and its downstream effect on distribution costs
- Q4 recovery trajectory consistent with CBN data showing improving consumer sentiment in late 2024
- Divisional and regional structure modelled on the operational footprint of companies like PZ Cussons Nigeria, Unilever Nigeria, and Nestlé Nigeria

Simulating realistic data when real data is inaccessible — and being transparent about why — is standard practice in business analytics. More importantly, it demonstrates an understanding of the Nigerian business environment that a downloaded dataset cannot.

---

## Dataset Structure

```
data/
├── monthly_actuals/
│   ├── 01_January_2024_Actuals.csv
│   ├── 02_February_2024_Actuals.csv
│   ├── 03_March_2024_Actuals.csv
│   ├── 04_April_2024_Actuals.csv
│   ├── 05_May_2024_Actuals.csv
│   ├── 06_June_2024_Actuals.csv
│   ├── 07_July_2024_Actuals.csv
│   ├── 08_August_2024_Actuals.csv
│   ├── 09_September_2024_Actuals.csv
│   ├── 10_October_2024_Actuals.csv
│   ├── 11_November_2024_Actuals.csv
│   └── 12_December_2024_Actuals.csv
└── budget/
    └── FY2024_Budget.csv
```

All figures in **NGN '000 (thousands of Naira)**

**P&L Lines tracked:** Revenue · COGS · Gross Profit · Marketing · Salaries · Logistics · Other OpEx · Total OpEx · EBITDA

---

## Analytical Approach

**Step 1 — Data Pipeline (Power Query)**
Rather than manually copying and consolidating 12 monthly files, a Power Query ETL pipeline was built to automatically combine all monthly actuals into a single clean dataset. One click refreshes the entire model when new monthly data arrives — replacing what was previously a multi-hour manual process.

**Step 2 — Data Model (PowerPivot)**
A data model was built connecting the Actuals and Budget tables, with 12 DAX measures calculating variance, margin ratios, and performance indicators. The TREATAS function was used to pass filter context across tables without a traditional foreign key relationship — enabling accurate division-level and region-level budget comparisons.

**Step 3 — Variance Analysis (Excel PivotTables)**
Three PivotTables were built providing sliced views of performance — by Division, by Month, and by Region — giving the banking team multiple lenses through which to assess client health.

**Step 4 — Executive Dashboard (Power BI)**
A 3-page dashboard was built for stakeholder presentation, translating the underlying analysis into visual insights a relationship manager or credit committee can act on immediately.

---

## Key Findings

### Full Year Performance
| Metric | Actual | Budget | Variance |
|---|---|---|---|
| Revenue | ₦5,200,783K | ₦5,353,110K | -₦152,327K (-2.8%) |
| EBITDA | ₦1,355,700K | ₦1,481,086K | -₦125,386K (-8.5%) |

### The Q3 Shock
| Quarter | Revenue Variance | Story |
|---|---|---|
| Q1 2024 | -2.6% | Slight underperformance — seasonal |
| Q2 2024 | +2.3% | Above budget — business gaining momentum |
| **Q3 2024** | **-16.2%** | **Macro shock — fuel subsidy impact peaks** |
| Q4 2024 | +3.3% | Recovery confirmed |

August was the worst single month at **-18.8% revenue variance** against budget.

### What the Data Tells Us

All four divisions and all five regions were impacted almost identically in Q3 — uniform deterioration across the entire business. This is a critical analytical signal. When every segment moves together, it points to an **external macro cause**, not internal mismanagement or a specific product or market failure. A single underperforming division would suggest a different problem entirely.

The Q4 recovery — revenue +3.3% above budget by December — confirms that NovaBridge's underlying business model is intact. The shock was temporary and exogenous.

---

## Business Recommendation

From a corporate banking risk perspective, NovaBridge's loan serviceability profile is **low to moderate risk**.

The Q3 deterioration was macro-driven and is now reversing. Full-year revenue variance of -2.8% is within acceptable tolerance for the Nigerian macroeconomic environment of 2024. The company demonstrated operational resilience by recovering strongly in Q4 without signs of structural damage to its revenue base or cost structure.

**Recommended action:** Maintain standard monitoring cadence. Request Q1 2025 management accounts to confirm recovery trajectory. No immediate covenant review required unless Q1 2025 shows renewed deterioration.

---

## DAX Measures

```dax
Total Actual Revenue = SUM(Actuals_Data[Revenue])
Total Actual EBITDA = SUM(Actuals_Data[EBITDA])
Actual Gross Profit = SUM(Actuals_Data[Gross_Profit])
Actual EBITDA Margin = DIVIDE([Total Actual EBITDA],[Total Actual Revenue],0)
Actual GP Margin = DIVIDE([Actual Gross Profit],[Total Actual Revenue],0)
Logistics % of Revenue = DIVIDE(SUM(Actuals_Data[Logistics]),[Total Actual Revenue],0)
Total Budget Revenue = CALCULATE(SUM(Budget_Data[Revenue]),TREATAS(VALUES(Actuals_Data[Division]),Budget_Data[Division]),TREATAS(VALUES(Actuals_Data[Month_Number]),Budget_Data[Month_Number]),TREATAS(VALUES(Actuals_Data[Region]),Budget_Data[Region]))
Total Budget EBITDA = CALCULATE(SUM(Budget_Data[EBITDA]),TREATAS(...))
Revenue Variance = [Total Actual Revenue] - [Total Budget Revenue]
Revenue Variance % = DIVIDE([Revenue Variance],[Total Budget Revenue],0)
EBITDA Variance = [Total Actual EBITDA] - [Total Budget EBITDA]
EBITDA Variance % = DIVIDE([EBITDA Variance],[Total Budget EBITDA],0)
```

---

## Dashboard Pages

**Page 1 — Executive Summary**
KPI cards for Revenue, Budget, Variance, and EBITDA. Line chart showing Actual vs Budget monthly trend — the Q3 dip and Q4 recovery tell the entire story visually.

**Page 2 — P&L Variance by Division**
Clustered bar charts comparing Actual vs Budget by division and monthly variance. Summary table with full P&L metrics per division.

**Page 3 — Regional Performance**
Revenue comparison and variance % by region. Confirms the macro-driven nature of the shock — all regions affected uniformly.

---

*Built as a portfolio project demonstrating Business Analytics applied to Nigerian corporate banking and FMCG sector analysis.*
