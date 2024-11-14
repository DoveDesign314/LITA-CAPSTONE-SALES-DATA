#  Retail Store Sales Analysis
---

### Project Outline
---
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
---

**EXCEL**
---
- **SALES TREND BY MONTH**
![SalesTrendbyMonth](https://github.com/user-attachments/assets/41449945-c7fb-433f-9562-13938b6a06de)

There is a noticeable decline 

- **AVERAGE ORDER QUANTITY BY REGION**
![AverageOrderquantitybyRegion](https://github.com/user-attachments/assets/75adc542-c0ed-4dc0-8f49-97ae6bcff435)

- **SALES BY PRODUCT BY REGION**
![SalesbyProductbyRegion](https://github.com/user-attachments/assets/7292c52b-a120-4bb9-a779-c3fb59547cfd)

- **MONTHLY SALES BY REGION**
![MonthlysalesbyRegion](https://github.com/user-attachments/assets/3745c19a-ec63-4f82-a129-7b86bd8b6c62)


**EXCEL DASHBOARD FOR SALES DATA**

![SalesDashboard](https://github.com/user-attachments/assets/adbc85de-7aca-47fa-bd55-b6ea06cdafbe)

**SQL**
---
- **HIGHEST SELLING PRODUCT PER SALES**
  
![HighestSellinProductperSales](https://github.com/user-attachments/assets/813bc98a-5239-4f0a-808e-a09db1550dbb)

- **MONTHLY SALES FOR THE CURRENT YEAR**
![MonthlySalesforthecurrentyear](https://github.com/user-attachments/assets/6e0aaff1-5340-45f8-9f84-e0f9758cc0f9)

- **NUMBER OF SALES PER REGION**
![NoofSalesperRegion](https://github.com/user-attachments/assets/75ed6f8f-aee3-4016-a6cb-96e18451a984)

- **TOP 5 CUSTOMERID BY PURCHASE AMOUNT**
 ![Top5CustomerIDbyPurchaseAmount](https://github.com/user-attachments/assets/e34cf389-f943-4821-9820-1017ffd843c7)

- **TOTAL REVENUE PER PRODUCT**
![Totalrevenueperproduct](https://github.com/user-attachments/assets/b16dd869-10bc-41c3-9db1-b394a6bdccbf)

- **TOTAL SALES OF EACH PRODUCT**
![Totalsalesforeachproduct](https://github.com/user-attachments/assets/d4a18ed3-d6aa-45a9-a71d-976ea2941aae)


**POWER BI**
---
**SALES OVERVIEW (TOP - PERFORMING PRODUCTS)**
---
**TOTAL SALES BY MONTH**
![TOTALSALESBYMONTH](https://github.com/user-attachments/assets/9d55abb2-9d9a-4681-92bb-39f4d89df041)

**TOTAL SALES BY MONTH (WITH SLICER 2023)**
![TOTALSALESBYMONTH 2023](https://github.com/user-attachments/assets/b4f9a7e1-6ea0-4a4b-9b58-038204d153ca)

**TOTAL SALES BY MONTH (WITH SLICER 2024)**
![TOTALSALESBYMONTH 2024](https://github.com/user-attachments/assets/75dccc34-1cd9-4827-a57d-f7064c2b7774)


TOP-PERFORMING PRODUCTS
---
**PRODUCT RANK BY PRODUCT**
![PRODUCTRANK BY PRODUCT](https://github.com/user-attachments/assets/ffff4692-3a07-4a19-8d91-6c390854bbe1)

**TOTAL QUANTITY SOLD BY PRODUCT**
![TOTALQTYSOLD BY PRODUCT ](https://github.com/user-attachments/assets/927254ac-5344-4697-a2cb-232617ce11a0)

**TOTAL SALES BY PRODUCT**
![TOTALSALES BY PDT COL](https://github.com/user-attachments/assets/42c8269b-59ff-4aa1-8549-2fbe944e040c)


REGIONAL BREAKDOWNS
---
**SALES BY REGION**
![SALES BY REGION](https://github.com/user-attachments/assets/31d4cd23-acfd-4d9c-92f5-b8faa60011de)


SALES DATA DASHBOARD
---
![SALES DATA DASHBOARD POWERBI](https://github.com/user-attachments/assets/03d89d45-2513-4843-86a9-f0278f77d440)

Here’s a summary based on the information visible in the Power BI dashboard:
---

1. **Regional Performance**
The sales data is distributed across four regions: East, North, South, and West.
The South region accounts for the highest sales, making up 44.1% of total sales, followed by the North and East regions, which contribute around 23% each. The West region records the lowest sales percentage.
This indicates a concentration of sales in the South, suggesting it is the most active or populous market.

2. **Revenue Trends and Distribution**
- Monthly Sales Trends: Sales peaked in March with approximately 2.8M in revenue, which is the highest among all months. Following that, there is a gradual decline with some fluctuations, indicating possible seasonality or promotional impacts.
- Product Sales Distribution: Shoes and Jackets are the top-selling products, showing strong demand in these categories. Other products like Hats, Gloves, and Socks also contribute significantly but lag behind the top two.
- Quantity Sold by Product: The pie chart shows that Hats and Shoes lead in terms of the total quantity sold, with each making up 23.1% and 18.1%, respectively, of the overall quantity sold.

3. **Strategic Implementation**
To maximize growth, the company could focus on promoting high-demand products (Shoes and Jackets) in less-performing regions like the West. Tailored promotions, discounts, or outreach programs could help boost sales in these areas.
Seasonal promotions might be effective, as seen from the revenue spike in March. Additional targeted campaigns during high-sales months could further optimize revenue.
Expanding product variety or enhancing availability in lower-demand products could also increase overall sales.

4. **Conclusion**
The South region is the key market, and Shoes and Jackets are top-performing products. However, there is an opportunity for growth in the West region and for lower-selling products.
Implementing targeted regional strategies, enhancing product availability, and leveraging high-sales months could help maintain and boost overall revenue.









