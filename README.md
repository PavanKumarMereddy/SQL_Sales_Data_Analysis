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


**Average Order Value:**

**Question:** What is the average value of an order (average order value)?
```sql
--Question: What is the average value of an order (average order value)?

SELECT AVG(sales) AS average_order_value 
FROM sales_data;
```

**Expected Outcome:** A single value representing the average order value.

 ![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/6e940266-120d-4eda-8f80-df7a4a05a1bb)


**Seasonal Sales Analysis:**

**Question:** Are there any noticeable patterns or trends in sales during different months?
```sql
--Question: Are there any noticeable patterns or trends in sales during different months?

SELECT month, SUM(quantity_ordered * price) AS monthly_revenue
FROM sales_data
GROUP BY month
ORDER BY monthly_revenue DESC;
```

**Expected Outcome:** Visualization or summary highlighting any seasonal trends in sales.


![graph_visualiser-1704441464580](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/36ada37f-c539-45bc-b782-da73931ff2a5)


**Correlation Between Price and Sales:**

**Question:** Is there a correlation between the product price and the quantity ordered?
```sql
--Question: Is there a correlation between the product price and the quantity ordered?

SELECT AVG(price) AS avg_price, AVG(quantity_ordered) AS avg_quantity
FROM sales_data;
```


**Expected Outcome:** Insights into whether higher-priced products tend to have lower quantities ordered or vice versa.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/a8859045-1b6d-4429-8f8c-390ea57c911e)


**Customer Segmentation:**

**Question:** Can we identify different customer segments based on their purchasing behavior?
```sql
--Question: Can we identify different customer segments based on their purchasing behavior?

SELECT
CASE
WHEN quantity_ordered >=7 THEN 'High'
WHEN quantity_ordered >=4 THEN 'Medium'
ELSE 'Low'
END AS customer_segment,
COUNT(*) AS customer_count
FROM sales_data
GROUP BY customer_segment;
 ```

**Expected Outcome:** Clusters or groups of customers with similar purchasing patterns.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/2ea37626-eaaa-4625-a3fd-b5d14ae6595e)


**Geographical Analysis:**

**Question:** How do sales vary across different regions or addresses?
```sql
 --Question: How do sales vary across different regions or addresses?

SELECT city, SUM(quantity_ordered * price) AS Revenue_by_region
FROM sales_data
GROUP BY city;
```

**Expected Outcome:** Regional analysis highlighting areas with higher and lower sales.

![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/45a30026-28f5-4707-ac3c-67c296244218)
![graph_visualiser-1704454623376](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/e3fc2b9f-8ce0-4eea-8ea8-c636e6a761e8)


## Data Exploration and Visualizations
```
•	Explored the distribution of order quantities using Piechart.
•	Visualized monthly sales trends over time.
•	Sales across different regions.
```

## Data Cleaning and Transformation
```
•	Handled missing values by excluding rows with NULL in critical columns.
•	Converted the 'order_date' column to a datetime format for better analysis.
•	No significant outliers were identified.
```

## Results and Analysis
**Top-selling products:** 
```
a)	AAA Batteries (4-pack)
b)	AA Batteries (4-pack)
c)	USB-C Charging Cable
d)	Lightning Charging Cable
e)	Wired Headphones.
```
**Total revenue:** **$ 34M**
>Total Revenue $34 Million

**Monthly sales trends** 
![graph_visualiser-1704455263310](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/cf643de4-dcad-45ae-b9b3-af5af948bd1f)

## Insights and Recommendations

* Products `AAA Batteries`, `AA Batteries`, `USB-C Charging Cable`, `Lightning Charging Cable`, `Wired Headphones` are consistently high-performing; consider targeted marketing strategies.

* Monthly sales exhibit a `seasonal pattern`, with peaks during `Jan - Dec` . Plan promotions accordingly.

## Review and Refinement

*	Reviewed `SQL queries` and addressed feedback on query optimization.

*	Refinements made to visualizations for clarity.

## Challenges Faced

*	Addressed issues with `NULL` values in the dataset.

*	Overcame challenges related to `Data Import`, `Organising`, `Quering`.

## Next Steps

*	Explore customer segmentation based on purchasing behavior.

*	Conduct a more granular analysis of sales in specific regions.


## Conclusion

* The project successfully provided insights into `top-selling products`, `revenue trends`, and `monthly sales patterns`. The findings can guide marketing and sales strategies for improved performance.

## References

*	No external references used.

## Code Snippets

*	Relevant code snippets for `SQL queries` and data `visualizations` are embedded within the documentation.

## File Organization

*	The `project` files are organized in a directory structure for clarity.

## Final Review

*	The documentation is reviewed for clarity, completeness, and correctness.

## Acknowledgments

*	No external contributions for this project.

## Portfolio Inclusion

This project showcases skills in `SQL`, `data analysis`, and `visualization`, making it a valuable addition to the portfolio.





















