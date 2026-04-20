# 📊 Budget vs. Actual Sales Analysis - Power BI Professional Dashboard

## 📝 Project Overview
This project provides a high-level financial performance analysis, comparing **Actual Sales** against **Budgeted Targets**. It is designed to help stakeholders identify performance gaps, monitor seasonal trends, and analyze product-level contributions to overall revenue.

The dashboard transforms raw, fragmented data into actionable business intelligence using advanced Power BI techniques.

---

## 📂 Project Structure
To maintain a professional workflow, the repository is organized as follows:

* 📁 **[Power BI Report](./Power%20BI%20Report/)**: Contains the main dashboard file `Budget vs Actual.pbix`.
* 📁 **[raw data](./raw%20data/)**: The original Excel/CSV datasets used as the data source before cleaning and transformation.
* 📁 **[docs](./docs/)**: Detailed technical and business documentation:
    * `Data_Modeling.md`: Explaining the Multi-Fact Star Schema and relationships.
    * `DAX_Measures.md`: A complete library of all DAX formulas with their business logic.
    * `Business_Insights.md`: A deep-dive analysis of the sales trends and variance findings.
* 📁 **[images](./images/)**: Visual previews, screenshots of the dashboard, and the data model schema.

---

## 🛠️ Technical Deep Dive

### 1. Data Transformation 
Using **Power Query**, the data underwent a rigorous cleaning process:
* **Normalization:** Unpivoted monthly columns into a row-based format for time-series analysis.
* **Data Integrity:** Removed "Total" rows and corrected headers to prevent double-counting.
* **Structural Fixes:** Transposed the `Region` table to align geographical data vertically.
* **Date Standardization:** Developed a custom **Calendar Table** to support Time Intelligence.

### 2. Data Modeling
The model follows a **Multi-Fact Star Schema** (Fact Constellation) architecture:
* **Two Fact Tables:** `Actual Sales` and `Budget` are kept separate to manage different data granularities.
* **Shared Dimensions:** Both facts are filtered by common dimensions (`Calendar Table` and `Region`) via **1:N (One-to-Many)** relationships.
* **Optimized Filtering:** Single-direction cross-filtering ensures high performance and accurate DAX calculations.

### 3. DAX Capabilities
Advanced DAX was implemented to calculate dynamic metrics, including:
* **Time Intelligence:** YTD (Year-To-Date) and MOM (Month-Over-Month) growth.
* **Variance Analysis:** Absolute and percentage deviations from the budget.
* **Dynamic UI:** Measures like `Select Country` for interactive dashboard titles.

---

## 📈 Executive Insights
* **Target Achievement:** The company exceeded its annual budget by **1.43%**, reaching a total of **$5.72M** in sales.
* **Product Mix:** **Bikes** are the primary revenue driver (26.32%), while other categories maintain a healthy balance (approx. 24% each).
* **Performance Trends:** Significant performance spikes occurred in **January** and **June**, while **October** showed the highest volatility with a **-9.99%** MOM drop.
* **Financial Stability:** Actual YTD performance consistently stayed above Budget YTD throughout the fiscal year.

---

## 🚀 How to Explore this Project
1. **View the Dashboard:** Navigate to the [Power BI Report](./Power%20BI%20Report/) folder and download `Budget vs Actual.pbix`.
2. **Understand the Architecture:** Check [docs/Data_Modeling.md](./docs/Data_Modeling.md) to see how the tables are connected.
3. **Review the Logic:** Check [docs/DAX_Measures.md](./docs/DAX_Measures.md) for the specific formulas and calculations used.
4. **Analyze the Results:** Read the [docs/Business_Insights.md](./docs/Business_Insights.md) for a summary of the business performance and recommendations.

