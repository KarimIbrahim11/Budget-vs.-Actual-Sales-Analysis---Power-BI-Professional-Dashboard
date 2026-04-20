# Data Modeling Documentation

This document describes the data architecture and the relational model used in the **Budget vs. Actual Sales** Power BI project.

## 🏗️ Architecture: Multi-Fact Star Schema
The project is built using a **Multi-Fact Star Schema** (also known as a Fact Constellation). This design is specifically chosen to handle multiple transactional processes (Actual Sales vs. Budgeted Targets) while maintaining a high-performance relational structure.

### 1. Fact Tables (Core Metrics)
The model contains two central fact tables that share common dimensions:
* **`Actual Sales`**: Stores real-time transactional data including dates, product codes, country codes, and sales values.
* **`Budget`**: Stores the financial targets assigned to specific countries and dates for performance comparison.

### 2. Shared Dimension Tables (The Context)
These tables act as the "entry points" for filtering both fact tables simultaneously:
* **`Calendar Table`**: The primary time reference used to enable Time Intelligence calculations (YTD, Previous Month). 
    * *Relationship:* **1:N (One-to-Many)** with both Fact tables.
* **`Region`**: Contains geographical attributes (`Country`, `Country Code`).
    * *Relationship:* **1:N (One-to-Many)** with both Fact tables.
* **`Product Data`**: Contains details for product categorization (`Product Name`, `Product Code`).
    * *Relationship:* **1:N (One-to-Many)** with the `Actual Sales` table.

---

## 🛠️ Technical Specifications

### Relationship Cardinality
* **One-to-Many (1:N):** This ensures that each unique attribute in a dimension filters multiple records in the fact tables, maintaining data integrity.
* **Cross-filter Direction:** Set to **Single** (from Dimension to Fact). This is a best practice to avoid ambiguity and ensure that the "Filter Flow" is predictable and efficient.

### Why Multi-Fact Star Schema?
* **Granularity Control:** Actual sales and Budget data often come at different levels of detail. Keeping them in separate facts prevents data duplication and keeps calculations accurate.
* **Seamless Comparison:** By using **Shared Dimensions** (Date and Region), we can compare Actuals vs. Budget in a single visual without needing to merge the tables, which keeps the model lightweight.

---

## 📐 Optimization Highlights
* **Marked as Date Table:** The `Calendar Table` is designated as a Date Table to support DAX Time Intelligence.
* **Measure Categorization:** A dedicated `Measure` folder is used to centralize all logic, ensuring the model remains clean and developer-friendly.

---
**Note:** This architecture ensures that any filter applied to a Country or Date will automatically and accurately affect both Actual and Budget calculations simultaneously.
