# romisqlproj
Lush Sales Analysis SQL Project
Project Overview
Project Title: Lush Sales Analysis
Level: Intermidiate
Database: romis
This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. This project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.

Objectives
1.Set up a retail sales database: Create and populate a retail sales database with the provided sales data.
2.Data Cleaning: Identify and remove any records with missing or null values.
3.Exploratory Data Analysis (EDA): Perform basic exploratory data analysis to understand the dataset.
4.Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.

Project Structure

1. Database Setup

Database Creation: The project starts by creating a database named romis.

Table Creation: A table named [dbo].[monie works111csv]  is created to store the sales data. The table structure includes columns for Index, Order ID, Custumer ID, Gender, Age, Age Group, Date, Month, Status, Channel, Category, Size, Amount, Ship city, Ship state, Ship postal code.

CREATE DATABASE romis;

CREATE TABLE [dbo].[monie works111csv]
(
index INT PRIMARY KEY,
order_ID INT,
Cust_ID INT,
Gender VARCHAR(10),
Age INT,
Age_Group VARCHAR,
Date DATE,
Month VARCHAR,
Status VARCHAR,
Channel VARCHAR,
Category VARCHAR,
Size VARCHAR,
Amount FLOAT,
ship_city VARCHAR,
ship_state VARCHAR,
ship_postal_code INT
);

2. Data Exploration & Cleaning
Record Count: Determine the total number of records in the dataset.
Customer Count: Find out how many unique customers are in the dataset.
Category Count: Identify all unique product categories in the dataset.
Channel Types: Identify all the channels used in the dataset.
Null Value Check: Check for any null values in the dataset and delete records with missing data.



SELECT COUNT (*) as total_sales from [dbo].[monie works111csv];

SELECT COUNT(DISTINCT Cust_ID) as unique_customers from [dbo].[monie works111csv];

SELECT DISTINCT category from [dbo].[monie works111csv];

SELECT DISTINCT category from [dbo].[monie works111csv;

SELECT * FROM [dbo].[monie works111csv]
WHERE
Index NULL OR Order_ID IS NULL OR Cust_ID IS NULL OR Gender IS NULL OR Age IS NULL OR Age Group IS NULL OR 
Date IS NULL OR Month IS NULL OR Status IS NULL OR
Channel IS NULL OR Category IS NULL OR Size IS NULL OR
Amount IS NULL OR Ship city IS NULL OR 
Ship state IS NULL OR Ship_postal_code IS NULL;

DELETE FROM [dbo].[monie works111csv]
WHERE 
Index NULL OR Order_ID IS NULL OR Cust_ID IS NULL OR Gender IS NULL OR Age IS NULL OR Age Group IS NULL OR 
Date IS NULL OR Month IS NULL OR Status IS NULL OR
Channel IS NULL OR Category IS NULL OR Size IS NULL OR
Amount IS NULL OR Ship city IS NULL OR 
Ship state IS NULL OR Ship_postal_code IS NULL;

3. Data Analysis & Findings
The following SQL queries were developed to answer specific business questions:

Q1. Write a SQL query to retrieve all columns for sales made on '2022-12-04:

SELECT *
FROM [dbo].[monie works111csv]
WHERE date = '2022-12-04';

Q2. Write a SQL query to retrieve all columns for sales made BETWEEN '2022-12-04' AND '2022-12-07:

SELECT TOP 1000 * FROM [dbo].[monie works111csv]
WHERE DATE BETWEEN '2022-12-04' AND '2022-12-07';

Q3. Write a SQL query to retrieve all transactions where category is 'Set' and the amount is more than 500 the month of Dec 5-6:

SELECT * FROM [dbo].[monie works111csv]
WHERE CATEGORY = 'Set' AND AMOUNT > 500 
AND DATE BETWEEN '2022-12-05' AND '2022-12-07';

Q4. Write a SQL query to retrieve all transactions where category is 'Kurta' and the amount is more than 500 in the month of Dec 5-6:

SELECT * FROM [dbo].[monie works111csv]
WHERE CATEGORY = 'Kurta' AND AMOUNT > 500 
AND DATE BETWEEN '2022-12-05' AND '2022-12-07';

Q5. Write a SQL query to retrieve all transactions where category is 'Top' and the amount is more than 300 the month of Dec 6:

SELECT * FROM [dbo].[monie works111csv]
WHERE CATEGORY = 'Top' AND AMOUNT > 300 
AND DATE = '2022-12-06';

Q6. Write a SQL query to calculate the total sales as (net_sale) for each category:

SELECT 
CATEGORY, SUM (Amount) as net_sale 
FROM [dbo].[monie works111csv]
GROUP BY CATEGORY;

Q7. Write a SQL query to calculate the total sales as (Channel_net_sale) for each Channel:

SELECT 
Channel, SUM (Amount) as Channel_net_sale 
FROM [dbo].[monie works111csv]
GROUP BY CHANNEL;

Q8. Write a SQL query to calculate the total sales as (SHIPCITY_net_sale) for each Ship_city:

SELECT 
Ship_city, SUM (Amount) as SHIPCITY_net_sale 
FROM [dbo].[monie works111csv]
GROUP BY Ship_city;

Q9. Write a SQL query to calculate the total sales as (SHIPSTATE_sale) for each Ship_state:

SELECT Ship_state, SUM (Amount) as SHIPSTATE_net_sale 
FROM [dbo].[monie works111csv]
GROUP BY Ship_state;

Q10. Write a SQL query to calculate the total sales as (SHIPSTATE_sale) for each Ship_state with their number of orders:

SELECT Ship_state, SUM (Amount) as SHIPSTATE_net_sale,
COUNT (*) as total_state_orders
FROM [dbo].[monie works111csv]
GROUP BY Ship_state;

Q11. Write a SQL query to calculate the total sales as (SHIPCITY_sale) for each Ship_city with their number of orders:

SELECT Ship_city, SUM (Amount) as SHIPCITY_net_sale,
COUNT (*) as total_city_orders
FROM [dbo].[monie works111csv]
GROUP BY Ship_city;

Q12. Write a SQL query to find the age of customers who purchased items from the western dress category:

SELECT 
AVG(AGE) AS AVG_AGE
FROM [dbo].[monie works111csv]
WHERE CATEGORY = 'Western Dress'

Q13. Write a SQL query to find all transactions where the amount is greater than 1600:

SELECT * FROM [dbo].[monie works111csv]
WHERE amount > 1600

Q14. Write a SQL query to find the total number of transactions (Order_ID) made by each gender in each category:

SELECT category, gender, COUNT (*) as total_gendersales
FROM [dbo].[monie works111csv]
GROUP BY category,gender
ORDER BY 1

Q15. Write a SQL query to find the average amount of sales per month,to determine best selling and low sales month, extracting year from date column:
 
SELECT Year (date) as year,
month,
AVG(amount) as avg_sales 
FROM [dbo].[monie works111csv]
GROUP BY Year (date), month
ORDER BY year, month;

Q16. Write a SQL query to find the average amount of sales per Category,to determine best selling and low sales categories:

SELECT
category,
AVG(amount) as avg_sales 
FROM [dbo].[monie works111csv]
GROUP BY category
ORDER BY 1
 
Q17. Write a SQL query to find the average amount of sales per Age group:

SELECT
Age_group, AVG(Amount)
FROM [dbo].[monie works111csv]
GROUP BY Age_group
ORDER BY 1

Q18. Write a SQL query to find the total numbers of orders per Age group:

SELECT
Age_group, COUNT (order_id) as order_numbers
FROM [dbo].[monie works111csv]
GROUP BY Age_group
ORDER BY 1

Q19. Write a SQL query to find top 10 customers based on their amount of sales:

SELECT DISTINCT TOP 10
Cust_id, amount 
FROM [dbo].[monie works111csv]
GROUP BY cust_id, amount
ORDER BY 2 DESC

Q20. Write a SQL query to find number of unique customers who purchased items from each category:

SELECT  
category, count (DISTINCT Cust_id) as uniqueCust_numbrs
FROM [dbo].[monie works111csv]
GROUP BY category 
ORDER BY 2 DESC

Q21. Write a SQL query to COUNT total amount of sales greater and less than $500:

SELECT COUNT(*) AS amtover
FROM [dbo].[monie works111csv]
WHERE amount > 500;

SELECT COUNT(*) AS amtunder
FROM [dbo].[monie works111csv]
WHERE amount < 500;

OR

SELECT
COUNT(CASE WHEN amount > 500 THEN 1 END) AS amtover,
COUNT(CASE WHEN amount < 500 THEN 1 END) AS amtunder
FROM [dbo].[monie works111csv];


Findings
Customer Demographics: The dataset includes customers from various age groups, with sales distributed across different categories such as Kurta, Set, Top, Western Dress and Ethnic dress.
High-Value Transactions: Several transactions had a total sale amount greater than 500, indicating premium purchases.
Sales Trends: Monthly analysis shows variations in sales, helping identify peak seasons.
Customer Insights: The analysis identifies the top-spending customers and the most popular product categories.

Reports
Sales Summary: A detailed report summarizing total sales, customer demographics, and category performance.
Trend Analysis: Insights into sales trends across different months and shifts.
Customer Insights: Reports on top customers and unique customer counts per category.

Conclusion
This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, data cleaning, exploratory data analysis, and business-driven SQL queries. The findings from this project can help drive business decisions by understanding sales patterns, customer behavior, and product performance.
































































