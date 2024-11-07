# Customer Data Project

### Project Title: Subscription Analysis

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Data Structure](#data-structure)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Conclusion](#conclusion)

### Project Overview:
---
This project involves analyzing customer data of a subscription service to identify segments and trends. My goal is to understand customer behavior, track subscription types and identify key trends in cancellations and renewals. This project showcases my ability to manipulate and derieve insights from large dataset, enabling me to make data driven recommendations.

### Data Sources:
---
Considering this is a capestone project, my trainer, The Incubator Hub provided the customer subscription dataset for this analysis.

### Data Structure:
---
The original dataset is an excel file with 75,000 rows and 7 columns which includes: CustomerID, Customer Name, Region, Subscriptionstart, Sudscriptionend, cancelled and Revenue.

### Tools Used:
---
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
---
The dataset went through some processes of data cleaning and preparations to ensure accuracy and consistency. This involves;
- Data Inspection.
- Addressing missing values.
- Removing Duplicates.

### Exploratory Data Analysis:
---
Exploratory Data Analysis involves the exploring of the data to answer some questions about the data such as;
- Retrieve the total number of customers from each region.
- Find the most popular subscription type by the number of customers.
- Find customers who canceled their subscription within 6 months.
- Calculate the average subscription duration for all customers.
- Find customers with subscriptions longer than 12 months.
- Calculate total revenue by subscription type.
- Find the top 3 regions by subscription cancellations.
- Find the total number of active and canceled subscription

### Data Analysis:
---
This is where I include some Excel Formulars, SQL Queries and DAX Functions used during the analysis.
#### Analysis using Excel Formulars:
  1. I started by creating a new column for Subscription duration(in months). 
  2. I also created another column for subscription status.   
     ![Creation of 2 columns(ii)](https://github.com/user-attachments/assets/4db333b0-289b-43f5-9e6d-bf73b2a0ecb1)

  3. Most popular subscription type.
     ![Most subscription type](https://github.com/user-attachments/assets/4dd96788-90d3-4a10-b56d-c7067b83726d)

 After the analysis on the microsoft excel worksheet, I summarized the data using pivot table.
 Below is the screenshot of the pivot tables created.
     ![pivot table customerdata](https://github.com/user-attachments/assets/f0977b25-cd91-4001-a778-f4e376dc7a87)

#### Analysis using SQL Queries:
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
   
#### Analysis using Microsoft Powerbi:
I loaded the data into powerbi for further analysis and visaulization. After loading the dataset, i took it to transform in power query where i will clean the data to ensure column quality

![Transformed data](https://github.com/user-attachments/assets/6a617274-000b-40ba-aea7-80afd0e2e329)

After i have ascertained the quality of the data, i began my analyss in microsoft powerbi.  I creating a conditional column for cancellation count and renewal count which will help me to calculate cancellation rate and renewal rate.

![CANCELLATION COUNT 2](https://github.com/user-attachments/assets/014c3f1e-3640-407c-8253-d8a174731d4c)

![RENEWAL COUNT 2](https://github.com/user-attachments/assets/5544ef02-011c-4759-af5d-db57edda9569)


I also created some measures using DAX functions.

![DAX Formulars for creating measures](https://github.com/user-attachments/assets/118372fa-3bd8-4f99-a40e-6098b2fa6d91)

### Data Visualization:
---
1. Subscription by Region:

   ![Subscription by region 2](https://github.com/user-attachments/assets/688a7c58-3c22-4362-9788-c5c6bf35f99a)

   #### Key Insight:
   The East regionis leading with 8,488 subscriptions, the South has 8,446 subsciptions, the North region has 8,433 subscriptions while West has 8,420 subscrbers.There is a balanced subsciption distribution 
   across the regions.

   #### Recommendation:
   Maintain consistent marketing efforts across the regions.
   

2. Subscription Type by Revenue.

   ![Revenue by subscription type](https://github.com/user-attachments/assets/401c2c15-e414-42c9-ac44-d7cd1d06c664)

   #### Key Insights:
   The Basic subscription type generates revenue of $34M while the Standard and the premium subscription type  generates 17M. Basic subscirption type drives the majority of the revenue.

   #### Recommendation:
   The variation between the Basic subscription type and the othe subscription is not minimal. Strong marketing campaigns should be deployed to the Standard and premium subscription plan. Pricing startegy should 
   be reviewed, discounts and promotions should also be adopted.

3. Cancellation vs Renewal.

   ![CANCELLATION OVERVIEW](https://github.com/user-attachments/assets/bc74c4f5-c05b-4511-95d3-19aeca1d475e)

   #### Key Insights:
   Cancellation rate is 55.09% while renewal rate is 44.91%. A higher cancellation rate indicates potential issues  with customer satisfaction.

   #### Recommendation:
   Investigate reasons for cancellations. This can be achieved through the use of survey or feedbacks. Enhance customer support services and offer incentives e.g loyalty discount.
  
4. Cancellation by Subscription Type.

   ![Subscription by cancellation](https://github.com/user-attachments/assets/90735140-04de-4f14-84f9-860009263c82)

   #### Key Insights:
   Basic has 5067 cancellations, Premium has 5064 cancellations while Standard has 5044 cancellations. There is  similar cancellation rate across the subsciption type. no significant differenec in cancellation 
   behaviour.

   #### Recommendations:
   Analyze customers feedbacks for common cancellation reasons. Review pricing strategy and enhance customer support 
   services.
  
  
5. Customer"s Subscription Preference.

   
   ![Customers Subscription preference](https://github.com/user-attachments/assets/f46b732b-f341-4ff2-b1ea-72f38b02f23e)

  #### Key Insights:
   Basic Subscription type is the most popular with a total number of 16,921 which is over 50% of the total subscibers. Premium subsciption type and Standard subscription type has a total of 8,446 subscribers 
   and 8,420 subscribers respectively.

  #### Strategic Recommendations:
   There should be targeted marketing for Premium and Standard subscription type, include exciting features in the premium and standard plan and also review their pricing strategy.

 
  ### Conclusion:
  ---
  The analysis reveals a relatively balanced distribution across regions, subscription types and customer preferences. However, there are opportunity for growth and improvement.
 
  #### Some Key Takeaways:
 - Balanced regional distribution with East slightly leading.
 - Basic Subscription is the most popular.
 - Cancellation rate is higher than renewal rate indicating issues with customer satisfaction.
 - Even distribution across Premium and Standard Subscription Type.
  #### Strategic Recommendation:
 - Review pricing strategy.
 - Enhance customer support services
 - Develop targeted marketing campaigns in under performing regions and under performing subscription types.
 - Anlyse customer feedbacks.
   

   
