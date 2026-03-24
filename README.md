# SuperSmart Mortgage Strategy Model

**An Australian tax‑optimised mortgage repayment strategy model**

This Excel‑based tool models the interaction between salary sacrifice to superannuation, an offset account, and annual principal sweeps to accelerate mortgage payoff while maximising lifetime tax savings. It is designed for dual‑persona households and provides a side‑by‑side comparison of three mortgage strategies.

---

## 📌 Overview

The SuperSmart strategy works in three coordinated stages each financial year:

1. **Salary Sacrifice to Super (Tax Reduction)**  
   Each persona redirects pre‑tax income into superannuation up to their concessional cap (including carry‑forward from unused prior years). This reduces taxable income from the marginal rate (up to 47% incl. Medicare) to the 15% super contributions tax — saving up to 32 cents per dollar contributed.

2. **Offset Account Accumulation (Interest Reduction)**  
   The tax‑saved funds are deposited into a mortgage offset account each pay period. While in offset, the balance directly reduces the effective mortgage principal that accrues interest.

3. **Annual Sweep to Mortgage (Principal Acceleration)**  
   At the end of each financial year, the accumulated offset balance is swept as a lump‑sum extra repayment against the loan principal. This permanently reduces the outstanding balance, creating a compounding effect.

---

## ✨ Key Features

- Dual‑persona tax modelling (different incomes, ages, retirement horizons)
- Three‑scenario mortgage comparison:  
  - **A** – No strategy (baseline)  
  - **B** – Extra after‑tax repayments  
  - **C** – SuperSmart with offset + annual sweep
- Carry‑forward concessional cap utilisation with 5‑year rolling tracker and spousal transfers
- Division 293 high‑earner surcharge modelling and Medicare levy integration
- Monthly‑granularity offset account with automatic annual sweep
- Inflation‑adjusted projections with dynamic SG rate and concessional cap indexation
- 28 advanced DAX measures ready for Power BI dashboarding
- Executive dashboard with KPI scorecards and 6 charts

---

## 🚀 How to Use

### Step 1 – Enter Client Details
Go to the **Input** sheet. Update the blue‑text cells in sections ①–⑤:  
- Gross incomes, ages, super balances, carry‑forward balances  
- Loan amount, interest rate, loan term  
- Leave green‑text (formula) cells untouched.

### Step 2 – Verify Tax Calculation
Check the **Tax Helper** sheet – confirm marginal rates and tax payable match the client’s latest tax assessment. The "WITH SuperSmart" section shows the reduced taxable income after salary sacrifice.

### Step 3 – Review the Dashboard
Navigate to **Dashboard** for the executive summary. The 4 KPI cards show headline metrics. Scroll down for:
- Loan trajectory chart (3 scenarios)
- Cumulative tax saved
- Super growth
- Contribution breakdown

### Step 4 – Deep‑Dive with Measures
The **Measures** sheet provides 28 KPIs with descriptions. Use these to answer client questions like:
- *What’s my break‑even super return?*
- *How much risk is front‑loaded in Year 1?*
- *What’s the real benefit after inflation?*

### Step 5 – Scenario Analysis
Adjust Input parameters to test scenarios: change interest rate, super return, or inflation rate and watch all sheets recalculate. Compare the Dashboard before/after to quantify impact.

### Step 6 – Export to Power BI (Optional)
Column D of the **Measures** sheet contains valid Power BI DAX measures. To use:
1. Import this workbook into Power BI via `Get Data > Excel`
2. Create relationships between **Input**, **YearlySummary**, and **Loan** tables
3. Copy each DAX formula from column D into a new measure in Power BI Desktop.

---

## 📁 Sheets Guide

| Sheet | Purpose |
|-------|---------|
| **Dashboard** | Executive summary with KPI scorecards and visualisations. All values are formula‑linked – changes to Input flow through automatically. |
| **Measures** | 28 advanced KPIs across 4 categories: Strategy Efficiency, Mortgage Acceleration, Super & Wealth, Risk & Sensitivity. Each row has the computed value, plain‑English description, and a copy‑pasteable Power BI DAX measure. |
| **Input** | All client‑specific parameters: incomes, ages, super balances, carry‑forward, mortgage terms, SG rate, Div 293 threshold, inflation. Blue = change per client, yellow = system assumptions, green = formula‑derived. Live preview panel shows real‑time impacts. |
| **Tax Helper** | Australian marginal tax table with Medicare levy. Calculates tax payable with and without the strategy for both personas. Produces headline figures: 'Year 1 Tax Saved' and 'Lifetime Tax Saved'. Uses ATO 2024–25 tax brackets. |
| **PersonaA / PersonaB** | Monthly‑granularity salary sacrifice calculators. Tracks base pre‑tax contribution, carry‑forward allowance, actual contribution, tax saved per period, cumulative YTD totals. Handles carry‑forward burn sequence and spousal transfer logic. |
| **Loan** | Full monthly amortisation for all three scenarios side‑by‑side. Includes a comparison summary table showing total interest paid, payoff periods, interest saved, and time saved for each scenario. |
| **Offset** | Tracks monthly deposits from both personas into the offset account. Accumulates through the year, then sweeps to zero at year‑end. Records peak balance per period and interest saved before the sweep. |
| **YearlyParamsA / YearlyParamsB** | Yearly rollup of superannuation parameters: concessional cap progression, carry‑forward balance tracking, employer SG, Division 293 income test, and net personal contribution after transfers. |
| **YearlySummary** | Central data hub – one row per projection year with 34 columns covering contributions, tax saved, super balances, loan balances, interest saved, sweep amounts, offset peak, employer SG, carry‑forward remaining, Div 293 tax, and savings rates. Feeds the Dashboard and Measures. |

---

## 📐 Key Assumptions

- **Tax brackets**: ATO 2024–25 rates (incl. Stage 3 tax cuts). Medicare levy 2%.
- **Concessional cap**: $32,500 base, indexed $2,500 every 2 years.
- **Carry‑forward**: 5‑year rolling window. Available only if total super < $500K.
- **Super returns**: 7% p.a. gross (before 15% earnings tax inside fund).
- **Inflation**: 2.5% p.a. applied to incomes and contribution capacity.
- **Spousal transfer**: Enabled by default – when one persona exhausts their concessional room, excess personal contributions are redirected to the other persona’s available cap.
- **Offset sweep**: Annual frequency at end of financial year (June 30).

---

## 🔁 Data Flow & Formula Chain

Every output is formula‑driven. Change any input and all 11 sheets recalculate.
