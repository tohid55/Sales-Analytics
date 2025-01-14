# Super-Store Sales Analytics

## Table of contents

- [Objectives](#objectives)
- [Learning](learning)
- [Project Overview](Project-Overview)
- [Data Source](Data-Source)
- [Tools](Tools)
- [Data Cleaning/Preparation](Data-Cleaning/Preparation)
- [Exploratory Data Analysis](Exploratory-Data-Analysis)
- [Data Analysis](Data-Analysis)
- [Results/Findings](Results/Findings)
- [Recommendations](Recommendations)
- [Limitations](Limitations)


### Objectives

To contribute to the success of a business by utilizing data analysis technique,
specificalyy focusing on TIME SERIES ANALYSIS, to provide valuable insight and 
accurate SALES FORECASTING.

1. Dashboard Creation 
2. Data Analysis
3. Sale Forecasting
4. Actionable Insights and Recommendations

### Learning

Incorporated data analysis techniques, specializing in TIME SERIES ANALYSIS, to 
deliver valuable INSIGHTS, accurate SALES FORECASTING, and INTERACTIVE DASHBOARD
creation, driving business success.

### Project Overview

This data analysis project aims to provide insights into the sales performance of an e-commerce company over past year.
By analyzing various aspects of the sales data, we seek to identify trends, make data-driven recommendation, and gain a deeper understanding of the company's performance.

### Data Source 

Sales Data: The primary dataset used for this analysis is the "SuperStore Sales DataSet.xlsx" file, containing detailed information about each sale made by the company.

### Tools

- Excel - Data Cleaning
- SQL - Data Analysis
- Power BI - Creating Reports 

### Data Cleaning/Preparation 

In the Initial data preparation phase, we performed the following tasks:
1. Data Transform and Inspection
2. Handling missing values
3. DAX Calculations
4. Data cleaning and formatting

### Exploratory Data Analysis

EDA involved exploring the sales data to answer key question, such as:

- What is the overall sales trend?
- which product are top sellers?
- what are the peak sales periods?
- what is the monthly Profit by YoY?
- what is the sales based on regions, segments, payment mode?
- In which Region has the Highest sales?
- what will be the forecast of 15 days based on sales?

### Data Analysis

Include some interesting code/features worked with

- Overall Sales Trend
  
```sql
SELECT 
    YEAR(SalesDate) AS Year,
    MONTH(SalesDate) AS Month,
    SUM(SalesAmount) AS TotalSales
FROM Sales
GROUP BY YEAR(SalesDate), MONTH(SalesDate)
ORDER BY Year, Month;
```
- Top-Selling Products

```
SELECT 
    ProductName,
    SUM(SalesAmount) AS TotalSales,
    COUNT(SalesID) AS UnitsSold
FROM Sales
JOIN Products ON Sales.ProductID = Products.ProductID
GROUP BY ProductName
ORDER BY TotalSales DESC
LIMIT 10;
```
- Monthly Profit by YoY

```
SELECT 
    YEAR(SalesDate) AS Year,
    MONTH(SalesDate) AS Month,
    SUM(SalesAmount) - SUM(COGS) AS MonthlyProfit
FROM Sales
JOIN Products ON Sales.ProductID = Products.ProductID
GROUP BY YEAR(SalesDate), MONTH(SalesDate)
ORDER BY Year, Month;
```
- Sales by Region, Segments, and Payment Mode

```
SELECT 
    Region,
    SUM(SalesAmount) AS TotalSales
FROM Sales
JOIN Customers ON Sales.CustomerID = Customers.CustomerID
GROUP BY Region
ORDER BY TotalSales DESC;
```
```
SELECT 
    Segment,
    SUM(SalesAmount) AS TotalSales
FROM Sales
JOIN Customers ON Sales.CustomerID = Customers.CustomerID
GROUP BY Segment
ORDER BY TotalSales DESC;
```
```
SELECT 
    PaymentMode,
    SUM(SalesAmount) AS TotalSales
FROM Sales
GROUP BY PaymentMode
ORDER BY TotalSales DESC;
```

- Region with the Highest Sales

```
SELECT 
    Region,
    SUM(SalesAmount) AS TotalSales
FROM Sales
JOIN Customers ON Sales.CustomerID = Customers.CustomerID
GROUP BY Region
ORDER BY TotalSales DESC
LIMIT 1;
```

### Results/Findings

The analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
2. In Category office supplies is the best-performing category in terms of sales and revenue.
3. customer segment with home office should be targeted for marketing efforts.

### Recommendations

Based on the analysis, we recommend the following actions:
- Invest in marketing and promotions during peak sales season to maximize revenue.
- Focus on expanding and promoting products.
- Implementing a customer segmentation strategy to target customers seffectively.

### Limitations

I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusion from the analysis. There are stills a few outliers even after the omissions but even then we can stills see that there is positive correlation between both budget and number of votes with revenue.
