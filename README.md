### LITA-PROJECT2

## INCUBATOR HUB: This repository contains a comprehensive analysis of aims to generate insights into the sales performance of a sales data. Using Excel, SQL & PowerBI for analysis, report & visualization.

### Project Title: Customer Data

### Project Overview
---
This project aims to analysis customer data for subsciption service as well as identify the segment and trends. The goal is to understand the customer behavior, track subscription types & identify key trends.

### Data sources

The primary sorce of tis data is [LITA Capstone Dataset.xlsx](https://github.com/user-attachments/files/17638564/LITA.Capstone.Dataset.xlsx)

### Tools & Technologies
---
- Microsoft Excel:
  1. For data analysis & visualization.
  2. For summary of the data set
  3. For creating charts & reports.

  - Structured Query Language
    1. To retrieve and analyze data.
    2. To manage and manipulate data.
    3. To create queries and modify data.
       
       - PowerBi:
         1. For data visualization
         2. For data modeling
         3. For creating amazing insight on the dashboard.
        
         ### Data Cleaning
         ---
 - Identify the duplicate in the column
 ![Cleansed Salesdata](https://github.com/user-attachments/assets/087d0cbf-86b4-4263-bf00-1c38e8a65a13)
-  Filter the column headers
-  Adding column to generate the subscription duration
  ![Screenshot (71)](https://github.com/user-attachments/assets/65b99101-2c8c-4b5e-bfd2-3c704bd009b7)

![BarChart CustomerData](https://github.com/user-attachments/assets/23066a9a-f102-4779-8566-cb4b64cf9a33)


![Pivot Table customerDate](https://github.com/user-attachments/assets/6efcda45-1c0c-49a6-83fc-9853e820354f)

### Data Analysis Exploratory
---
This part includes lines of code or queries
SELECT * FROM [dbo].[LITA PJ ]

---Retrieve the total number of customers from each region.---
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers
FROM [dbo].[LITA PJ ]
GROUP BY Region

---Find the most popular subscription type by the number of customers---
SELECT SubscriptionType,COUNT(CustomerID)AS NO_Of_Customers
FROM [dbo].[LITA PJ ]
GROUP BY SubscriptionType

--Find customers who canceled their subscription within 6 months----
SELECT CustomerName,Canceled,SubscriptionStart
FROM [dbo].[LITA PJ ]
WHERE Canceled =0 AND MONTH(SubscriptionStart) BETWEEN 1 AND 6

---Calculate the average subscription duration for all customers----
SELECT Count(CustomerID) As
All_Customers,AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) AS
Average_Subscription_Duration
FROM [dbo].[LITA PJ ]
WHERE SubscriptionEnd IS NOT NULL

----Find customers with subscriptions longer than 12 months.DATEDIFF---
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd
FROM [dbo].[LITA PJ ]
WHERE DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd) >=12

--- Calculate total revenue by subscription type---
SELECT SubscriptionType,SUM(Revenue) AS Total_Revenue
FROM[dbo].[LITA PJ ]
GROUP BY SubscriptionType

---Find the top 3 regions by subscription cancellations---
   SELECT TOP 3 Region,Canceled
   FROM [dbo].[LITA PJ ]

---Find the total number of active and canceled subscriptions---
SELECT SUM( CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
       SUM (CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
       FROM [dbo].[LITA PJ ]
       GROUP BY CustomerID

![Screenshot (75)](https://github.com/user-attachments/assets/8d4a5b33-7fa0-4c82-a582-20183dbb8474)

 ### PowerBi
 ---
 This includes data visualization, data cleaning and preparation

![CustomerData PowerBi](https://github.com/user-attachments/assets/1795b169-3b00-45ee-8117-f54e206f46ad)


