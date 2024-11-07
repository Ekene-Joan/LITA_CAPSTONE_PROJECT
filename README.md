# LITA_CAPSTONE_PROJECT
## Project Title: Sales Performance Analysis


### Project Overview
--- 
This project aims to comprehensively review a retail store's sales data to identify key insights, including top-selling products, regional performance, and monthly sales trends. This analysis will incorporate data exploration in Excel, data extraction and transformation using SQL, and visualization through an interactive Power BI dashboard. Combining these tools will uncover essential metrics such as total revenue by product and region, highest-selling products, top-performing customers, and sales contribution by region. The final Power BI dashboard will present these findings in a clear and interactive format, offering valuable insights to guide strategic business decisions for enhanced sales performance.

### Data Sources
--- 
The data retrieved was a CSV data set that comprises of two main data:
- The sales data: which includes information on order ID, customer ID, product, region, order date, quantity, and unit price
- The Customer data: which has in it the Customer ID, customer name, subscription type, subscription start date, and end date, canceled, and revenue.

### Project Objective
---
To gain a comprehensive understanding of sales performance and customer trends, we can extract key insights by analyzing the data based on the following questions:

- Retrieve the total sales for each product category.
- Find the number of sales transactions in each region.
- Identify the highest-selling product by total sales value.
- Calculate total revenue per product.
- Calculate monthly sales totals for the current year.
- Find the top 5 customers by total purchase amount.
- Calculate the percentage of total sales contributed by each region.
- Identify products with no sales in the last quarter.

### Tools Used
--- 
- Microsoft Excel:
    1) For Data cleaning
    2) Exploratory analysis

- MYSQL: For Querying data
  
- Power BI: For Visualization and Dashboard presentation.

### Data Cleaning and Preparation
--- 
In this phase of data cleaning, the following are performed:
- Data loading and Inspection.
  
- Data Wrangling and formatting.

### Exploratory Data Analysis and Formula used
--- 
This is the analysis where the data is explored to answer some questions which include:

- Total sales by product, region, and month.
  
      1) ```=SUMIF(Sales4[Product],"Gloves",Sales4[SalesAmount])```
  
      2) ```=SUMIF(Sales4[Region],"East",Sales4[SalesAmount])```
  
      3) ```=SUMIF(Sales4[Orderdate],"2023-Jan",Sales4[SalesAmount])```
  
- Average sales per product
  
      1) ```AVERAGEIF(Sales4[Product],"Gloves",Sales4[SalesAmount])```
  
- Total revenue by region.
  
      1) ```=SUMIF(Sales4[Region],"East",Sales4[SalesAmount])```
  
- Percentage sales amount by region
  
      1) ```=K13/SUM($K$13:$K$16)```

### Visual Analysis and Inference
--- 
This visual presentation showcases the analysis conducted using Excel functions, pivot tables, and SQL queries. By performing parallel analyses with both tools, we validate data accuracy and ensure the reliability of the results.

1) Excel Pivot


2) SQL Query
   
- Total Sales by each product category.
  
```SQL
select * from sales;

SELECT Product, SUM(SalesAmount) AS TotalSales FROM Sales
GROUP BY Product;
```

-  Number of sales transactions in each region.

```SQL
select* from sales;

SELECT Region, count(OrderID) AS no_of_sales_transaction
FROM Sales
GROUP BY Region;
```

- Highest-selling product by total sales value.
  
```SQL
select * from sales;

SELECT product, SUM(SalesAmount) AS TotalSales
FROM sales
GROUP BY product
ORDER BY TotalSales DESC
LIMIT 1;
```
- Total revenue per product.

```SQL
SELECT * FROM SALES;

SELECT PRODUCT, SUM(SALESAMOUNT) AS TOTAL_REVENUE
FROM SALES
GROUP BY PRODUCT;
```
-  Monthly sales totals for the current year(2024)
```SQL
