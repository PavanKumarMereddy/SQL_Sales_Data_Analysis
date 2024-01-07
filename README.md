# Sales Data Analysis Project 

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


**Revenue Analysis:**

**Question:** What is the total revenue generated during the entire period covered by the dataset?
```sql
--Question: What is the total revenue generated during the entire period covered by the dataset?

SELECT  SUM(quantity_ordered * price) AS total_revenue 
FROM sales_data;
```

**Expected Outcome:** A single value representing the total revenue from sales.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/6c0c7f54-62b2-435f-a9c4-c73b6df17f96)


**Monthly Sales Trends:**

**Question:** How does sales revenue vary month by month?
```sql
--Question: How does sales revenue vary month by month?

SELECT month,  SUM(quantity_ordered * price) AS monthly_revenue 
FROM sales_data
GROUP BY month
ORDER BY monthly_revenue;
```


**Expected Outcome:** A monthly breakdown of sales revenue, showing trends or seasonality.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/bef39d46-f8c5-41de-a496-8fd599b2dcf3)


**City-wise Sales Performance:**

**Question:** Which city has the highest total sales?
```sql
--Question: Which city has the highest total sales?

SELECT city,  SUM(quantity_ordered * price) AS revenue 
FROM sales_data
GROUP BY city
ORDER BY revenue DESC
LIMIT 3;
```


**Expected Outcome:** Identification of the city with the highest sales and the corresponding sales amount.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/5d0b4adc-cf4b-4f30-982c-5cd3691db0c0)


**Order Quantity Distribution:**

**Question:** What is the distribution of order quantities? Are most orders small or large?
```sql
--Question: What is the distribution of order quantities? Are most orders small or large?

SELECT quantity_ordered AS quantity, COUNT(quantity_ordered) AS Distribution 
FROM sales_data
GROUP BY quantity_ordered
ORDER BY quantity_ordered;
```

**Expected Outcome:** A histogram or summary statistics showing the distribution of order quantities.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/137865fb-97ba-4b00-86d2-dc0a2e2336e4) ![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/10f18c53-9e80-4ec8-b6c1-5012e1b9abc2)











