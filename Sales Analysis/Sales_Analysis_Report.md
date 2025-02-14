# Project: Sales Analysis in some Cities in the United States

## Table of Contents  
1. [Introduction](#introduction)
2. [Project Aim](#project-aim)
3. [Project Description](#project-description)
4. [Data Acquisition and Preparation](#data-acquisition-and-preparation)
5. [Data Cleaning and Transformation](#data-cleaning-and-transformation)
6. [Data Analysis and Visualization](#data-analysis-and-visualization)
7. [Interpretation of Data](#interpretation-of-data)
8. [Recommendations](#recommendations)

## Introduction
This project about Sales Analysis is one of the projects offered by MeriSKILL as part of an internship. The project is focused on data analytics and is carefully planned to reveal patterns and insights hidden in complex datasets. I will be using Power BI to facilitate the extraction of critical insights.

## Project Aim
Deep dive into sales data to extract valuable insights to enhance strategic decision-making. This will involve analyzing sales data to identify trends, top-selling products, and revenue metrics for business decision-making.    

## Project Description
In this project, I will dive into a large sales dataset to extract valuable insights. To properly convey my findings, I will calculate revenue indicators like total sales and profit margins, analyze sales patterns over time, determine the best-selling products, and produce visualizations. This project demonstrates my capacity to work with and extract meaning from huge datasets, allowing me to provide data-driven recommendations for improving sales strategies. 

The following bullets list the insights I will derive through my data analysis process:
*	What are the best-selling products?  
*	What are the top five cities with the highest sales in 2019?
*	How much profit was made in 2019?
*	What are the top five products based on sales?
*	Which day of the week and which month have major sales?
  
Here is what I did:

## Data Acquisition and Preparation
MeriSKILL provided data. I downloaded the dataset from *Google Drive*. Then, I uploaded it in Power BI using the *Get Data* option. This dataset was unclean and had 10 columns in total. The data were recorded for the year *2019*.

## Data Cleaning and Transformation
The first row of the data was used as headers using the option *Use First Row as Headers* under the Home tab. Then, using the *Transform* tab, I selected *Detect Data Type* to automatically identify the data type of each column and convert them where needed.
* Next, I split the fourth column named *Order Date* into date and time stamps. I
  * selected the column named *Order Date*. 
  * Then, I chose the *Split Column* option and selected the space as the delimiter.
  * Next, I selected *Each occurrence of the delimiter*. Then I pressed OK.

*	To proceed, I created a column named *Day* to extract days of the week from the date column.
*	I also performed some calculations by using the New measure option:
  * The total cost using the formula: `Total cost = SUM('Sales Data'[Price Each])`
  * The profit margin using the formula: `Profit Margin = ([Total Sales]-[Total Cost])/[Total Sales])*100`
  * The total sales using the formula: `Total Sales = SUM('Sales Data'[Sales])`
    
## Data Analysis and Visualization
In Power BI, I used Visualizations to create a dashboard as shown in the figure below. 

<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Sales%20Analysis/Sales%20Analysis%20Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Sales Analysis Dashboard</figcaption>
</figure>
<br/><br/>

I used a
*	Line chart to represent sales trend over the year, 
*	Stacked column chart to display weekly sales for each day, 
*	Treemap to show the best-selling products, 
*	Stacked bar chart to identify the top 5 best-selling products, 
*	Map to show the top 5 cities by sales, 
*	Cards to display the sum of all sales, the total sales quantity, and the profit margin. The "Format" option for the visual was used to adjust the callout value to change the display unit of the quantity ordered as desired.
*	My charts were assembled and made interactive through the use of Slicers to display cities, months, days, and products.

## Interpretation of Data
The following insights were derived from the data analysis:
*	The top five products by sales count were the iPhone, 27in 4K Gaming Monitor, Google Phone, MacBook Pro Laptop, and ThinkPad Laptop.  
*	The top five best-selling products were  AAA Batteries (4-pack), AA Batteries (4-pack), USB-C Charging Cable, Lightning Charging Cable, and Wired Headphones.
*	The day of most sales was Tuesday and the minimum sales was on Thursday.
*	 December was the month with major sales. On the contrary, January was the month with lower sales followed by February. 
*	The top five cities with the most sales were Los Angeles, San Francisco, Atlanta, New York City, and Boston.

## Recommendations
Based on the insights from the sales analysis, here are several recommendations to enhance sales strategies and optimize performance:
*	Ensure ample inventory of the top five products by sales count (iPhone, 27in 4K Gaming Monitor, Google Phone, MacBook Pro Laptop, and ThinkPad Laptop) and best-selling products (AAA Batteries, AA Batteries, USB-C Charging Cable, Lightning Charging Cable, and Wired Headphones) to meet high demand and prevent stockouts. 
*	Develop marketing campaigns and promotions focused on these top products to further boost sales and capitalize on their popularity.
*	Implement targeted promotions and discounts on Thursdays to increase sales on this typically slow day. Consider limited-time offers or flash sales to drive urgency. On the other hand, enhance marketing efforts on Tuesdays with special deals, bundles, or loyalty rewards to sustain and potentially increase high sales volumes on this day. 
*	Plan extensive marketing campaigns and stock inventory well in advance for December, the month with major sales. Consider holiday-themed promotions, gift bundles, and early bird specials to maximize revenue during this peak season. 
*	Develop strategies to maintain sales momentum during off-peak months, such as introducing new product lines, offering exclusive deals, or launching loyalty programs. 
*	Concentrate marketing efforts and allocate resources to the top five cities with the most sales (Los Angeles, San Francisco, Atlanta, New York City, and Boston). Tailor advertising and promotional strategies to the preferences and behaviors of customers in these regions. In addition, analyze factors contributing to high sales in these cities and replicate successful strategies in other potential high-growth areas to expand market reach.
*	Regularly collect and analyze customer feedback to identify pain points and areas for improvement. Use these insights to refine product offerings, customer service, and overall sales strategies.  
  
By implementing these recommendations, the organization can optimize its sales strategies, improve inventory management, enhance customer experience, and maximize revenue across different periods and locations. 


<br/><br/>

**Thank you for taking the time to read this report!** 

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge) Powered by [MeriSKILL](https://meriskill.in/)


