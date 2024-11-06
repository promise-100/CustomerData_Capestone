# Customer Data Project

### Project Title: Subscription Analysis

### Project Overview:
This project involves analyzing customer data for a subscription service to identify segments and trends. My goal is to understand customer behavior, track subscription types and identify key trends in cancellations and renewals. This project showcases my ability to manipulate and derieve insights from large dataset, enabling me to make data driven recommendations.

### Data Sources:
Considering this is a capestone project, my trainer, The Incubator Hub provided the customer subscription dataset for this analysis.

### Data Structure:
The original dataset is an excel file with 75,000 rows and 7 columns which includes: CustomerID, Customer Name, Region, Subscriptionstart, Sudscriptionend, cancelled and Revenue.

### Tools Used:
- Microsoft Excel [Download Here](https:www.microsoft.com)
   1. For Data Cleaning and Analysis.
   2. For Data Analysis.
- SQL - Structured Query Language
   1. For Querying of Data.
- Microsoft Powerbi [Download Here](https:www.microsoft.com)
   1. For Data Analysis
   2. For Data Visualization.
- GitHub
   1. For Portfolio Building.

### Data Cleaning and Preparation:
The dataset went through some processes of data cleaning and preparations to ensure accuracy and consistency. This involves;
- Data Inspection.
- Addressing missing values.
- Removing Duplicates.

### Exploratory Data Analysis(EDA).
EDA involved the exploring of the data to answer some questions about the data such as;
- Retrieve the total number of customers from each region.
- Find the most popular subscription type by the number of customers.
- Find customers who canceled their subscription within 6 months.
- Calculate the average subscription duration for all customers.
- Find customers with subscriptions longer than 12 months.
- Calculate total revenue by subscription type.
- Find the top 3 regions by subscription cancellations.
- Find the total number of active and canceled subscription

### Data Analysis:
This is where I include some Excel Formulars, SQL Queries and DAX Functions used during the analysis.
#### Analysis using Excel Formulars used:
  1. I started by creating a new column for Subscription duration(in months). 
  2. I also created another column for subscription status.   
     ![Creation of 2 columns(ii)](https://github.com/user-attachments/assets/4db333b0-289b-43f5-9e6d-bf73b2a0ecb1)

  3. Most popular subscription type.
     ![Most subscription type](https://github.com/user-attachments/assets/4dd96788-90d3-4a10-b56d-c7067b83726d)

 After the analysis on the microsoft excel worksheet, I summarized the data using pivot table.
 Below is the screenshot of the pivot tables created.
     ![pivot table customerdata](https://github.com/user-attachments/assets/f0977b25-cd91-4001-a778-f4e376dc7a87)

#### Analysis using SQL Queries used:
  I used SQL Queries to answer the questions below:

 - Retrieve the total number of customers from each region.
   ```
   SELECT REGION, COUNT(DISTINCT CUSTOMERID) AS TOTAL_CUSTOMERS
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   GROUP BY REGION
   ```
 - Find the most popular subscription type by the number of customers.
   ```
   SELECT REGION, COUNT(DISTINCT CUSTOMERID) AS TOTAL_CUSTOMERS
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   GROUP BY REGION
   ```
 - Find customers who canceled their subscription within 6 months.
   ```
   SELECT CUSTOMERID, SUBSCRIPTION_DURATION FROM [dbo].[CUSTOMERDATA_PROJECT]
   WHERE SUBSCRIPTION_STATUS = 'CANCELLED' AND SUBSCRIPTION_DURATION <= 6
   ```
 - Calculate the average subscription duration for all customers.
   ```
   SELECT AVG(SUBSCRIPTION_DURATION) AS AVERAGE_SUBSCRIPTION_DURATION
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   ``` 
 - Find customers with subscriptions longer than 12 months.
   ```
   SELECT CUSTOMERID, SUBSCRIPTION_DURATION FROM [dbo].[CUSTOMERDATA_PROJECT]
   WHERE SUBSCRIPTION_DURATION > 12
   ```
 - Calculate total revenue by subscription type.
   ```
   SELECT SUBSCRIPTIONTYPE, SUM(REVENUE) AS TOTAL_REVENUE
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   GROUP BY SUBSCRIPTIONTYPE
   ORDER BY TOTAL_REVENUE DESC
   ```
 - Find the top 3 regions by subscription cancellations.
   ```
   SELECT TOP 3 REGION, COUNT(SUBSCRIPTION_STATUS) AS CANCELLATION_COUNT
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   WHERE SUBSCRIPTION_STATUS = 'CANCELLED'
   GROUP BY REGION
   ORDER BY CANCELLATION_COUNT DESC
   ```
 - Find the total number of active and canceled subscription.
   ```
   SELECT 
   SUM(CASE WHEN SUBSCRIPTION_STATUS = 'ACTIVE' THEN 1 ELSE 0
		 END) AS ACTIVE_SUBSCRIPTION,
   SUM(CASE WHEN SUBSCRIPTION_STATUS = 'CANCELLED' THEN 1 ELSE 0
		 END) AS CANCELLED_SUBSCRIPTION
   FROM [dbo].[CUSTOMERDATA_PROJECT]
   ```
   

