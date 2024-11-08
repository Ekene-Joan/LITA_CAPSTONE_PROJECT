# LITA_CAPSTONE_PROJECT
## Project Title: Sales Performance Analysis


### Project Overview
--- 
This project aims to comprehensively review a retail store's sales data to identify key insights, including top-selling products, regional performance, and monthly sales trends. This analysis will incorporate data exploration in Excel, data extraction and transformation using SQL, and visualization through an interactive Power BI dashboard. Combining these tools will uncover essential metrics such as total revenue by product and region, highest-selling products, top-performing customers, and sales contribution by region. The final Power BI dashboard will present these findings in a clear and interactive format, offering valuable insights to guide strategic business decisions for enhanced sales performance.

### Data Sources
--- 
The data retrieved was a CSV sales data set that comprises information on the following column:

- Order ID: A unique identifier for each order, often a numeric or alphanumeric code, used to track and reference individual transactions.

- Customer ID: A unique identifier assigned to each customer to track their orders, history, and preferences in the system.

- Product: The item or service being purchased by the customer, usually identified by its name or SKU (Stock Keeping Unit) in the catalog.

- Region: The geographical area where the order is being placed or delivered, helping with logistics, reporting, and market analysis.

- Order Date: The date when the customer placed the order, important for tracking timelines, processing, and analysis of order patterns.

- Quantity: The number of units of the product being ordered, helping calculate the total cost and manage inventory.

- Unit Price: The cost per single unit of the product, used in calculating the total price of the order based on quantity.

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

## Visual Analysis and Inference
--- 
This visual presentation showcases the analysis conducted using Excel functions, pivot tables, and SQL queries. By performing parallel analyses with both tools, we validate data accuracy and ensure the reliability of the results.

1) Excel Pivot


![pivot 3](https://github.com/user-attachments/assets/646bd894-f652-47b8-8fce-d22794b61dd6)


- The sales data by product category shows that Shoes, Shirts, and Hats are the top performers, together accounting for 67.4% of total sales, with Shoes leading at 29.2%. In contrast, Socks and Jackets have the lowest sales, contributing just 8.6% and 9.9%, respectively. This suggests that while a few products drive most of the revenue, there is potential to increase sales for the lower-performing items through targeted marketing or promotions.


- The total sales by region reveal that the South region generates the highest sales, contributing 927,820, which accounts for approximately 44.2% of the grand total. The East region follows with 485,925, making up about 23.1% of total sales. North and West regions contribute 387,000 and 300,345 respectively, with sales shares of 18.4% and 14.3%. Together, the South and East regions account for 67.3% of the total sales, indicating they are the strongest markets. The overall grand total sales stand at 2,101,090, with the South region being the dominant contributor.


- The average sales by region reveal notable regional performance differences. The South region leads with an average sales amount of 374, significantly higher than the other regions, indicating stronger sales performance. In contrast, the West region shows the lowest average sales at 121, suggesting weaker sales in that area. The East and North regions show average sales of 196 and 156, respectively, which are above the West but still lag behind the South. The overall Grand Total average of 212 suggests that while some regions perform better, there may be a need to focus on boosting sales in the West and North regions to reach a more balanced overall performance.


- The number of sales transactions is fairly consistent across all regions, with the East having the highest count at 2,483 orders, closely followed by the North at 2,481, the South at 2,480, and the West at 2,477. Together, these regions contribute to a total of 9,921 sales transactions. This distribution indicates balanced sales activity across all regions, with no significant variation in the number of transactions per region.


- The total sales across the months show significant fluctuations. February stands out with the highest sales of 546,300, while months like March, April, September, and December show lower sales, with September being the weakest at 34,720. The sales are relatively consistent from January to June, but there’s a noticeable drop starting in September and continuing through December. Despite this, the grand total of 2,101,090 indicates a strong overall performance, with a few peak months driving the majority of the revenue. The data suggests that sales tend to dip in the latter half of the year, particularly after the mid-point.


- In 2023, the average sales amount was 186, generating a total revenue of 1,105,330, which accounted for 52.61% of the grand total. In contrast, 2024 saw an increase in the average sales amount to 251, but total revenue dropped to 995,760, contributing 47.39% of the overall revenue. This suggests that while the sales amount per transaction increased in 2024, the overall revenue declined, potentially due to fewer transactions or changes in customer behavior. Together, both years contributed to the grand total of 2,101,090 in sales.


- In comparing the months of 2023 and 2024, there is a noticeable increase in average sales, with 2024 showing higher overall performance. The 2024 total revenue of 995,760 represents 47.39% of the grand total, while 2023 was 1,105,330, accounting for 52.61%. However, 2024 experienced strong months, such as February with 298,800, significantly outpacing 2023's 247,500. January also saw a major boost, increasing from 49,600 in 2023 to 198,400 in 2024, reflecting a substantial improvement. On the downside, July 2024 shows a significant drop to 37,200, compared to 237,600 in 2023, highlighting a marked difference in performance in this particular month. Overall, 2024 saw a consistent rise in monthly sales, except for a dip in July, which suggests strong growth in the early months of the year and more fluctuation in the latter half.



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
SELECT * FROM sales;

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
SELECT orderdate, sum(salesamount) as totalsales
FROM sales
WHERE (orderdate) = 2024
GROUP BY orderdate;
```
- The top 5 customers by total purchase amount
  
``` SQL
SELECT 
    Customerid As Customer,
    SUM(salesamount) AS Total_purchase_amount
FROM 
   sales
GROUP BY 
    customerid
ORDER BY 
    total_purchase_amount DESC
LIMIT 5;
```
- % Percentage of Total sales by each region
```SQL

SELECT 
    region,
    SUM(salesamount) AS Total_Sales,
    ROUND(SUM(salesamount) * 100.0 / (SELECT SUM(salesamount) FROM sales), 2) AS Percentage_of_Total_Sales
FROM 
    sales
GROUP BY 
    region
ORDER BY 
    Percentage_of_Total_Sales  DESC;
```




- Identify products with no sales in the last quarter
  
``` SQL
SELECT s.orderdate, s.product,
       SUM(CASE WHEN s.orderdate BETWEEN '2024-05-01' AND '2024-08-31' THEN s.salesamount ELSE 0 END) AS total_sales
FROM sales s
WHERE s.orderdate in ('2024-may','2024-jun', '2024-jul', '2024-Aug')
GROUP BY s.product, s.orderdate
HAVING SUM(CASE WHEN s.orderdate BETWEEN '2024-05-01' AND '2024-08-31' THEN s.salesamount ELSE 0 END) = 0;
```

## 
