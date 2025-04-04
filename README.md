# Music Store Sales SQL Analysis

## Project Overview
This project analyzes an invoice dataset using SQL to extract meaningful business insights. The goal is to identify the best customers, top-performing locations, popular music genres, and revenue trends. By leveraging SQL queries, we provide actionable recommendations to improve business performance.

## Tools Used
- PostgreSQL

## Exploratory Data Analysis (EDA)
1. **Senior-most Employee:** Identified based on job title.
2. **Most Invoiced Country:** Determined by counting the number of invoices per country.
3. **Top 3 Invoice Amounts:** Sorted by highest total invoice values.
4. **Best Customer Location:** City with the highest total sales.
5. **Best Customer:** The customer who has spent the most money.
6. **Rock Music Listeners:** Identified customers who listen to rock music.
7. **Top 10 Rock Artists:** Most frequently purchased rock artists.
8. **Longest Songs:** Tracks longer than the average song length.
9. **Customer Spending on Best-selling Artist:** Amount spent on the most popular artist.
10. **Most Popular Genre by Country:** Determined using purchase data.
11. **Top Customer by Country:** Highest spending customers by country.

## Data Analysis
Incluing some interesting code and features I worked with

```sql
with top_customer as
(
select c.customer_id, c.first_name, c.last_name, i.billing_country, sum(i.total)as total_spending,
row_number() over(partition by i.billing_country order by sum(i.total) desc)as rownum
from customer c
join invoice i on c.customer_id = i.customer_id
group by 1,2,3,4
order by 4 asc, 5 desc
)
select *
from top_customer
where rownum <= 1;
```

## Results and Findings
1. **Best Performing Country:** The country with the highest number of invoices.
2. **Highest Spending Customers:** Identified top customers in terms of total spending.
3. **Top Music Genre Per Country:** Determined the most popular music type in different regions.
4. **Best-selling Artist:** Found the artist who generated the most revenue.
5. **Top Cities for Business:** Locations with the highest sales volume.

## Recommendations
- **Target High-Revenue Cities:** Expand marketing efforts in cities with the highest sales.
- **Promote Popular Music Genres:** Offer promotions on top-selling genres to attract more customers.
- **Loyalty Programs for Top Customers:** Reward high-spending customers to encourage repeat purchases.
- **Optimize Inventory Based on Demand:** Stock more of the top-selling artists and genres.
- **Focus on High-Spending Countries:** Allocate resources efficiently to maximize revenue from high-performing locations.

## How to Run the Queries
1. Import the dataset into PostgreSQL.
2. Open the SQL script and execute queries in order.
3. Analyze the results to derive insights.

---
This repository contains the SQL script with all queries used for analysis. Feel free to explore and modify the queries for further insights!


