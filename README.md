# Project Title
---
## Customer Subscription Analysis Project
---



### Table Outline for the Portfolio
---
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools Used](#tools-used)
- [Data Dictionary](#data-dictionary)
- [Data Cleaning and Preparations](#data-cleaningand-preparation)
- [Data Analysis](#data-analysis)
- [Data Visualization](#data-visualization)
- [Conclusion](#conclusion)
- [Recommendation](#recommendation)

### Project Overview
---
This project focuses on analyzing customer subscription trends, including patterns in subscriptions, cancellations, and renewals. It also aims to identify the most popular subscription types among customers.

### Data Sources
---
The primary source of data used here is Lita Capstone Dataset.CSV. This will be made available for view.

### Tools Used
---
- Microsoft Excel [Lita Capstone Dataset Download](https://shorturl.at/iVtt2)
  1. For data cleaning
  2. For Analysis
     
- SQL - Structured Query Language for Querying of Data
- Power B.I - For visualization of the dataset
- GitHub for Portfolio Building

### Data Dictionary
Outline the terminology and definitions of key column headers specific to the dataset. This section ensures clarity for anyone reviewing the project.

- CustomerID: Unique identifier for each customer.
- CustomerName: Name of the customer.
- Region: Geographic area where the customer is located.
- SubscriptionType: Type of subscription chosen by the customer.
- SubscriptionStart: Date when the subscription began.
- SubscriptionEnd: Date when the subscription ended.
- Canceled: Indicates if the subscription was canceled (Yes/No).
- Revenue: Income generated from the customer's subscription.

### Data Cleaning and Preparations
----
In the initial phase of the data cleaning and preparations, we preform the following actions;
1.  Data inspection and loading
2.  Handling missing variables
3.  Data cleaning and formatting

### Exploratory data Analysis
----
#### Customer Subscriptions
 This involved analysing the data to answer the following questions;
a. retrieve the total number of customers from each region. 
b. find the most popular subscription type by the number of customers. 
c. find customers who canceled their subscription within 6 months. 
d. calculate the average subscription duration for all customers. 
e. find customers with subscriptions longer than 12 months. 
f. calculate total revenue by subscription type. 
g. find the top 3 regions by subscription cancellations. 
h. find the total number of active and canceled subscriptions. 


### Data Analysis
---
```SQL
1.  Retrieve the total number of customers from each region.
 
Select  region, count(distinct Customerid) as total_customers 
from [dbo].[CustomerData]
Group by region;

```

```SQL
2. Find the most popular subscription type by the number of customers. 

Select top 1 subscriptiontype, count(distinct customerid) as total_customers
From  [dbo].[CustomerData]
Group by subscriptiontype 
Order by total_customers desc;
```

```SQL
3. Find customers who canceled their subscription within 6 months. 

Select customerid
From [dbo].[CustomerData]
Where datediff (month, subscriptionstart, subscriptionend) <= 6;
```

```SQL
4.   Calculate the average subscription duration for all customers. 

Select avg(datediff(day, subscriptionstart, subscriptionend)) as avg_subscription_duration
From [dbo].[CustomerData]
```

```SQL
5.  Find customers with subscriptions longer than 12 months. 

SELECT CustomerID
FROM [dbo].[CustomerData]
WHERE DATEDIFF(month, SubscriptionStart, SubscriptionEnd) > 12;

```


```SQL
6. Calculate total revenue by subscription type.

Select Subscriptiontype,
Sum(revenue) as Total_revenue 
From [dbo].[CustomerData]
Group by subscriptiontype;
```

```SQL
7.  Find the top 3 regions by subscription cancellations. 

Select top 3 region,
Count(*) as subscriptionend_count
From [dbo].[CustomerData]
Where subscriptionend is null
Group by region
Order by subscriptionend_count desc;

```

### Data Visualization
---
<img width="583" alt="Customer Analysis Dashboard" src="https://github.com/user-attachments/assets/390e9818-2aa4-4dde-88b7-8b71829cbd97">



<img width="580" alt="Customer Analysis Dashboard 2" src="https://github.com/user-attachments/assets/de735558-0fe5-40f5-9d33-d4111b3bbbf1">

<img width="573" alt="Customer Analysis Dashboard 3" src="https://github.com/user-attachments/assets/2c04c584-66a4-4598-b059-1455e17249b3">




### Conclusion
---
After my analysis,these were the insights deducted;
1.  

### Recommendation

