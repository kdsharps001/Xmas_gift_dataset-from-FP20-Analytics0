# Xmas_gift_dataset-from-FP20-Analytics0
This project includes the analysis of customer gift purchases during the period of Christmas.

## TITLE OF PROJECT
Xmas Gift Sales Dataset

## PROJECT OVERVIEW

The project aims to analyze and derive actionable insights from a dataset capturing sales transactions during the Christmas season. By leveraging SQL queries within SQL Server Management Studio and also utilizing Power BI, the analysis will focus on various aspects including customer demographics, product performance, geographical sales distribution, and purchasing behaviors during the festive period.

Approach:
- Data Collection: Utilize the provided Christmas dataset containing information on sales transactions, customer demographics, products, payments, and more.
- Data Exploration: Use SQL queries to explore the dataset and gain a comprehensive understanding of the available information.
- Analysis and Insights:
    - Customer Insights: Analyze customer demographics, purchasing behaviors, Xmas budgets, and payment preferences.
    - Product Performance: Determine top-selling products, profitable categories, and identify products with high-profit margins.
    - Geographic Analysis: Explore sales distribution among different countries and cities, along with preferred payment methods.
    - Temporal Trends: Analyze sales trends based on time factors such as hourly purchases and monthly sales patterns.
- Recommendations: Derive actionable recommendations based on the insights obtained, focusing on marketing strategies, customer targeting, product enhancement, cost optimization, and payment method preferences.
- Limitations and Considerations: Address potential limitations in data quality, completeness, and context, providing a framework for informed decision-making considering these constraints.

Outcome:
- Comprehensive insights derived from the analysis will facilitate data-driven decision-making for optimizing sales strategies, enhancing customer experiences, and maximizing profits during the Christmas season.
- A project report summarizing key findings, actionable recommendations, limitations, and considerations for stakeholders to make informed business decisions and potential strategies for future holiday seasons.

This project aims to provide a deep understanding of sales dynamics during Christmas, enabling businesses to make strategic decisions to enhance sales, improve customer satisfaction, and optimize operational efficiency during festive periods.

### DATA SOURCE(S)
FP20 Analytics
### TOOLS
- SQL
- POWERBI
    - [dashboard](https://app.powerbi.com/view?r=eyJrIjoiY2U1Zjg3ZjItYTc3Mi00YWZmLWIzYjMtY2U5NjAwZDNhY2EzIiwidCI6ImRmODY3OWNkLWE4MGUtNDVkOC05OWFjLWM4M2VkN2ZmOTVhMCJ9)

### DATA CLEANING
The data provided by FP20 Analytics was a clean data with neither errors nor missing values.

### TYPE OF ANALYSIS
The type of analysis performed on the Christmas dataset using SQL queries within SQL Server Management Studio can be categorized as exploratory and descriptive analysis.

1. **Exploratory Analysis:**
   - Exploring the dataset to understand its structure, available columns, and general patterns present in the data.
   - Identifying relationships between different variables such as customer demographics, product categories, sales figures, and geographical distribution.
   - Investigating various dimensions within the dataset to uncover potential trends, outliers, or interesting patterns that could guide further analysis.

2. **Descriptive Analysis:**
   - Calculating summary statistics like counts, averages, maximum and minimum values, and totals for different attributes such as sales, profits, customer demographics, product types, and geographical aspects.
   - Categorizing and grouping data to gain insights into customer behaviors, popular products, preferred payment methods, and sales trends during the Christmas period.
   - Providing a detailed overview and description of the dataset's characteristics and distributions to comprehend key metrics and trends.

Through the SQL queries executed in SQL Server Management Studio, the analysis aimed to derive meaningful insights, understand patterns, and summarize the dataset's information without employing predictive modeling or hypothesis testing commonly associated with more advanced analytical methods like predictive analytics or inferential statistics. The focus was on understanding historical data patterns to draw actionable insights and make data-informed decisions.

### DATA ANALYSIS(SQL)
Below are 23 questions that was used as comments for analysis on the Xmas dataset in SQL Server Management Studio, along with SQL code to answer the questions below:

1. **What is the total number of records in the dataset?**
```sql
SELECT COUNT(*) AS TotalRecords
FROM Xmastable;
```

2. **What is the average age range of customers making purchases?**
```sql
SELECT AVG(customer_age_range) AS AvgAgeRange
FROM Xmastable;
```

3. **What were the top 5 most purchased product types during Christmas?**
```sql
SELECT TOP 5 product_type, COUNT(*) AS TotalPurchases
FROM Xmastable
GROUP BY product_type
ORDER BY TotalPurchases DESC;

```

4. **How many different product categories were sold during Christmas?**
```sql
SELECT COUNT(DISTINCT product_category) AS UniqueCategories
FROM Xmastable;
```

5. **What were the top 3 countries with the highest total sales?**
```sql
SELECT TOP 3 country, SUM(total_sales) AS TotalSales
FROM Xmastable
GROUP BY country
ORDER BY TotalSales DESC;
```

6. **What is the overall total sales and profit for all purchases during Christmas?**
```sql
SELECT SUM(total_sales) AS TotalSales, SUM(profit) AS TotalProfit
FROM Xmastable;
```

7. **How many purchases were made by each gender during Christmas?**
```sql
SELECT gender, COUNT(*) AS TotalPurchases
FROM Xmastable
GROUP BY gender;
```

8. **What were the average and maximum Xmas budget set by customers?**
```sql
SELECT AVG(xmas_budget) AS AvgXmasBudget, MAX(xmas_budget) AS MaxXmasBudget
FROM Xmastable;
```

9. **Which payment methods were used for purchases and how many times each was utilized?**
```sql
SELECT payment_method, COUNT(*) AS PaymentCount
FROM Xmastable
GROUP BY payment_method;
```

10. **What was the average quantity of products purchased per transaction?**
```sql
SELECT AVG(quantity) AS AvgQuantity
FROM Xmastable;
```

11. **Which cities had the highest and lowest average unit prices for products sold during Christmas?**
```sql
SELECT TOP 1 city, AVG(unit_price) AS AvgUnitPrice
FROM Xmastable
GROUP BY city
ORDER BY AvgUnitPrice DESC;

SELECT TOP 1 city, AVG(unit_price) AS AvgUnitPrice
FROM Xmastable
GROUP BY city
ORDER BY AvgUnitPrice ASC;
```

12. **How many purchases were made in each customer age range category?**
```sql
SELECT customer_age_range, COUNT(*) AS PurchasesCount
FROM Xmastable
GROUP BY customer_age_range;
```

13. **What is the total tax amount collected during Christmas?**
```sql
SELECT SUM(tax_amount) AS TotalTaxAmount
FROM Xmastable;
```

14. **Which product had the highest sales and what was the quantity sold?**
```sql
SELECT TOP 1 product_name, MAX(total_sales) AS MaxSales, quantity
FROM Xmastable
GROUP BY product_name, quantity
ORDER BY MaxSales DESC;
```

15. **How many purchases were made by customers in each country?**
```sql
SELECT country, COUNT(*) AS PurchasesCount
FROM Xmastable
GROUP BY country;
```

16. **What was the most common purchase type during Christmas?**
```sql
SELECT TOP 1 purchase_type, COUNT(*) AS PurchaseTypeCount
FROM Xmastable
GROUP BY purchase_type
ORDER BY PurchaseTypeCount DESC;
```

17. **What is the total cost and profit for each product category?**
```sql
SELECT product_category, SUM(cost) AS TotalCost, SUM(profit) AS TotalProfit
FROM Xmastable
GROUP BY product_category;
```

18. **How many purchases were made in each hour of the day during Christmas?**
```sql
SELECT DATEPART(HOUR, time) AS HourOfDay, COUNT(*) AS PurchasesCount
FROM Xmastable
GROUP BY DATEPART(HOUR, time)
ORDER BY HourOfDay;
```

19. **What were the top 5 products with the highest profit margins?**
```sql
SELECT TOP 5 product_name, (SUM(total_sales) - SUM(cost)) AS ProfitMargin
FROM Xmastable
GROUP BY product_name
ORDER BY ProfitMargin DESC;
```

20. **How many purchases were made in each product type per country?**
```sql
SELECT product_type, country, COUNT(*) AS PurchasesCount
FROM Xmastable
GROUP BY product_type, country;
```

21. **Which month had the highest total sales during Christmas?**
```sql
SELECT TOP 1 DATEPART(MONTH, date) AS SalesMonth, SUM(total_sales) AS TotalSales
FROM Xmastable
GROUP BY DATEPART(MONTH, date)
ORDER BY TotalSales DESC;
```

22. **What was the distribution of gender among different product categories?**
```sql
SELECT product_category, gender, COUNT(*) AS GenderCount
FROM Xmastable
GROUP BY product_category, gender;
```

23. **How many purchases were made in each age range category for male customers?**
```sql
SELECT customer_age_range, COUNT(*) AS PurchasesCount
FROM Xmastable
WHERE gender = 'Male'
GROUP BY customer_age_range;
```

### RESULTS
The analysis of the Xmas dataset provides a comprehensive view of sales transactions during the festive Christmas season, uncovering several crucial insights. Total sales reached $3,371,636, with a substantial profit margin of $2,579,472, reflecting the overall success during this period. The dataset portrays diverse purchase behaviors across three primary product types: children (7,566 purchases), adults (4,448 purchases), and teens (4,369 purchases), indicating varied preferences among different age ranges. Key countries such as Austria ($605,841.8), Poland ($601,634.7), and Italy ($376,893.1) emerged as top performers, suggesting potential areas for market expansion. Notably, Poland had the highest purchase count of 3,077, while the Netherlands recorded the lowest purchase count of 754 among the listed .countries

### RECOMMENDATIONS
To leverage the dataset insights, businesses should tailor marketing strategies to target specific customer segments and geographical regions. Optimizing payment methods to accommodate prevalent preferences such as cash (8,262 transactions) and credit/debit cards (3,061 transactions) can significantly enhance customer satisfaction. Focusing on high-selling products like Chess Sets and Hot Wheels Car Sets, which demonstrated both high sales volumes and considerable profit margins, can optimize inventory management and potentially increase overall profitability. Targeting high-budget Christmas shoppers and capitalizing on peak sales hours, particularly at 18:00 (1,440 purchases), could maximize sales opportunities.

### Limitations
The datasets provided was clean and easy to read. However, the link to the pctures of stores and the countries were not accessible online.

