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
The primary source of data used here is Lita Capstone Dataset.CSV. Download [Lita Capstone Dataset Download](https://shorturl.at/iVtt2)

### Tools Used
---
- Microsoft Excel 
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
- Canceled: Indicates if the subscription was canceled (True/False).
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
1. The total number of customers from each region. 
2. The most popular subscription type by the number of customers. 
3. Customers who canceled their subscription within 6 months. 
4. The average subscription duration for all customers. 
5. Customers with subscriptions longer than 12 months. 
6. The total revenue by subscription type. 
7. Top 3 regions by subscription cancellations. 
8. The total number of active and canceled subscriptions. 


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
1.  Revenue by Subscription Type: The donut chart shows that Basic subscriptions bring in the most revenue, making it a top choice among our customers.

2.  Regional Revenue: Our pie chart highlights that, on average, each region generates around $17 million in revenue, with some regions clearly outperforming others.

3. Most Popular Subscription: The clustered bar chart tells us that Basic is the most subscribed option, with over 10 customers choosing this plan, showing it’s quite popular.

4. Revenue from Active vs. Canceled Subscriptions: The donut chart also breaks down revenue by subscription status. Over $30 million came from customers who’ve canceled, while active customers contribute about $37 million, which indicates good ongoing engagement despite some turnover.

5.  Average Subscription Duration: Our data shows that the average subscription length is about 12 months, or roughly 360 days. This is decent, but there’s room to improve retention and keep customers on board longer.

6. Revenue by Region: A table layout summarizes how each region contributes to the overall revenue, offering a clear breakdown of performance by area.

8. Regional Subscription Breakdown: The final chart compares active and canceled subscriptions by region. The East stands out with no cancellations and over 8,488 active customers, while the North has the most cancellations (5,067) and only 3,366 active subscriptions, suggesting a need for better retention efforts there.

### Recommendation
----
1.  Promotional programs such as referrals and campaigns should be targeted in High-Churn Area such as the Northern region which has the highest canceled subscription.

2.  We need to build on our Popular Subscription Plans(Basic subscriptions) as well to encourage an increase in subscribers by adding adding perks/Incentives to make them even more appealing.

3.  It would be valuable to reach out and engage previously subscribed (but now canceled) customers, for their feedback and also with personalized offers to encourage them to resubscribe, as a substantial chunk of revenue came from them.

4.  To increase the average duration beyond 12 months, offering benefits or rewards for longer-term commitments might keep customers around longer.

5.  To bring in more active subscribers, focusing on underperforming regions with targeted marketing could help boost both revenue and customer engagement.

