# 🛒 E-Commerce Sales Analytics Project

> End-to-end data analytics project covering data loading, exploratory analysis, SQL querying, Power BI dashboarding, and executive reporting.

---

## 📌 Overview

This project demonstrates a complete data analytics workflow applied to an e-commerce dataset. It covers every stage of the analytics pipeline — from raw data ingestion and cleaning in Python, to SQL-based business queries, interactive Power BI dashboards, a written report, and a presentation built with Gamma.

The goal is to uncover actionable insights around customer behavior, sales performance, shipping trends, and product ratings.

---

## 📂 Dataset

| Attribute | Details |
|---|---|
| **Source** | E-Commerce Sales Dataset |
| **Format** | `.csv` |
| **Key Fields** | Customer ID, Order Date, Product Category, Purchase Amount, Shipping Type, Subscription Status, Review Rating |
| **Size** | 3900 rows for 407KB |

---

## 🛠️ Tools & Technologies

| Layer | Tool |
|---|---|
| **Language** | Python 3.x |
| **Data Analysis** | Pandas, NumPy |
| **Visualization (EDA)** | Matplotlib, Seaborn |
| **Database** | PostgreSQL / MySQL / SQL Server |
| **SQL Client** | pgAdmin / MySQL Workbench / SSMS |
| **Dashboard** | Microsoft Power BI |
| **Report** | Microsoft Word / PDF |
| **Presentation** | Gamma |
| **Version Control** | Git & GitHub |

---

## 🔄 Project Workflow

```
Raw Data (.csv)
     │
     ▼
Python (EDA & Cleaning)
     │
     ▼
SQL Database (Querying & Aggregation)
     │
     ▼
Power BI (Dashboard)
     │
     ▼
Report + Presentation
```

---

## 📋 Steps

### 1. 🐍 Load Dataset in Python

- Imported the dataset using `pandas`
- Previewed structure with `.head()`, `.info()`, `.describe()`
- Checked data types, column names, and record count

```python
import pandas as pd

df = pd.read_csv("ecommerce_data.csv")
print(df.shape)
df.head()
```

---

### 2. 🔍 Exploratory Data Analysis (EDA)

- Analyzed distribution of Purchase Amount, Review Ratings, and Customer demographics
- Visualized category-wise sales and shipping type breakdown
- Identified patterns in subscription vs non-subscription customers
- Plotted correlations between key numeric variables

```python
import matplotlib.pyplot as plt
import seaborn as sns

sns.histplot(df['Purchase Amount (USD)'], bins=30)
plt.title("Distribution of Purchase Amount")
plt.show()
```

---

### 3. 🧹 Data Cleaning

- Handled missing values using `.isnull()` checks
- Removed duplicate records
- Standardized column names (lowercase, underscores)
- Converted date columns to `datetime` format
- Fixed inconsistent category labels

```python
df.dropna(inplace=True)
df.drop_duplicates(inplace=True)
df.columns = df.columns.str.lower().str.replace(" ", "_")
df['order_date'] = pd.to_datetime(df['order_date'])
```

---

### 4. 🗄️ SQL Queries (PostgreSQL / MySQL / SQL Server)

Loaded the cleaned dataset into the database and ran business queries:

```sql
-- Total revenue by product category
SELECT category, ROUND(SUM(purchase_amount), 2) AS total_revenue
FROM ecommerce
GROUP BY category
ORDER BY total_revenue DESC;

-- Average review rating by shipping type
SELECT shipping_type, ROUND(AVG(review_rating), 2) AS avg_rating
FROM ecommerce
GROUP BY shipping_type;

-- Top 10 customers by spend
SELECT customer_id, SUM(purchase_amount) AS total_spent
FROM ecommerce
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 10;

-- Subscription vs non-subscription revenue
SELECT subscription_status, COUNT(*) AS orders, SUM(purchase_amount) AS revenue
FROM ecommerce
GROUP BY subscription_status;
```

---

### 5. 📊 Power BI Dashboard

Built an interactive single-page dashboard in Power BI with the following visuals:

| Visual | Metric |
|---|---|
| KPI Cards | Total Customers, Avg. Purchase Amount, Avg. Review Rating |
| Donut Chart | Sales by Category |
| Clustered Bar Chart | Revenue by Shipping Type |
| Clustered Column Chart | Orders by Month / Category |
| Slicers | Shipping Type, Subscription Status |

📁 File: `E-Commerce_Dashboard.pbix`

---

### 6. 📝 Report

A structured written report summarizing:
- Project objectives
- Key findings from EDA and SQL analysis
- Dashboard insights
- Recommendations for business stakeholders

📁 File: `E-Commerce_Report.pdf`

---

### 7. 🎤 Presentation (Gamma)

A clean, visual presentation created using [Gamma](https://gamma.app) covering:
- Project background
- Data overview
- Key metrics and charts
- Insights and next steps

📁 File / Link: *(add Gamma link or exported PDF here)*

---

## 📈 Key Results

- 📦 **Top-selling category** identified with highest revenue contribution
- 🚚 **Shipping type** with best average customer review rating surfaced
- 👥 **Subscribed customers** showed higher average spend compared to non-subscribers
- ⭐ **Review ratings** correlated with specific product categories and shipping methods
- 🔝 **Top 10 high-value customers** identified for targeted marketing

> *(Replace these with your actual findings after analysis)*

---

## 🚀 How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2
```

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/your-username/ecommerce-analytics.git
cd ecommerce-analytics

# 2. Run EDA and cleaning
jupyter notebook notebooks/eda_cleaning.ipynb

# 3. Load data into database
python scripts/load_to_db.py

# 4. Run SQL queries
# Open pgAdmin / MySQL Workbench / SSMS and execute files in /sql/

# 5. Open Power BI dashboard
# Open E-Commerce_Dashboard.pbix in Power BI Desktop
```

---

## 📁 Repository Structure

```
ecommerce-analytics/
│
├── data/
│   └── ecommerce_data.csv
│
├── notebooks/
│   └── eda_cleaning.ipynb
│
├── sql/
│   ├── revenue_by_category.sql
│   ├── avg_rating_by_shipping.sql
│   └── top_customers.sql
│
├── dashboard/
│   └── E-Commerce_Dashboard.pbix
│
├── report/
│   └── E-Commerce_Report.pdf
│
├── presentation/
│   └── E-Commerce_Presentation.pdf
│
└── README.md
```

---

## 👤 Purusothaman S

**Your Name**
📧 s.purusothaman1234@gmail.com
🔗 [LinkedIn] https://www.linkedin.com/in/purusothaman-s-8450a4373 | [GitHub](https://github.com/PURUSOTH-2005)

---

## 📄 License

This project is for educational and portfolio purposes.
