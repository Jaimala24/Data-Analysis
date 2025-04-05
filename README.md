# Sales Insights Data Analysis using Power BI

This project analyzes sales data for AtliQ Hardware, a computer hardware company struggling to navigate a dynamic market. The aim is to create an interactive Power BI dashboard that provides real-time insights into sales performance, helping stakeholders make data-driven decisions.

The project involves:

✅ Connecting MySQL database with Power BI

✅ ETL (Extract, Transform, Load) & Data Cleaning in Power BI

✅ Creating calculated measures using DAX (Data Analysis Expressions)

✅ Designing an interactive dashboard for sales insights

## Objective
The key goals of this project are:

🔹 Monitor sales performance across different regions, customers, and products

🔹 Identify trends and patterns to support business decisions

🔹 Analyze customer purchasing behavior to improve marketing strategies

🔹 Create dynamic reports for stakeholders with interactive visualizations

## Relationship Model

![Screenshot 2025-04-03 235542](https://github.com/user-attachments/assets/9e29a825-694a-42e5-81c2-0b6522e2644f)

## Step-by-Step Dashboard Creation using Power BI
#### 1. Connecting MySQL to Power BI
Used the MySQL connector in Power BI

Imported sales, customer, product, and market data

Established relationships in Power BI’s Model View

#### 2. Data Cleaning & Transformation (ETL Process)
Used Power Query Editor for:

✅ Removing duplicates

✅ Handling missing values

✅ Formatting data types (dates, currencies)

✅ Creating calculated columns (e.g., profit margin)

#### 3. Key Calculations in DAX

SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

#### Data Analysis Using SQL

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`

## Dashboard Report Overview
The Power BI dashboard includes:

✅ Revenue by Markets

✅ Sales Quantity by Markets

✅ Revenue Trend

✅ Top 5 Customers

✅ Top 5 Products

![Screenshot 2025-04-04 004145](https://github.com/user-attachments/assets/4f104060-f97e-421d-905c-1854992855ae)

## Summary
The Sales Insights Data Analysis project provides a comprehensive real-time sales performance dashboard for AtliQ Hardware, enabling data-driven decision-making. By integrating MySQL with Power BI, we extracted, cleaned, and transformed raw sales data using Power Query, ensuring accuracy and consistency. Key DAX calculations were implemented to analyze total sales, revenue, profit margins, and year-over-year growth. The final interactive dashboard offers deep insights into sales trends, customer behavior, product performance, and market distribution, allowing stakeholders to identify opportunities and optimize business strategies. This project demonstrates the power of data visualization and analytics in enhancing business decision-making and driving growth. 🚀
