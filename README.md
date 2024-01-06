# Sales Data Analysis Project Documentation

## Project Overview
This project aims to analyse a sales dataset to derive insights into product performance, revenue trends, and customer behaviour. The dataset includes information such as order ID, product details, quantity ordered, prices, order date, purchase addresses, sales amounts, city, and month.

## Environment Setup
- SQL Database: PostgreSQL
- Query Tool: PgAdmin
- Visualization Tool: PgAdmin Graphic Visualiser

## Dataset Description
The dataset contains the following columns:
- orderid
- product
- quantity_ordered
- price
- order_date
- purchase_address
- sales
- city
- month

## SQL Queries
**Top-Selling Products:**

**Question:** What are the top 5 best-selling products in terms of quantity ordered?
```sql
--Question1: What are the top 5 best-selling products in terms of quantity ordered?

SELECT product, SUM(quantity_ordered) AS total_quantity FROM sales_data
GROUP BY product
ORDER BY total_quantity DESC
LIMIT 5;
```


**Expected Outcome:** A list of the top-selling products with their respective quantities ordered.
 
![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/52ac4e0d-465f-413b-ab89-7307ae3ba1f7)

