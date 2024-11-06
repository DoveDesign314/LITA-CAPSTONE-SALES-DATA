#  Retail Store Sales Analysis

[Project Overview](#project-overview)

[Project Workflow](#project-workflow)

[Data Source](#data-source)

[Datasets and column definitions](datasets-and-column-definitions)

[Key Insights from the Data](#key-insights-from-the-data)

[Tools Used](#tools-used)

[Data Cleaning and Preparation (Excel)](#data-cleaning-and-preparation)

[Key steps](#key-steps)

[Formula Used](#formula-used)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis (SQL)](#data-analysis-(sql))

[Data Visualization (Power BI)](#data-visualization-(power-bi))

[Key Findings](#key-findings)

[Pictorial Visuals of Analysis](#pictorial-visuals-of-analysis)

### Project Overview
---
This project focuses on analyzing the sales performance of a retail store. The goal is to uncover key insights such as top-selling products, regional performance, and monthly sales trends using Excel, SQL, and Power BI. The analysis focuses on understanding revenue trends and sales performance across regions and calculating key metrics such as average revenue by region. The findings are presented through an interactive Power BI dashboard that visualizes the data and helps inform decision-making.

### Project Workflow
---
The project was completed in three phases: data cleaning and exploration in Excel, query-based analysis using SQL, and final visualization in Power BI.

### Data Source
---
The primary source of data used here was Data Sale.xlsx

### Datasets and column definitions
---
The sales data used in this project consists of multiple columns that capture key information about sales transactions. Below is an explanation of each column in the dataset:
- Order_ID: Used to distinguish individual transactions in the dataset.
- Product_Name: Name of the product sold such as shirt, shoes, hat, jacket, gloves etc.
-  Quantity_Sold: Number of units of the product sold in a single transaction.
-  Order_Date: he date when the transaction occurred
-  Customer_ID: Unique identifier for each customer
-  Region: Geographic region where the sale took place.

### Key Insights from the Data
---
- Top-Selling Products: Identified by using the Product_Name, Quantity_Sold, and Sales_Amount columns.
- Regional Performance: Analyzed through the Region column in relation to total sales.
- Monthly Sales Trends: Derived from the Order_Date column by aggregating sales across different months.
- Average Revenue by Region: Calculated by the average revenue per sales in each region to assess performance

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

### Formula Used
---
- Average sales per Product
```EXCEL
=AVERAGEIF(C2:C50001,C2,H2:H50001)
```
- Total revenue by Region
```EXCEL
SUMIF(D3:D50002,D3,H3:H50002)
```
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

### 3. Data Visualization (Power BI)
---
DAX Measures for key insights were created:
- Total Sales:
```DAX
TotalSales = SUMX(Sales, Sales[Quantity] * Sales[UnitPrice])
```
- Sales by Region
```DAX
  SalesByRegion = SUM(Sales[TotalSales])
```
The final stage was to visualize the insights using Power BI. The interactive dashboard includes:

- Top-Performing Products: A bar chart showing the products that brought in the highest revenue.
```
Axis: Product Name.
Values: Total Sales (using TopProductSales).
 ```
- Regional Sales Performance: A map chart displaying total sales by region.
```
	Location: Region
	Values: Total Sales
```
- Monthly Sales Trends: A line chart visualizing sales trends over time.
```
X-axis: Order Date 
Y-axis: Total Sales.
```

### Key Findings
---
- Top-Selling Products: The top 3 products accounted for 40% of total sales, with Product A leading the list.
- Regional Performance: Region X generated the highest sales, contributing to 35% of the overall revenue.
- Sales Trends: The highest sales occurred in December, with a steady increase observed in the last quarter of the year.

### Pictorial Visuals of Analysis
EXCEL
- SALES TREND BY MONTH
![SalesTrendbyMonth](https://github.com/user-attachments/assets/41449945-c7fb-433f-9562-13938b6a06de)


