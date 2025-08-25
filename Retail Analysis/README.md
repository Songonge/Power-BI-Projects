# Retail Sales Case Study
----

## Table of Contents  
1. [Introduction](#introduction)
2. [Backgrounf](#background)
3. [Data Cleaning and Preparation](#Data-Cleaning-and-Preparation)
4. [Data Modeling](#data-modeling)
5. [A. Sales Analysis](#A-Sales-Analysis)
   * [1. DAX Measures](#1-dax-measures)
   * [2. Key Findings](#2-Key-Findings)
6. [B. Profit Analysis](#B-profit-Analysis)
   * [1. DAX Measures](#1-dax-measures)
   * [2. Key Findings](#2-Key-Findings)
7. [C. Orders Analysis](#C-orders-Analysis)
   * [1. DAX Measures](#1-dax-measures)
   * [2. Key Findings](#2-Key-Findings)
8. [Challenges Faced](#Challenges-Faced)
9. [Recommendations](#recommendations)
10. [Conclusion](#conclusion)

## Introduction
This project analyzes retail sales data from 2014 to 2018 (9,994 transactions) from the United States using a modern data analytics workflow. The goal was to provide a comprehensive analysis of sales, profit, and order trends, identify key business opportunities, and create an interactive dashboard for decision-makers.

The project followed the standard data analysis life cycle:  
1. Data Collection & Understanding
2. Data Cleaning & Preparation
3. Exploratory Data Analysis (EDA)
4. Data Visualization
5. Insights, Recommendations & Reporting

## Background
Retailers often manage vast amounts of sales data across multiple channels and geographies. Without proper analysis, identifying growth opportunities and performance gaps becomes challenging.

The dataset was downloaded from the FP20 Analytics website [Link](https://fp20analytics.com/wp-content/uploads/2024/05/10.-Retail-Supply-Chain-Sales-Analysis_Challenge-10.xlsx) and consisted of:  
* Retail Transactions (2014–2018)
* Sales, Profit, Discounts, Quantity
* Products (Product ID, Product Name, Category, Sub-category)
* Location (Country, City, State, Postal Code, Region
* Customer Details (Customer ID,	Customer Name, Segment)
* Order details (Order ID, Order Date, Ship Date, Ship Mode)
* Calendar Table for time-based analysis.  

The project was implemented using:
* **Power Query**: for data cleaning and transformation
* **Power BI**: Dashboard creation and interactive reporting
* DAX (Data Analysis Expressions): Custom KPI calculations

## Data Cleaning and Preparation
* Checked for duplicates: No duplicate values were found.
* Removed irrelevant fields: Country, since it was only the United States.
* Transformed the Product Name column by shortening text to facilitate display on the y-axis.
* Assigned the correct data type to numeric data fields.
* Assigned the correct data type to the date fields.
* Checked for missing values: none were found.

## Data Modeling
* Ensured the Date table was marked as a date. This was needed for time analysis and using Time Intelligence functions.
* Ensured date fields (Order Date, Ship Date) were consistent and linked with the calendar table.
* Created Fact and Dimension Tables from the Order Table. The image below shows the relationship.

| Figure: Star Schema - Relationship between Fact and Dimension tables |
| :------------: |
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Retail Analysis/Start_Schema_Relationship.png" width=100% height=100% alt="alt text">
<!--   <figcaption>Figure: Star Schema - Relationship between Fact and Dimension tables.</figcaption> -->
</figure>
<!-- <br></br> -->

## A. Sales Analysis
### 1. DAX Measures
```
Sales = SUM('Fact Sales'[Sales])
```
```
Previous Year Sales = CALCULATE([Sales], SAMEPERIODLASTYEAR('Date Table'[Date]))
```
```
YoY% Sales =
  VAR a = DIVIDE([Sales] - [PY Sales], [PY Sales])
  VAR b = FORMAT(a, "#0.0%")           
RETURN
  IF(a > 0, "▲", "▼") & " " & b
```
```
Color Sales = IF([Sales] > [PY Sales], "Green", "#D60000")
```
```
Max Sales =
  VAR Max_Sales = MAXX(ALL('Date Table'[Monthnumber]), [Sales])
RETURN
  IF([Sales] = Max_Sales, Max_Sales, BLANK()) 
```
```
Color Sales Segment =
  VAR max_v = MAXX(ALL('Dim Customers'[Segment]), [Sales])
  VAR color_v = IF([Sales] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Sales Product =
  VAR max_v = MAXX(ALL('Dim Products'[Product Name]), [Sales])
  VAR color_v = IF([Sales] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Sales Product =
  VAR _max = MAXX(ALL('Dim Products'[Product Name]), [Sales])
 RETURN
  IF([Sales] = _max, _max, BLANK())
```
```
Color Sales Category =
  VAR max_v = MAXX(ALL('Dim Products'[Category]), [Sales])
  VAR color_v = IF([Sales] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Sales Sub-Category =
  VAR max_v = MAXX(ALL('Dim Products'[Sub-Category]), [Sales])
  VAR color_v = IF([Sales] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Sales Customers =
  VAR max_v = MAXX(ALL('Dim Customers'[Customer Name]), [Sales])
  VAR color_v = IF([Sales] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Sales Customer =
  VAR _max = MAXX(ALL('Dim Customers'[Customer Name]), [Sales])
RETURN
  IF([Sales] = _max, _max, BLANK())
```

### 2. Key Findings
| Figure: Sales Analysis Dashboard |
| :------------: |
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Retail Analysis/Sales.png" width=100% height=100% alt="alt text">
<!--   <figcaption>Figure: Sales Analysis Dashboard.</figcaption> -->
</figure>
<!-- <br></br> -->

* Overall KPIs:  
  * Sales: $2.3M 
  * Profit: $286.4K 
  * Orders: 9,994
  * Customers: 793 

* Regional Insights  
  * Strongest sales occurred in California ($457,687.6), followed by New York ($310,876.3) and Texas ($170,188.0)

* Product Performance  
  * Top category: Technology ($0.84M, accounting for 37% of total sales)
  * Top Sub-Category: Phones ($0.33M), followed by Chairs ($0.33M) and Tables ($0.22M)
  * Leading Products: Canon imageCLASS 2200 Advanced ($61.6K)

* Customer Insights  
  * High-value customers included Sean Miller ($25.0K) and Tamara Chand ($19.1K).  

* Customer Segments  
  * Consumer segment led with $1.16M (50% of revenue), followed by Corporate and Home Office.

* Year-Over-Year Analysis  
  * Comparing 2015 to 2014 showed a decrease in sales in some areas, leading to a 28% loss.
  * Comparing 2016 to 2015 showed an increase in all areas, giving an overall of 29.5%.
  * Comparing 2017 to 2016 showed an increase in all areas, giving an overall of 20.4%.

 
## B. Profit Analysis
### 1. DAX Measures
```
Profit = SUM('Fact Sales'[Profit])
```
```
Previous Year Profit = CALCULATE([Profit], SAMEPERIODLASTYEAR('Date Table'[Date]))
```
```
YoY% Profit =
  VAR a = DIVIDE([Profit] - [PY Profit], [PY Profit])
  VAR b = FORMAT(a, "#0.0%")           
RETURN
  IF(a > 0, "▲", "▼") & " " & b
```
```
Color Profit = IF([Profit] > [PY Profit], "Green", "#D60000")
```
```
Max Profit =
  VAR Max_Profit = MAXX(ALL('Date Table'[Monthnumber]), [Profit])
RETURN
  IF([Profit] = Max_Profit, Max_Profit, BLANK()) 
```
```
Color Profit Segment =
  VAR max_v = MAXX(ALL('Dim Customers'[Segment]), [Profit])
  VAR color_v = IF([Profit] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Profit Product =
  VAR max_v = MAXX(ALL('Dim Products'[Product Name]), [Profit])
  VAR color_v = IF([Profit] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Profit Product =
  VAR _max = MAXX(ALL('Dim Products'[Product Name]), [Profit])
 RETURN
  IF([Profit] = _max, _max, BLANK())
```
```
Color Profit Category =
  VAR max_v = MAXX(ALL('Dim Products'[Category]), [Profit])
  VAR color_v = IF([Profit] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Profit Sub-Category =
  VAR max_v = MAXX(ALL('Dim Products'[Sub-Category]), [Profit])
  VAR color_v = IF([Profit] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Profit Customers =
  VAR max_v = MAXX(ALL('Dim Customers'[Customer Name]), [Profit])
  VAR color_v = IF([Profit] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Profit Customer =
  VAR _max = MAXX(ALL('Dim Customers'[Customer Name]), [Profit])
RETURN
  IF([Profit] = _max, _max, BLANK())
```


### 2. Key Findings
| Figure: Profit Analysis Dashboard |
| :------------: |
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Retail Analysis/Profit.png" width=100% height=100% alt="alt text">
<!--   <figcaption>Figure: Profit Analysis Dashboard.</figcaption> -->
</figure>
<!-- <br></br> -->

* Overall KPIs:  
  * Sales: $2.3M 
  * Profit: $286.4K 
  * Orders: 9,994
  * Customers: 793 

* Regional Insights  
  * Strongest profit occurred in California ($76.381.4), followed by New York ($74,038.5) and Washington ($33,402.7)

* Product Performance  
  * Top category: Technology ($145K, accounting for 50% of total Profit)
  * Top Sub-Category: Copiers ($56K), followed by Phones ($45K) and Accessories ($42K)
  * Leading Products: Canon imageCLASS 2200 Advanced ($25.2K)

* Customer Insights  
  * High-value customers included Tamara Chand ($9.0K) and Raymonf Buch ($7.0K).  

* Customer Segments  
  * Consumer segment led with $134K (47% of profit), followed by Corporate ($92K, 32%) and Home Office ($60K, 21%).

* Year-Over-Year Analysis  
  * Comparing 2015 to 2014 showed an increase in profit in most areas, leading to an overall percentage of 24.4%.
  * Comparing 2016 to 2015 showed an increase in most areas, leading to an overall percentage of 32.7%.
  * Comparing 2017 to 2016 showed an increase in most areas, leading to an overall percentage of 14.2%.


## C. Orders Analysis
### 1. DAX Measures
```
Orders = SUM('Fact Sales'[Orders])
```
```
Previous Year Orders = CALCULATE([Orders], SAMEPERIODLASTYEAR('Date Table'[Date]))
```
```
YoY% Orders =
  VAR a = DIVIDE([Orders] - [PY Orders], [PY Orders])
  VAR b = FORMAT(a, "#0.0%")           
RETURN
  IF(a > 0, "▲", "▼") & " " & b
```
```
Color Orders = IF([Orders] > [PY Orders], "Green", "#D60000")
```
```
Max Orders =
  VAR Max_Orders = MAXX(ALL('Date Table'[Monthnumber]), [Orders])
RETURN
  IF([Orders] = Max_Orders, Max_Orders, BLANK()) 
```
```
Color Orders Segment =
  VAR max_v = MAXX(ALL('Dim Customers'[Segment]), [Orders])
  VAR color_v = IF([Orders] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Orders Product =
  VAR max_v = MAXX(ALL('Dim Products'[Product Name]), [Orders])
  VAR color_v = IF([Orders] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Orders Product =
  VAR _max = MAXX(ALL('Dim Products'[Product Name]), [Orders])
 RETURN
  IF([Orders] = _max, _max, BLANK())
```
```
Color Orders Category =
  VAR max_v = MAXX(ALL('Dim Products'[Category]), [Orders])
  VAR color_v = IF([Orders] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Orders Sub-Category =
  VAR max_v = MAXX(ALL('Dim Products'[Sub-Category]), [Orders])
  VAR color_v = IF([Orders] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Color Orders Customers =
  VAR max_v = MAXX(ALL('Dim Customers'[Customer Name]), [Orders])
  VAR color_v = IF([Orders] = max_v, "#6B9DFE", "#DDE4F2")
RETURN color_v
```
```
Max Orders Customer =
  VAR _max = MAXX(ALL('Dim Customers'[Customer Name]), [Orders])
RETURN
  IF([Orders] = _max, _max, BLANK())
```


### 2. Key Findings
| Figure: Orders Analysis Dashboard |
| :------------: |
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Retail Analysis/Orders.png" width=100% height=100% alt="alt text">
<!--   <figcaption>Figure: Orders Analysis Dashboard.</figcaption> -->
</figure>
<!-- <br></br> -->

* Overall KPIs:  
  * Sales: $2.3M 
  * Profit: $286.4K 
  * Orders: 9,994
  * Customers: 793 

* Regional Insights  
  * Maximum orders occurred in California (2,001), followed by New York (1,128) and Texas (985)

* Product Performance  
  * Top category: Office Suppliers (6,000, accounting for 60% of total orders)
  * Top Sub-Category: Binders (1,523), followed by Paper (1,370) and Furnishings (957)
  * Leading Products: Staple envelope (48), followed by Easy-staple paper (46)

* Customer Insights  
  * High-value customers included William Brown (37) and John Lee (34).  

* Customer Segments
  * Consumer segment led with $1.16M (50% of revenue), followed by Corporate and Home Office.

* Year-Over-Year Analysis  
  * Comparing 2015 to 2014 showed an increase in orders in most areas, leading to an overall percentage of 5.5%.
  * Comparing 2016 to 2015 showed a significant increase in most areas, leading to an overall percentage of 23.1%.
  * Comparing 2017 to 2016 showed an increase in most areas, leading to an overall percentage of 28.0%.

> [!NOTE]
> The dashboards were designed to provide stakeholders with a clear and actionable view of key performance indicators (KPIs), enabling them to monitor growth, identify trends, and make data-driven decisions in real time.

## Challenges Faced
While building the dashboards, I faced so many challenges, such as:  
- Creating a bar chart that highlights the maximum bar with a different color, and having the y-axis label and data labels above the bar. So, I ended up creating a simple bar chart highlighting the bar with the maximum value in a different color.

- Making the length of the previous year bar pass that of the current year. I added the previous year to the column and bar charts using Error Bar. However, I could not increase the Previous year bar to be longer than the current year bar, since the maximum length is 10.

- Using the integrated bookmark navigator in Power BI. I did not want to create three pages of a dashboard. So, I decided to use bookmarks to switch from one dashboard to another. It took me time to create the bookmark navigation from scratch for it to work properly the way I wanted, but I eventually found my way around it.

- Creating the map chart with bubbles. The Retail Sales dataset I used did not contain the latitude and longitude columns. As a result, I could not create a map chart with bubbles. So, I settled for the filled map chart.

## Recommendations
Based on the analysis, the following strategies are recommended:
* Expand Technology Product Line  
  * Focus on increasing the availability and marketing of high-performing technology items.
    
* Target Underperforming Regions  
  * Deploy regional campaigns to boost sales in low-revenue states.
    
* Strengthen B2C Marketing Efforts  
  * Consumer segment shows the most potential; allocate more marketing resources here.

* Loyalty Program for Top Customers  
  * Incentivize repeat purchases through personalized offers and loyalty rewards.

## Conclusions
This project provided a clear picture of retail sales performance over five years. Key insights highlighted the dominance of technology products, the importance of consumer-focused sales, and areas where discounts eroded profitability.

By acting on the recommendations:  
* Profit margins can be improved by 5–8% annually.
* Underperforming regions could generate up to $250K in additional sales.
* Retention-focused strategies may increase customer lifetime value by 12–15%.



