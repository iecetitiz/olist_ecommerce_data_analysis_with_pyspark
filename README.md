# 🛒 Olist E-Commerce Data Analysis with PySpark

An end-to-end data analysis project on the **Brazilian Olist E-Commerce dataset**, built with **PySpark** and structured around a **medallion architecture** (Bronze → Silver). The project covers data preprocessing, cleaning, and exploratory data analysis (EDA) across 8 interconnected datasets.

---

## 📁 Project Structure

```
olist-ecommerce-pyspark/
│
├── olist_ecommerce_preprocessing.ipynb   # Data cleaning & Silver layer creation
├── olist_ecommerce_eda.ipynb             # Exploratory Data Analysis
└── README.md
```

---

## 🗂️ Dataset Overview

The project uses the **Olist Brazilian E-Commerce** public dataset, which contains ~100K orders placed between 2016–2018.

| Dataset | Description |
|---|---|
| `olist_customers` | Customer info (ID, city, state, zip code) |
| `olist_orders` | Order status and timestamps |
| `olist_order_items` | Products per order with pricing |
| `olist_order_payments` | Payment methods and values |
| `olist_order_reviews` | Customer review scores and comments |
| `olist_products` | Product dimensions and category |
| `olist_sellers` | Seller location info |
| `olist_geolocation` | Brazilian zip code coordinates |

---

## ⚙️ Tech Stack

- **PySpark** — distributed data processing
- **Python 3.12** — core language
- **Pandas** — local display and inspection
- **Parquet** — efficient columnar storage for the Silver layer
- **Jupyter Notebook** — interactive development environment

---

## 🔄 Pipeline Overview

### 1️⃣ Preprocessing (`olist_ecommerce_preprocessing.ipynb`)

Transforms raw CSV data (Bronze) into a clean, reliable Silver layer.

**What's done:**
- ✅ Defined explicit schemas (e.g., zip codes as `StringType` to preserve leading zeros)
- ✅ Identified and handled `NULL` values and duplicate records
- ✅ Standardized geographic data — city names and state codes
- ✅ Validated logical consistency across datasets
- ✅ Saved all cleaned tables to **Silver Layer** in Parquet format

### 2️⃣ EDA (`olist_ecommerce_eda.ipynb`)

Loads the Silver layer datasets and performs analytical queries to uncover business insights.

**Key analyses:**
- 📦 Order volume and status distribution
- 🗺️ Customer distribution by state and city
- 💳 Most popular payment methods per product category
- 🏆 Top-selling product categories by transaction count
- ⭐ Review score patterns

---

## 🚀 Getting Started

### Prerequisites

- Apache Spark (local mode)
- Python 3.10+
- Jupyter Notebook or JupyterLab

### Run the Notebooks

```bash
# 1. Start with preprocessing to build the Silver layer
jupyter notebook olist_ecommerce_preprocessing.ipynb

# 2. Then run EDA on the cleaned data
jupyter notebook olist_ecommerce_eda.ipynb
```

> **Note:** Update the dataset paths in the notebooks to match your local environment. Default path: `/opt/examples/datasets/brazilian_ecommerce/`

---

## 💡 Key Insights

| # | Category | Insight |
|---|---|---|
| 1 | 📦 Total Orders | The platform processed **99,441 orders** in total across 2016–2018. |
| 2 | 📈 Growth | Order volume grew ~65× — from **325 orders in Q4 2016** to **21,208 in Q1 2018**. |
| 3 | 💰 Revenue Peak | Quarterly revenue peaked at **R$3.33M in Q2 2018**, up from just R$54K in Q4 2016. |
| 4 | 🗓️ Busiest Month | **November 2017** had the highest single-month volume with **7,544 orders**, driven by Black Friday. |
| 5 | 📅 Seasonal Pattern | **August, May, and July** are consistently the highest-order months across years. |
| 6 | 🛍️ Top Category | **Health & Beauty** was the #1 selling category in 2018 with **5,924 items sold**. |
| 7 | 💳 Payment Method | **Credit card** dominates as the top payment method in **73 out of 74** product categories. |
| 8 | 💳 Avg Spend by Payment | Credit card orders average **R$163.94**, the highest of all payment types. |
| 9 | 🧾 Voucher Users | Voucher payments have the lowest average order value at **~R$98 per order**. |
| 10 | 🛒 Basket Size | The average order contains only **1.14 items**, suggesting most customers buy one item at a time. |
| 11 | 💎 Highest AOV Category | **Computers** has the highest average order value at **~R$1,095** (price + freight). |
| 12 | 🌸 Lowest AOV Category | **Flowers** and **Home Comfort 2** have the lowest average order values at ~R$38 and ~R$32. |
| 13 | 🏪 Seller Count | There are **3,095 registered sellers** on the platform, mostly concentrated in **São Paulo**. |
| 14 | 👥 Customer Base | **99,441 customers** are registered, with São Paulo state representing the largest share. |
| 15 | 🗺️ Geolocation Scale | The geolocation dataset contains **1,000,163 coordinate records** across Brazilian zip codes. |

---

## 📌 Data Architecture

```
📂 Bronze Layer (Raw CSVs)
        ↓  schema definition + cleaning
📂 Silver Layer (Cleaned Parquet files)
        ↓  joins + aggregations
📊 EDA & Insights
```

---

## 🙌 Acknowledgements

Dataset sourced from [Olist](https://olist.com/) via [Kaggle — Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).
