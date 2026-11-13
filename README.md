# customer-shopping-behavior-analysis
End-to-end Customer Shopping Behavior Analysis using Python (Pandas/ETL), PostgreSQL, and Power BI to uncover customer segmentation, discount sensitivity, and revenue drivers across 3,900 transactions. 

# 🛍️ Customer Shopping Behavior Analysis (Python | SQL | Power BI)

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql)
![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-F2C811?logo=powerbi)
![Pandas](https://img.shields.io/badge/Library-Pandas-150458?logo=pandas)
![License](https://img.shields.io/badge/License-MIT-green)

An end-to-end retail data analytics project analyzing customer shopping trends, purchasing behavior, demographic drivers, and loyalty patterns across **3,900 customer records** generating **$233,081 in revenue**. 

This repository demonstrates the complete data analytics lifecycle: **Data Extraction & Cleaning (Python) ➔ Relational Database Ingestion ➔ Business Intelligence Queries (PostgreSQL) ➔ Interactive Executive Reporting (Power BI)**.

---

## 📌 Project Architecture & Workflow


---

## 📊 Key Business Insights & Findings

| Area | Analytical Finding | Business Implication |
|---|---|---|
| **Customer Retention** | **79.9% (3,116 customers)** are classified as **Loyal** (>10 previous orders). | High brand loyalty indicates strong organic satisfaction and retention. |
| **Subscription Gap** | Only **27.56% of repeat buyers** have an active subscription; average order value is identical ($59.49 vs $59.87). | The subscription model lacks compelling incentives (free shipping/VIP discounts) to monetize existing customer loyalty. |
| **Gender Distribution** | Males drive **67.74% ($157.9K)** of revenue vs. **32.26% ($75.2K)** for females, yet spend per order is nearly identical ($59.54 vs $60.25). | Growth opportunity: Targeted female-focused acquisition campaigns can balance revenue distribution. |
| **Discount Efficiency** | **50.03%** of customers who received discounts still spent **above average ($59.76)**. | Promotional discounting successfully drives basket sizes without devaluing spend. |
| **Product Demand** | **Clothing** dominates total revenue (**44.73%**, $104.3K), followed by **Accessories (31.83%)**, **Footwear (15.49%)**, and **Outerwear (7.95%)**. | Inventory prioritization should focus on staple categories (Blouses, Pants, Jewelry, Belts). |

---

## 📁 Repository Structure


---

## 🛠️ Step-by-Step Implementation

### Step 1: Data Cleaning & Feature Engineering (Python)
* File: `01-Customer-Shopping-Behavior-Analysis.ipynb`
* **Handling Missing Values**: Imputed 37 missing `Review Rating` values using the **category median rating**.
* **Standardization**: Converted all column headers to `snake_case` for SQL compatibility.
* **Feature Engineering**:
  * Created `age_group` using quartile binning (`qcut`): *Young Adult (18-31)*, *Adult (32-44)*, *Middle-aged (45-57)*, and *Senior (58-70)*.
  * Mapped string purchase frequencies to numerical days (`Weekly` $\rightarrow$ 7, `Monthly` $\rightarrow$ 30, `Annually` $\rightarrow$ 365).
  * Removed redundant columns (`promo_code_used` was 100% identical to `discount_applied`).
* **Database Ingestion**: Loaded the prepared dataset into PostgreSQL using `SQLAlchemy`.

### Step 2: Business Logic & Queries (PostgreSQL)
* File: `02_Customer_Shopping_Behavior_Analysis.sql`
* Explored 10 critical business questions:
  1. Gender revenue contribution comparison.
  2. High-value discount users spending above average order value.
  3. Top 5 highest rated products by average review score.
  4. Standard vs. Express shipping spend difference.
  5. Subscription status vs. spend and revenue share.
  6. Products with the highest discount dependency.
  7. Customer segmentation (`New`, `Returning`, `Loyal`) using Common Table Expressions (CTEs).
  8. Top 3 best-selling products per category using `ROW_NUMBER() OVER (PARTITION BY...)`.
  9. Subscription adoption rate among repeat buyers (>5 purchases).
  10. Revenue distribution by age quartile.

### Step 3: Interactive Dashboard (Power BI)
* File: `03_customer_Shopping_behavior_dashboard.pbix`
* **Executive KPIs**: Total Sales ($233.1K), Total Orders (3,900), Average Spend ($59.76), Average Rating (3.75).
* **Interactive Slicers**: Filter data dynamically by Season, Subscription Status, Shipping Type, and Location.
* **Charts & Visuals**: Demographic breakdown, Category revenue shares, and Product ratings.

---

## 🚀 How to Run Locally

### Prerequisites
* Python 3.9+
* PostgreSQL & pgAdmin
* Power BI Desktop

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/Customer_Shopping_Behavior_Analysis.git
cd Customer_Shopping_Behavior_Analysis

2. Install dependencies & run notebook
bash
pip install pandas numpy sqlalchemy psycopg2-binary jupyter
jupyter notebook 01-Customer-Shopping-Behavior-Analysis.ipynb
3. Run SQL Analysis

Open 02_Customer_Shopping_Behavior_Analysis.sql in pgAdmin or your favorite SQL editor and execute the queries against the customer table.

4. View Dashboard

Open 03_customer_Shopping_behavior_dashboard.pbix in Power BI Desktop to interact with the visualizations.
