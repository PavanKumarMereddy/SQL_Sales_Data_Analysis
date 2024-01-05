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
## Top-Selling Products:

## Question: What are the top 5 best-selling products in terms of quantity ordered?

--Question: How do sales vary across different regions or addresses?

--Question1: What are the top 5 best-selling products in terms of quantity ordered?

SELECT product,SUM(quantity_ordered) AS total_quantity FROM sales_data
GROUP BY product
ORDER BY total_quantity DESC
LIMIT 5

## Expected Outcome: A list of the top-selling products with their respective quantities ordered.
 
![image](https://github.com/PavanKumarMereddy/SQL_Sales_Data_Analysis/assets/155641231/6074787b-6607-4de5-b5ab-de527754487c)


Revenue Analysis:
Question: What is the total revenue generated during the entire period covered by the dataset?
1
2
3
4	--Question: What is the total revenue generated during the entire period covered by the dataset?

SELECT  SUM(quantity_ordered * price) AS total_revenue 
FROM sales_data;


Expected Outcome: A single value representing the total revenue from sales.

 


Monthly Sales Trends:
Question: How does sales revenue vary month by month?
1
2
3
4
5
6	--Question: How does sales revenue vary month by month?

SELECT month,  SUM(quantity_ordered * price) AS monthly_revenue 
FROM sales_data
GROUP BY month
ORDER BY monthly_revenue;



Expected Outcome: A monthly breakdown of sales revenue, showing trends or seasonality.

 

City-wise Sales Performance:
Question: Which city has the highest total sales?
1
2
3
4
5
6
7	--Question: Which city has the highest total sales?

SELECT city,  SUM(quantity_ordered * price) AS revenue 
FROM sales_data
GROUP BY city
ORDER BY revenue DESC
LIMIT 3;



Expected Outcome: Identification of the city with the highest sales and the corresponding sales amount.
 
Order Quantity Distribution:
Question: What is the distribution of order quantities? Are most orders small or large?
1
2
3
4
5
6	--Question: What is the distribution of order quantities? Are most orders small or large?

SELECT quantity_ordered AS quantity, COUNT(quantity_ordered) AS Distribution 
FROM sales_data
GROUP BY quantity_ordered
ORDER BY quantity_ordered;


Expected Outcome: A histogram or summary statistics showing the distribution of order quantities.
  



Average Order Value:

Question: What is the average value of an order (average order value)?

1
2
3
4	--Question: What is the average value of an order (average order value)?

SELECT AVG(sales) AS average_order_value 
FROM sales_data;






Expected Outcome: A single value representing the average order value.
 

Seasonal Sales Analysis:
Question: Are there any noticeable patterns or trends in sales during different months?
1
2
3
4
5
6	--Question: Are there any noticeable patterns or trends in sales during different months?

SELECT month, SUM(quantity_ordered * price) AS monthly_revenue
FROM sales_data
GROUP BY month
ORDER BY monthly_revenue DESC;


Expected Outcome: Visualization or summary highlighting any seasonal trends in sales.

 




Correlation Between Price and Sales:

Question: Is there a correlation between the product price and the quantity ordered?

1
2
3
4	--Question: Is there a correlation between the product price and the quantity ordered?

SELECT AVG(price) AS avg_price, AVG(quantity_ordered) AS avg_quantity
FROM sales_data;




Expected Outcome: Insights into whether higher-priced products tend to have lower quantities ordered or vice versa.

 

Customer Segmentation:

Question: Can we identify different customer segments based on their purchasing behavior?
1
 2
 3
 4
 5
 6
 7
 8
 9
10
11	--Question: Can we identify different customer segments based on their purchasing behavior?

SELECT
CASE
WHEN quantity_ordered >=7 THEN 'High'
WHEN quantity_ordered >=4 THEN 'Medium'
ELSE 'Low'
END AS customer_segment,
COUNT(*) AS customer_count
FROM sales_data
GROUP BY customer_segment;






Expected Outcome: Clusters or groups of customers with similar purchasing patterns.

 
Geographical Analysis:

Question: How do sales vary across different regions or addresses?

1
2
3
4
5	--Question: How do sales vary across different regions or addresses?

SELECT city, SUM(quantity_ordered * price) AS Revenue_by_region
FROM sales_data
GROUP BY city;




Expected Outcome: Regional analysis highlighting areas with higher and lower sales.

 
 




Data Exploration and Visualizations
•	Explored the distribution of order quantities using Piechart.
•	Visualized monthly sales trends over time.
•	Sales across different regions.

Data Cleaning and Transformation
•	Handled missing values by excluding rows with NULL in critical columns.
•	Converted the 'order_date' column to a datetime format for better analysis.
•	No significant outliers were identified.

Results and Analysis
•	Top-selling products: 
a)	AAA Batteries (4-pack)
b)	AA Batteries (4-pack)
c)	USB-C Charging Cable
d)	Lightning Charging Cable
e)	Wired Headphones.
•	Total revenue: $ 34M.
•	Monthly sales trends: 
 

## Insights and Recommendations
•	Products [AAA Batteries, AA Batteries, USB-C Charging Cable, Lightning Charging Cable, Wired Headphones] are consistently high-performing; consider targeted marketing strategies.
•	Monthly sales exhibit a seasonal pattern, with peaks during [months]. Plan promotions accordingly.

## Review and Refinement
•	Reviewed SQL queries and addressed feedback on query optimization.
•	Refinements made to visualizations for clarity.

## Challenges Faced
•	Addressed issues with NULL values in the dataset.
•	Overcame challenges related to [specific challenges].

## Next Steps
•	Explore customer segmentation based on purchasing behavior.
•	Conduct a more granular analysis of sales in specific regions.


## Conclusion
The project successfully provided insights into top-selling products, revenue trends, and monthly sales patterns. The findings can guide marketing and sales strategies for improved performance.

## References
•	No external references used.

## Code Snippets
•	Relevant code snippets for SQL queries and data visualizations are embedded within the documentation.

## File Organization
•	The project files are organized in a directory structure for clarity.

## Final Review
•	The documentation is reviewed for clarity, completeness, and correctness.

## Acknowledgments
•	No external contributions for this project.

## Portfolio Inclusion
This project showcases skills in SQL, data analysis, and visualization, making it a valuable addition to the portfolio.
