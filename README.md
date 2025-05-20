# 📊 Sales Trend Analysis Using Aggregations

## ✅ Objective
Analyze **monthly revenue** and **order volume** from an ecommerce-style dataset using SQL aggregation and time-based grouping.

This project demonstrates how to:
- Use SQL queries for monthly trend analysis
- Group and aggregate data by time (month/year)
- Visualize trends using Python

---

## 🛠 Tools & Technologies
- Python (Jupyter Notebook)
- SQLite (`sqlite3`)
- Pandas
- SQL (with `STRFTIME()` for date extraction)
- Matplotlib (for optional visualization)

---

## 📁 Dataset
A synthetic dataset named `online_sales` was generated with the following fields:

| Column Name | Description                   |
|-------------|-------------------------------|
| `order_id`  | Unique ID for each order      |
| `order_date`| Date the order was placed     |
| `amount`    | Revenue from the order        |
| `product_id`| ID of the product ordered     |

---

## 🔎 SQL Query Used
```sql
SELECT
  STRFTIME('%Y', order_date) AS order_year,
  STRFTIME('%m', order_date) AS order_month,
  SUM(amount) AS total_revenue,
  COUNT(DISTINCT order_id) AS order_volume
FROM
  online_sales
GROUP BY
  STRFTIME('%Y', order_date),
  STRFTIME('%m', order_date)
ORDER BY
  order_year,
  order_month;
