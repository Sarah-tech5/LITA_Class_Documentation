# LITA_Class_Capstone

# Project Title: final project

## Project Overview
This final project must be the result of a 4-month training course in data analysis within the Ladies In Tech Africa (LITA) structure. 
As a data analyst, we must demonstrate all the skills acquired, ranging from data exploration to the interpretation of results.

The project is divided into 2 groups:

Project 1: Analysis of sales performance of a retail store

Project 2: Customer segmentation for a subscription service

-------------

## Project 1: Analysis of sales performance of a retail store

This project involves exploring sales data to uncover key insights such as top-selling products, regional performance, and monthly sales trends. 
The goal is to produce an interactive Power BI dashboard that highlights these findings.

-------

### Data Sources

The source of the data used is data SalesData.xlsx provided by the LITA structure in the student canvas.

----

### Tools Used

1. Microsoft Excel [downlaod here](https://www.microsoft.com)
- For data cleaning
- For data analysis
- For data svisuazalisation
  
2. SQL Structured Query Language for querying of data
   
3. Power BI
- To create custom, interactive data visualizations with an interface simple enough for end users
- To create reports and dashboards

4. Github for portfolio building

------

### Data cleaning

We take the following steps in the first stage of data preparation and cleaning :

1. Data loading and inspection
2. Handing missing variables
3. Data cleaning and formatting

-----

### Exploratory Data Analysis

EDA entailed examining the data to get answers to certain questions concerning it, including :

1. Excel
- Use pivot tables to summarize total sales by product, region, and month
- Use Excel formulas to calculate metrics such as average sales per product and total revenue by region

2. SQL
- Retrieve the total sales for each product category
- Fnd the number of sales transactions in each region
- Fnd the highest-selling product by total sales value
- Calculate total revenue per product
- Calculate monthly sales totals for the current year
- Fnd the top 5 customers by total purchase amount
- Calculate the percentage of total sales contributed by each region
- Identify products with no sales in the last quarter

3. Power BI
- Create a dashboard that visualizes the insights found in Excel and SQL
The dashboard should include a sales overview, top-performing products, and regional breakdowns

-----

### Data Analysis

Here we give simple lines of code, queries or even some DAX expressions that we used in our analysis.

```SQL
1. Retrieve the total sales for each product category
   
SELECT ProductCategory, SUM(TotalPrice) AS TotalSales
FROM Sales
GROUP BY ProductCategory;

2. Fnd the number of sales transactions in each region
   
SELECT Region, COUNT(*) AS NumberOfTransactions
FROM Sales
GROUP BY Region;

3. Fnd the highest-selling product by total sales value
   
SELECT ProductID, SUM(TotalPrice) AS TotalSales
FROM Sales
GROUP BY ProductID
ORDER BY TotalSales DESC
LIMIT 1;

4. Calculate total revenue per product
   
SELECT ProductID, SUM(TotalPrice) AS TotalRevenue
FROM Sales
GROUP BY ProductID;

5. Calculate monthly sales totals for the current year
   
SELECT STRFTIME('%m', TransactionDate) AS Month, SUM(TotalPrice) AS MonthlySales
FROM Sales
WHERE STRFTIME('%Y', TransactionDate) = STRFTIME('%Y', 'now')
GROUP BY Month;

6. Fnd the top 5 customers by total purchase amount
   
SELECT CustomerID, SUM(TotalPrice) AS TotalSpent
FROM Sales
GROUP BY CustomerID
ORDER BY TotalSpent DESC
LIMIT 5;

7. Calculate the percentage of total sales contributed by each region
   
WITH RegionalSales AS (
    SELECT Region, SUM(TotalPrice) AS RegionalTotal
    FROM Sales
    GROUP BY Region
), TotalSales AS (
    SELECT SUM(TotalPrice) AS GrandTotal
    FROM Sales
)
SELECT RegionalSales.Region,
       (RegionalSales.RegionalTotal * 100.0 / TotalSales.GrandTotal) AS SalesPercentage
FROM RegionalSales, TotalSales;

8. Identify products with no sales in the last quarter

SELECT ProductID
FROM Products
WHERE ProductID NOT IN (
    SELECT DISTINCT ProductID
    FROM Sales
    WHERE TransactionDate >= DATE('now', '-3 months')
);
```

-----

### Data visualization 

1. Excel

   
![pivot table customers](https://github.com/user-attachments/assets/08aa143d-4ad2-45d6-98e5-aa0bdb74e02b)



2. Power BI
![Sales analysis 1](https://github.com/user-attachments/assets/66220540-e308-4d73-98dc-1a9d7fd9794f)


![Sales analysis 2](https://github.com/user-attachments/assets/85789f79-34e5-4b7e-872e-d81923eefe05)

---------



## Project 2: Customer segmentation for a subscription service

This project involves analyzing customer data for a subscription service to identify segments and trends. Your goal is to understand customer behavior, track subscription types,
and identify key trends in cancellations and renewals. The fnal deliverable is a Power BI dashboard that presents your analysis.

-------

### Data Sources

The source of the data used is data SalesData.xlsx provided by the LITA structure in the student canvas.

----

### Tools Used

1. Microsoft Excel [downlaod here](https://www.microsoft.com)
- For data cleaning
- For data analysis
- For data svisuazalisation
  
2. SQL Structured Query Language for querying of data
   
3. Power BI
- To create custom, interactive data visualizations with an interface simple enough for end users
- To create reports and dashboards

4. Github for portfolio building

------

### Data cleaning

We take the following steps in the first stage of data preparation and cleaning :

1. Data loading and inspection
2. Handing missing variables
3. Data cleaning and formatting

-----

### Exploratory Data Analysis

EDA entailed examining the data to get answers to certain questions concerning it, including :

1. Excel
- Analyze customer data using pivot tables to fnd subscription patterns
- Calculate the average subscription duration and identify the most popular subscription types
- Create any other interesting reports.

2. SQL
- Retrieve the total number of customers from each region
- Fnd the most popular subscription type by the number of customers
- Fnd customers who canceled their subscription within 6 months
- Calculate the average subscription duration for all customers
- Fnd customers with subscriptions longer than 12 months
- Calculate total revenue by subscription type
- Fnd the top 3 regions by subscription cancellations
- Fnd the total number of active and canceled subscriptions

4. Power BI
- Build a Power BI dashboard that visualizes key customer segments,
cancellations, and subscription trends. Include slicers for interactive analysis
-----

### Data Analysis

Here we give simple lines of code, queries or even some DAX expressions that we used in our analysis.

```SQL

1. Retrieve the total number of customers from each region

SELECT Region, COUNT(CustomerID) AS TotalClients
FROM Customers
GROUP BY Region;

2. Fnd the most popular subscription type by the number of customers

SELECT SubscriptionType, COUNT(CustomerID) AS ClientCount
FROM Customers
GROUP BY SubscriptionType
ORDER BY ClientCount DESC
LIMIT 1;

3. Fnd customers who canceled their subscription within 6 months

SELECT CustomerID, CustomerName, SubscriptionType, SubscriptionStart, SubscriptionEnd
FROM Customers
WHERE Canceled = 1
  AND (julianday(SubscriptionEnd) - julianday(SubscriptionStart)) <= 180;

4. Calculate the average subscription duration for all customers

SELECT AVG(subscription_duration_per_month) AS AverageSubscriptionDuration
FROM Customers;

5. Fnd customers with subscriptions longer than 12 months

SELECT CustomerID, CustomerName, SubscriptionType, subscription_duration_per_month
FROM Customers
WHERE subscription_duration_per_month > 12;

6. Calculate total revenue by subscription type

SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM Customers
GROUP BY SubscriptionType;

7. Fnd the top 3 regions by subscription cancellations

SELECT Region, COUNT(CustomerID) AS CancellationCount
FROM Customers
WHERE Canceled = 1
GROUP BY Region
ORDER BY CancellationCount DESC
LIMIT 3;

8. Fnd the total number of active and canceled subscriptions

SELECT 
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM Customers;

```


-----

### Data visualization 

1. Excel

![pivot table customers](https://github.com/user-attachments/assets/d091bbc4-c61e-4742-b21e-f4f8b7d2277a)






2. Power BI
![Customers analysis 1](https://github.com/user-attachments/assets/b5de35b7-3a0c-4ab4-80af-3f881bfda42c)



![Customers analysis 2](https://github.com/user-attachments/assets/a3ba0099-8a42-4337-95be-e9087b04aea6)


--------
🏆 💻
