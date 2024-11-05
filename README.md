# LITA_Class_Capstone

# Project Title: final project

## Project Overview
ce projet final doit etre la resultante d'un cursus de 4 mois de formation en data analyse au sein de la struccture Ladies In Tech Africa (LITA).
En tant que data analyste nous devons demontrer toutes les compétences acquises, allant de l'exploration de donnees jusqu'a linterpretation de resultats.

le projet est subdivisé et en 2 groupes :

Projet 1 : Analyse des performances de vente d'un magasin de détail

Projet 2 : Segmentation de la clientèle pour un service d'abonnement

-------------

## Projet 1: Analyse des performances de vente d'un magasin de détail

ce projet coonsiste a explorer les données de vente pour découvrir des informations clés telles que les produits les plus vendus, les performances
régionales et les tendances des ventes mensuelles. 

L'objectif est de produire un tableau de bord Power BI interactif qui met en évidence ces résultats.

-------

### Data Sources
la source des donnees utilisees est data SalesData.xlsx fourni par la structure LITA dans le canvas pour etudiant.

### Tools Used
1. Microsoft Excel [downlaod here](https://www.microsoft.com)
- For data cleaning
- For data analysis
- For data svisuazalisation
  
2. SQL Structured Query Language for querying of data
   
3. Power BI
- Pour créer des visualisations de données personnalisées et interactives avec une interface suffisamment simple pour que les utilisateurs finaux
- Pour creer des rapports et tableaux de bord

4. Github  for portfolio building

------

### Data cleaning
In the initial phase of data cleaning and preparations, we perform the following action;
1. Data loading and inspection
2. Handing missing variables
3. Data cleaning and formatting

-----

### Exploratory Data Analysis
EDA involved the exploring of the data to answer some question about the data such as :

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
This is where we include some basic lines of code or queries or even some of the DAX expressions used during your analysis

'''SQL
### 1. Récupérer le total des ventes pour chaque catégorie de produits
sql
SELECT ProductCategory, SUM(TotalPrice) AS TotalSales
FROM Sales
GROUP BY ProductCategory;


### 2. Trouver le nombre de transactions de vente dans chaque région
sql
SELECT Region, COUNT(*) AS NumberOfTransactions
FROM Sales
GROUP BY Region;


### 3. Trouver le produit le plus vendu en fonction de la valeur totale des ventes
sql
SELECT ProductID, SUM(TotalPrice) AS TotalSales
FROM Sales
GROUP BY ProductID
ORDER BY TotalSales DESC
LIMIT 1;


### 4. Calculer le revenu total par produit
sql
SELECT ProductID, SUM(TotalPrice) AS TotalRevenue
FROM Sales
GROUP BY ProductID;








Résumé : Dans ce projet, vous êtes chargé d’analyser les performances de vente d’un magasin de détail.
Projet 1 : Analyse des performances de vente d'un magasin de détail

Instructions:
Résumé : Ce projet consiste à analyser les données client d'un service d'abonnement afin d'identifier les segments et les
tendances. Votre objectif est de comprendre le comportement des clients, de suivre les types d'abonnement et d'identifier
les principales tendances en matière d'annulations et de renouvellements. Le résultat final est un tableau de bord
Power BI qui présente votre analyse.
