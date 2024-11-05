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

3. Fnd the number of sales transactions in each region
   
SELECT Region, COUNT(*) AS NumberOfTransactions
FROM Sales
GROUP BY Region;

4. Fnd the highest-selling product by total sales value
   
SELECT ProductID, SUM(TotalPrice) AS TotalSales
FROM Sales
GROUP BY ProductID
ORDER BY TotalSales DESC
LIMIT 1;

5. Calculate total revenue per product
   
SELECT ProductID, SUM(TotalPrice) AS TotalRevenue
FROM Sales
GROUP BY ProductID;

6. Calculate monthly sales totals for the current year
   
SELECT STRFTIME('%m', TransactionDate) AS Month, SUM(TotalPrice) AS MonthlySales
FROM Sales
WHERE STRFTIME('%Y', TransactionDate) = STRFTIME('%Y', 'now')
GROUP BY Month;

7. Fnd the top 5 customers by total purchase amount
   
SELECT CustomerID, SUM(TotalPrice) AS TotalSpent
FROM Sales
GROUP BY CustomerID
ORDER BY TotalSpent DESC
LIMIT 5;

8. Calculate the percentage of total sales contributed by each region
   
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

9. Identify products with no sales in the last quarter

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







Résumé : Dans ce projet, vous êtes chargé d’analyser les performances de vente d’un magasin de détail.
Projet 1 : Analyse des performances de vente d'un magasin de détail

Instructions:
Résumé : Ce projet consiste à analyser les données client d'un service d'abonnement afin d'identifier les segments et les
tendances. Votre objectif est de comprendre le comportement des clients, de suivre les types d'abonnement et d'identifier
les principales tendances en matière d'annulations et de renouvellements. Le résultat final est un tableau de bord
Power BI qui présente votre analyse.
