# FMCG Commercial Sales & Profitability Dashboard (Power BI)

## Project Overview
An executive-grade commercial performance dashboard built in Power BI Desktop to analyze over **1.1 Million transaction records** across 3 years of FMCG retail sales data. 

The dashboard provides C-suite analytics for monitoring revenue velocity, operating profit margins, channel distribution efficiency, and brand-level performance tiers.

![Dashboard Preview](dashboard_preview.png)

## Data Modeling & DAX Architecture

Built using explicit DAX measures calculated over a 1M+ row fact dataset:

  - **Total Net Sales:**
  ```dax
  Total Net Sales = SUM('fmcg_sales_3years_1M_rows[1]'[net_sales])
Total Profit = SUM('fmcg_sales_3years_1M_rows[1]'[net_sales]) - SUM('fmcg_sales_3years_1M_rows[1]'[purchase_cost])
Avg Margin Pct = AVERAGE('fmcg_sales_3years_1M_rows[1]'[margin_pct])
YoY Growth Pct = 
VAR PrevYearSales = CALCULATE([Total Net Sales], SAMEPERIODLASTYEAR('fmcg_sales_3years_1M_rows[1]'[date]))
RETURN
DIVIDE([Total Net Sales] - PrevYearSales, PrevYearSales, 0)
