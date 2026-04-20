# DAX Measures Documentation

This document contains a comprehensive list of all DAX measures and calculated tables developed for the **Budget vs. Actual Sales** Power BI report.

## 🛠️ Measures & Calculations

| Measure Name | DAX Formula | Description |
| :--- | :--- | :--- |
| **Total Actual** | `SUM('Actual Sales'[Value])` | Calculates the total sum of actual sales recorded. |
| **Total Budget** | `SUM(Budget[Value])` | Calculates the total sum of budgeted targets. |
| **Actual Previous Month** | `CALCULATE([Total Actual], DATEADD('Calendar Table'[Date],-1,MONTH))` | Calculates the total actual sales for the previous month using time intelligence. |
| **Actual Month Dev** | `[Total Actual]-[Actual Pervious Month]` | Calculates the absolute difference (deviation) between the current month and the previous month. |
| **Actual MOM%** | `DIVIDE([Actual month Dev], [Actual Pervious Month], 0)` | Calculates the Month-over-Month growth percentage safely using the DIVIDE function. |
| **Actual YTD** | `TOTALYTD([Total Actual],'Calendar Table'[Date])` | Calculates the running total of actual sales from the beginning of the fiscal year. |
| **Budget YTD** | `TOTALYTD([Total Budget],'Calendar Table'[Date])` | Calculates the running total of the budget from the beginning of the fiscal year. |
| **Variance Value** | `[Total Actual] - [Total Budget]` | Calculates the gap between actual achievement and the set budget. |
| **Variance %** | `DIVIDE([variance value], [Total Budget], 0)` | Calculates the percentage of variance relative to the budget. |
| **Select Country** | `IF(ISFILTERED(Region[Country]), VALUES(Region[Country]), "All Counties")` | A dynamic measure used for dashboard titles to display the selected country or a default text. |

## 📅 Calculated Tables

| Table Name | DAX Formula | Description |
| :--- | :--- | :--- |
| **Calendar Table** | `CALENDAR(MIN(MIN('Actual Sales'[Date]), MIN(Budget[Date])), MAX(MAX('Actual Sales'[Date]), MAX(Budget[Date])))` | Generates a continuous date table covering the full range of both Actual and Budget data. |

---
**Technical Note:** All Time Intelligence measures require the `Calendar Table` to be marked as a Date Table in Power BI and connected via a 1:N relationship to the Fact tables.
