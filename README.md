#  Retail Store Sales Analysis

### Project Overview
---
his project focuses on analyzing the sales performance of a retail store. The goal is to uncover key insights such as top-selling products, regional performance, and monthly sales trends using Excel, SQL, and Power BI. The findings are presented through an interactive Power BI dashboard that visualizes the data and helps inform decision-making.

### Project Workflow
---
The project was completed in three phases: data cleaning and exploration in Excel, query-based analysis using SQL, and final visualization in Power BI.

### Data Sources
---
The primary source of data used here was Data Sale.xlsx

### Tools Used
---
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. For initial data cleaning,
  2. For analysis,
  3. For exploration and
  4. For Data visualization.
     
- SQL [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
  1.  For data extraction
  2.  For advanced querying from the sales database.
     
- Power BI [Downloaad Here](https://learn.microsoft.com/en-us/power-bi/fundamentals/desktop-get-the-desktop)
  1. For data visualization
  2. For dashboard creation.
     
- Github for portfolio Building [Download Here](https://docs.github.com/en/desktop/installing-and-authenticating-to-github-desktop/installing-github-desktop)

### 1. Data Cleaning and Preparation (Excel)
---
The sales data was first explored and cleaned in Excel. The following actions were done:
1. Data loading and Inspection.
2. Handling missing variables, removing duplicates and formatting columns.
3. Data validation to ensure consistency (e.g., correct product IDs, regional codes).
4. Basic exploratory analysis, such as calculating total sales, average revenue, average unit price etc using pivot tables.

### Key Steps:
---
- Filtered sales data for the analysis period.
- Created summary/pivot tables for product categories, regions, and sales channels.
- Calculated key metrics such as average sales per product and total revenue by region.

### Exploratory Data Analysis
---
EDA involved exploring the data to answer some questions about the Data such as;
- what is the overall sales trend?
- which product are top selling?
- what are the products on peak sales?

### 2. Data Analysis (SQL)
---
After the initial data preparation, SQL was used to run more advanced queries on the dataset , allowing deeper insights.

Key SQL Queries:

- To retrieve the total number of customers from each region
```SQL
SELECT Region, COUNT(CustomerID) AS TotalCustomers
FROM CustomerData
GROUP BY Region;
```
- To find the number of sales transactions in each region.
```SQL
Select Region,COUNT(OrderID) as NumOfTransactions
from Sales Data
Group by Region
```
- To find the highest-selling product by total sales value
```SQL
select top(1) PRODUCT,
SUM([Total_sales])as TotalSales
from [dbo].[Sales Data]
group by PRODUCT
order by TotalSales DESC
```
- To calculate the total revenue per product
```SQL
Select PRODUCT, SUM([Total_sales]) as TotalRevenue
from [dbo].[Sales Data]
group by PRODUCT
```
- To find the top 5 customers by total purchase amount
```SQL
select top(5) [Customer_Id],
 SUM ([Total_sales]) as TotalPurchaseAmount from [dbo].[Sales Data]
group by [Customer_Id]
order by TotalPurchaseAMount DESC
```
