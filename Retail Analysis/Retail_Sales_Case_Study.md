# Retail Sales Case Study
----

## Introduction
This project analyzes retail sales data from 2014 to 2018 (9,994 transactions) from the United States using a modern data analytics workflow. The goal was to provide a comprehensive analysis of sales, profit, and order trends, identify key business opportunities, and 
create an interactive dashboard for decision-makers.

The project followed the standard data analysis life cycle:  
1. Data Collection & Understanding
2. Data Cleaning & Preparation
3. Exploratory Data Analysis (EDA)
4. Data Visualization
5. Insights, Recommendations & Reporting

## Background
Retailers often manage vast amounts of sales data across multiple channels and geographies. Without proper analysis, identifying growth opportunities and performance gaps becomes challenging.

The dataset consisted of:  
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

## Data Cleaning & Preparation
* Checked for duplicates: No duplicate values were found.
* Removed irrelevant fields: Country since it was only United States.
* Transformed the Product Name column by shortening text to facilitate display on the y-axis.
* Assigned correct data type to numeric data fields.
* Assigned correct data type to the date fields.
* Checked for missing values: none were found.

## Data Modeling
* Ensured the Date table was marked as a date. This was needed for time analysis and using Time Intelligence functions.
* Ensured date fields (Order Date, Ship Date) were consistent and linked with the calendar table.
* Created Fact and Dimension Tables from the Order Table. The image below shows the relationship.
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Retail Analysis/Start_Schema_Relationship.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Star Schema - Relationship between Fact and Dimension tables.</figcaption>
</figure>
<br></br>

## Sales Analysis
### DAX Measures
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

### Key Findings
* Overall KPIs: Comparing year `2016` to `2015`
  * Sales: $609.2K (+29.5% vs PY)
  * Profit: $81.8K (+32.7% vs PY)
  * Orders: 2,587 (+23.1% vs PY)
  * Customers: 638 (+11.3% vs PY)  

* Regional Insights  
  * Strongest sales occurred in California ($ 131,551.9), followed by New York ($71,844.1) and Texas ($41,686.2)

* Product Performance  
  * Top category: Technology ($0.23M, accounting for 38% of total sales)
  * Top Sub-Category: Chairs ($84K), forllowed by Phones ($79K) and Tables ($61K)
  * Leading Products: Canon imageCLASS 2200 Advanced ($25.9K) and GBC Ibimaster 500 Manual ($12.9K).
  * Leading segment: Consumer ($0.30M, 50% of revenue)  

* Customer Insights  
  * High-value customers included Tamara Chand ($18.3K) and Christopher Conant ($11.9K).  

* Customer Segments
  * Consumer segment led with $0.30M in sales (+114%), followed by Corporate and Home Office.

* Year-Over-Year Analysis
  * Comparing 2015 to 2014 showed a decrease in sales in some areas, leading to 28% lost.
  * Comparing 2016 to 2015 showed an increase in all areas, giving an overall of 29.5%.
  * Comparing 2016 to 2015 showed an increase in all areas, giving an overall of 20.4%.



## Recommendations
Based on the analysis, the following strategies are recommended:
* Expand Technology Product Line  
  * Focus on increasing availability and marketing of high-performing technology items.
    
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

The interactive Power BI dashboard serves as a live decision-making tool, enabling managers to track KPIs and adapt strategies in real time.




The dashboard was designed to provide business stakeholders with a clear and actionable view of key performance 
indicators (KPIs), enabling them to monitor growth, identify trends, and make data-driven decisions.
