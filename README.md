# Budget vs. Actual Sales Analysis - Power BI Professional Dashboard

## 📌 Project Overview
This project focuses on a comprehensive financial analysis comparing **Actual Sales** against **Budgeted Targets**. The dashboard provides deep insights into revenue performance, product distribution, and monthly variance trends, enabling data-driven decision-making for financial planning and performance management.

## 🛠️ Data Preparation & ETL (Power Query)
The raw data required significant transformation to reach a structured format for analysis:
* **Normalization (Unpivoting):** Transformed budget and actual sales sheets by unpivoting month columns into rows to enable time-series analysis.
* **Data Cleaning:** * Removed "Quarterly Total" rows to maintain data granularity and prevent calculation errors.
    * Promoted headers and adjusted data types for consistency.
* **Transposing Data:** Fixed the `Region` table structure by transposing columns (Country ID, Country) from horizontal to vertical format.
* **Time Intelligence:** Created a dedicated **Calendar Table** to support advanced DAX calculations like YTD and MOM.

## 🏗️ Data Modeling (Star Schema)
* **Fact Tables:** `Actual Sales`, `Budget` (containing values and dates).
* **Dimension Tables:** `Product Data`, `Region`, and `Calendar Table`.
* **Measures Table:** A centralized table for all DAX measures (Actual YTD, MOM%, Variance, etc.).
* **Relationships:** Established 1:N (One-to-Many) relationships between dimensions and facts.

## 📈 Key Business Insights
1.  **Financial Achievement:** Total Actual Sales reached **$5.72M**, exceeding the Budget of **$5.64M** by **1.43%**.
2.  **Product Mix:** Revenue is well-distributed; **Bikes** lead with **26.32%**, while **Parts**, **Service & Repairs**, and **Clothing** each contribute approximately **24-25%**.
3.  **Monthly Variance:** * **January** was the peak performance month with a **+$19K** variance.
    * **November and June** followed with strong growth (**+$18K**).
    * **May** was the lowest performing month, dipping **-$4K** below target.
4.  **Trend Analysis:** The **Waterfall Chart** reveals high volatility in the second half of the year, with a significant deviation in **October (-$49K)** followed by a strong recovery in November.
5.  **Growth Stability:** The **Actual YTD** consistently outperformed the **Budget YTD**, indicating healthy year-over-year progress.

## 🚀 Technologies & Skills Used
* **Power BI Desktop**
* **Power Query (M Language):** Data cleaning, Unpivoting, and Transposing.
* **DAX (Data Analysis Expressions):** Time Intelligence (YTD, Previous Month) and Variance % calculations.
* **Data Modeling:** Star Schema design and Relationship management.

## 📂 Project Structure
* `Budget_vs_Actual.pbix`: The main Power BI file.
* `Screenshots/`: Folder containing dashboard visuals and data model images.

---
