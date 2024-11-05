# LITA-Capstone-Project
---
Here, I share a summary of my Project on Data Analysis with Incubator Hub.
## Project Overview
---
The project aims to explore data on Capstone for the period of January 2023 to August, 2024. Using excel, SQL and PowerBi to gain key insights on top selling products, sales by product, region, month.

### 1. Identify Top Selling Products
Our data exploration reveals top selling products as soes being the highest at N613,380 followed by shirt at 485,600, Hats at 316,195.
  
### 2.Find out Total Sales By Products
The total sales by product was revealed after analyis as hat being 15,929, followed by shoes at 14,402 following eachother keenly is shirt and gloves which stood at 12,388 and 12,369 respectively. Other products are socks and jacket at 7,921 and 5,452 respectively.

### 3. Find out Total Sales By Region
We observed total sales by region as follows: 927,820 for South as the highest, followed by East which stood at 485,925, next is North at 387,000 and the last region being West at 300,345.

### 4. Find out Total Sales By Month
Our table reveals monthly sales. Here we see February as month with the highest sales in both year 2023 and 2024, while  April experienced low sales in both years.

### 5. Create Metrics for Avearge Sales Per Product and Total Revenue By Region

### 6. Create a Report


## Tools Used
---

1. Microsoft Excel [Download Here](https://www.microsoft.com)
   * For Data Cleaning
   * Data Analysis
   * Visualisation
2. Structured Querry Language (SQL)- for data Querring
4. Power BI-for Visualisation
5. Github- for Portfolio Building

## Data Source
---
Data: {Download Here}(Capstone)

  
## Data Cleaning and Preparation
We perfored the following to cleanand prepare the data:
1. Data download and inspection
1. We removed duplicated Data using Excel.
2. We explored on Sales Data using Excel
   
## Exploration of Sales Data
---
### 1. Top Selling Products

### 2. Total Sales By Products
![image](https://github.com/user-attachments/assets/f84dd105-3984-4103-be3a-46c7ea08f3f3)

### 3. Total Sales By Region
![image](https://github.com/user-attachments/assets/b778f344-3225-4fdb-aa0e-f5a596515287)


### 4. Total Sales By Month
![image](https://github.com/user-attachments/assets/f316959f-80de-49b3-90df-1d37263bc423)


## Average Sales Per Product and Total Revenue By Region 
---
	
![image](https://github.com/user-attachments/assets/0d604b3d-b0ae-4501-a977-d0ca6c00d103)

![image](https://github.com/user-attachments/assets/249e8e12-a0b9-488c-bdb2-27db2dbdc6b0)

## SQL Querries
---
CREATE DATABASE CAPSTONEPROJECT

SELECT * FROM [dbo].[TOTALSALES]

DELETE FROM [dbo].[TOTALSALES] 
WHERE Customer_Id IS NULL AND REGION IS NULL AND QUANTITY IS NULL


1-----TOTAL SALES OF EACH PRODUCT CATEGORY------------ 

SELECT SUM(SALES) AS TOTAL_SALES_SHIRT FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'SHIRT'
SELECT SUM(SALES) AS TOTAL_SALES_SHOES FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'SHOES'
SELECT SUM(SALES) AS TOTAL_SALES_HAT FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'HAT'
SELECT SUM(SALES) AS TOTAL_SALES_SOCKS FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'SOCKS'
SELECT SUM(SALES) AS TOTAL_SALES_JACKET FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'JACKET'
SELECT SUM(SALES) AS TOTAL_SALES_GLOVES FROM [dbo].[TOTALSALES] WHERE PRODUCT = 'GLOVES'

2----------NUMBER OF SALES TRANSACTION IN EACH REGION-------- 

SELECT region,
COUNT(OrderID) AS REGIONALSALES FROM [dbo].[TOTALSALES]
GROUP BY REGION
ORDER BY REGIONALSALES DESC


3-------- HIGHEST SELLING PRODUCT BY TOTAL SALES VALUE-------------

SELECT TOP 1 (PRODUCT), 
SUM(SALES) AS TOTALSALES FROM[dbo].[TOTALSALES]
GROUP BY PRODUCT

4--------CALCULATE TOTAL REVENUE PER PRODUCT--------

SELECT PRODUCT,
SUM(SALES) AS TOTALREVENUE FROM[dbo].[TOTALSALES]
GROUP BY PRODUCT
ORDER BY TOTALREVENUE DESC

5-------CALCULATE MONTHLY SALES TOTALS FOR THE CURRENT YEAR-------

SELECT MONTH(ORDERDATE) AS MONTH,
SUM(SALES) AS MONTHLY_TOTAL_SALES
FROM [dbo].[TOTALSALES]
WHERE YEAR(ORDERDATE)=YEAR(GETDATE())
GROUP BY MONTH(ORDERDATE)
ORDER BY MONTH

6-------TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT------

SELECT TOP (5) Customer_Id,
SUM(SALES) as Total_Purchase
FROM [dbo].[TOTALSALES]
GROUP BY Customer_id
ORDER BY Total_Purchase DESC

7---------PERCENTAGE OF TOTAL SALES CONTRIBUTED BY EACH REGION------

SELECT REGION,
SUM(SALES) AS PECENTAGE_REG_SALES,
(SUM (SALES)*100.0/(SELECT SUM(SALES)
FROM[dbo].[TOTALSALES])) AS PERCENTAGE_REG_SALES FROM[dbo].[TOTALSALES]
GROUP BY REGION
ORDER BY PERCENTAGE_REG_SALES DESC

8-------PRODUCTS WITH NO SALES IN THE LAST QUARTER----------


SELECT DISTINCT PRODUCT FROM [dbo].[TOTALSALES]
GROUP BY PRODUCT HAVING SUM(CASE WHEN ORDERDATE BETWEEN '2024-06-01' AND '2024-08-31'
THEN 1 ELSE 0 END) = 0

## Visualisation of Sales Data
---

## Findings
From the report, we found out top selling product is Shoes at 613,380 while Hats as te lowest being 316,195.

We found total sales by product as hat 15,929, followed by shoes at 14,402 following shirt and gloves at 12,388 and 12,369 respectively. Other products are socks and jacket at 7,921 and 5,452 respectively.

We observed South has the highest sales by region at 927,820, followed by East at 485,925, next is North at 387,000 and the last region being West at 300,345.

Monthly sale as February as month with the highest sales in both year 2023 and 2024, while  April experienced low sales in both years.

---
## Recommendations
---
Following the above findings, we will recommend that the company or store should ensure that they are enouugh stock to sell in February so they do not run out of suppply since this month appears to be the highest for both year.

We recommend, that an investigation be done to findout reason for poor sales in April as this is constant in both years.

South has the highest sales, aking i the cash cow of the company. As such, we recommend more resources should be put in place to keep this rate at maximum in that region while we probe on the reason for the low sales in the Western region.

## Conculsion
---
The project explores data on Capstone for the period of January 2023 to August, 2024. Using excel, SQL and PowerBi to gain key insights on top selling products, sales by product, region, month. Metrics such as average sales per product and total revenue by region done with report created.




