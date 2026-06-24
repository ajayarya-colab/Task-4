# Ecommerce Data Analysis using SQL (SQLite & Google Colab)

## 📌 Project Overview
This project demonstrates the use of Structured Query Language (SQL) for analyzing data in an e-commerce ecosystem. The analysis is performed within a **Google Colab Notebook** using a local **SQLite** database engine. It covers essential database concepts including data retrieval, filtering, multi-table joins, subqueries, view creation, and performance optimization via indexing.

## 🛠️ Tools & Technologies Used
* **Development Environment:** Google Colab (.ipynb)
* **Database Engine:** SQLite (In-Memory / Local file-based)
* **Libraries:** `sqlite3` for SQL execution, `pandas` for structured data representation

## 📊 Dataset Structure
The dataset consists of two primary tables containing relational data:
1. **`users` Table:** Contains customer details (`user_id`, `user_name`, `country`, `join_date`).
2. **`orders` Table:** Contains transaction details (`order_id`, `user_id`, `product_name`, `revenue`, `order_date`).

---

## 🚀 Implemented Queries & Tasks

### a & d. Aggregations & Basic Filtering (SELECT, WHERE, GROUP BY, ORDER BY)
Calculates total orders, aggregate revenue, and average order value for countries generating more than 2,000 in transaction revenue.

### b. Multi-Table Joins (LEFT JOIN)
Demonstrates data retrieval using a `LEFT JOIN` to fetch all registered users alongside their order details, ensuring customers with zero orders are not excluded from the report.

### c. Subqueries
Identifies high-value customers by filtering users whose purchase amounts exceed the platform's average order value via nested queries.

### e & f. Views & Optimization
* **View Creation:** Created a virtual representation layer named `vw_user_sales_summary` to encapsulate complex analytics for reuse.
* **Optimization:** Implemented an index (`idx_order_date`) on the transactional date column to significantly accelerate query execution times during point-lookups and range scans.

---

## 💬 Technical Interview Questions & Answers

### Q1. What is the difference between WHERE and HAVING?
* **`WHERE` clause:** Filters individual rows *before* any grouping occurs (`GROUP BY`). It cannot evaluate or be paired with aggregate functions like `SUM()` or `COUNT()`.
* **`HAVING` clause:** Filters summary rows or groups *after* the `GROUP BY` clause has been executed. It is specifically designed to work alongside aggregate metrics.

### Q2. What are the different types of joins?
* **INNER JOIN:** Returns records that have matching values in both tables.
* **LEFT JOIN (LEFT OUTER JOIN):** Returns all records from the left table, and the matched records from the right table. If no match is found, NULL values are returned for the right table's columns.
* **RIGHT JOIN (RIGHT OUTER JOIN):** Returns all records from the right table, and the matched records from the left table.
* **FULL JOIN (FULL OUTER JOIN):** Returns all records when there is a match in either left or right table records.

### Q3. How do you calculate average revenue per user in SQL?
Average Revenue Per User (ARPU) is calculated by dividing the total aggregated revenue by the absolute count of unique active users:
```sql
SELECT SUM(revenue) / COUNT(DISTINCT user_id) AS ARPU FROM orders;
