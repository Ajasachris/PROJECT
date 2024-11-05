# SALES PERFORMANCE ANALYSIS 

### PROJECT OVERVIEW


Retail stores operate in a competitive and dynamic environment, where sales performance is a key indicator of success. Analyzing sales performance enables a store to assess its profitability, understand customer purchasing patterns, and identify factors driving or hindering revenue growth. In this analysis, we aim to examine critical metrics, trends, and factors influencing sales performance in the retail context, considering various products, seasonal patterns, customer demographics, and marketing strategies.

 ### PROJECT OBJECTIVE
---
This project was designed to address the following analysis goals.

- To perform initial exploration of Sales Data and use pivot tables to summarize total sales by product, region and month.

- To calculate average sales per product and total revenue by region.

### FORMULAR USED
---
```
Average Sales = Total Sales / Units Sold
```

### TOOLS AND METHOD USED
---
- Data Analysis: the data was analyzed using Microsoft excel using pivot tables to organize, summarize and filter data for easier interpertation.
- Data Visualization: Bar chart were created in excel to visually represent key insights.

### VISUAL ANALYSIS
### Total Sales Per Product, Region

![Screenshot 2024-11-03 205804](https://github.com/user-attachments/assets/abbd5cfd-68e1-4637-b7e9-12ac996e7955)

### Bar Chart
![Screenshot 2024-11-03 205852](https://github.com/user-attachments/assets/c6d4e275-05fd-4d64-b043-cf6501fe88bd)

### Average Sales Per Product

![Screenshot 2024-11-04 083629](https://github.com/user-attachments/assets/8e4adce3-4752-4dd7-9f52-454785de6092)

### Total Revenue By Region

![Screenshot 2024-11-04 084317](https://github.com/user-attachments/assets/d512d431-3684-4619-b32d-b9e312dde604)



# STRUCTURED QUERY LANGAUGE

### Project Objectives
The objectives were to: 
- retrieve the total sales for each product category. 
- find the number of sales transactions in each region. 
-	find the highest-selling product by total sales value. 
-	calculate total revenue per product. 
- calculate monthly sales totals for the current year. 
-	find the top 5 customers by total purchase amount. 
-	calculate the percentage of total sales contributed by each region. 
-	identify products with no sales in the last quarter. 

### Skills:
The set of skills were used for the optimization of the analysis, which were:
- Create of database (new schema)
- Create a table based on the field name.

### To retrieve the total sales for each product category.
```
SELECT Product, SUM(Sales) AS TotalSales
FROM [dbo].[SalesData]
GROUP BY Product;
```

### To find the number of sales transactions in each region.
```
SELECT Region, COUNT(Sales) AS number_of_sales
FROM [dbo].[SalesData]
GROUP BY Region
ORDER BY number_of_sales
```
### To find the highest-selling product by total sales value.
```
SELECT Product, SUM(Sales) AS Total_sales_value
FROM [dbo].[SalesData]
GROUP BY Product 
ORDER BY Total_sales_value DESC;
```
### To calculate total revenue per product.
```
SELECT Product, SUM(CAST(Quantity AS INT) * CAST(UnitPrice AS DECIMAL(18,2))) AS Revenue
FROM [dbo].[SalesData]
GROUP BY Product
ORDER BY Revenue DESC;
```
### To calculate monthly sales totals for the current year.
```
SELECT 
    MONTH(OrderDate) AS Month, 
    SUM(Sales) AS Monthly_Sales
FROM [dbo].[SalesData]
WHERE YEAR(OrderDate) = YEAR(GETDATE())  -- Filter for the current year
GROUP BY MONTH(OrderDate)
ORDER BY Month;
```
### To find the top 5 customers by total purchase amount.
```
SELECT TOP 5 Customer_Id, SUM(Sales) AS Total_purchase_amount
FROM [dbo].[SalesData]
GROUP BY Customer_Id
ORDER BY Total_purchase_amount DESC;
```
### To calculate the percentage of total sales contributed by each region.
```
SELECT SUM(Sales) AS Total_Sales
    FROM [dbo].[SalesData]
)
SELECT Region, 
       (SUM(Sales) / (SELECT Total_Sales FROM TotalSales)) * 100 AS Sales_percentage
FROM [dbo].[SalesData]
GROUP BY Region
ORDER BY Sales_percentage DESC;
```
### To identify products with no sales in the last quarter.
```
SELECT Product, DATEPART(QUARTER, OrderDate) AS Quarter
FROM  [dbo].[SalesData] 
WHERE DATEPART(QUARTER, OrderDate) = DATEPART(QUARTER, GETDATE()) - 1
  AND YEAR(OrderDate) = YEAR(GETDATE())
ORDER BY DATEPART(QUARTER, OrderDate);
```

# POWER BI

### PROJECT OBJECTIVE
The objective is to create a dashboard that visualizes the insights in Excel, SQL.
The dashboard should include a Sales Overview and top-performing products and regional breakdowns.

![Screenshot 2024-11-04 220727](https://github.com/user-attachments/assets/e8bcb621-3642-4eb3-bf8a-7e2854ddfc0f)






















