# Project: Netflix Content Analysis

## Table of Contents  
1. [Introduction](#introduction)
   * [Business Overview or Problem](#business-overview-or-problem)
   * [Rationale for the Project](#rationale-for-the-project)
2. [Aim of the Project](#aim-of-the-project)
3. [Data Description](#data-description)
4. [Tech Stack](#tech-stack)
5. [Project Scope](#project-scope)
6. [Data Interpretation](#data-interpretation)
7. [Recommendations](#recommendations)

## Introduction 
This project provides a profound learning experience in data analytics by utilizing real-world data from Netflix to assess content from 2008 to 2021. I constructed a dynamic and interactive dashboard through Power BI that was designed for sophisticated reporting. This task involves leveraging intermediate and advanced Power BI functions to interpret complex data sets effectively. Completing this project enriched my analytical skills, enhancing my ability to navigate and make sense of intricate data landscapes. The project was completed during my internship at CognoRise Infotech.

### Business Overview or Problem
Netflix has been providing content to its customers. It has over 8000 movies or TV shows available on its platform, and as of mid-2021, they have over 200M Subscribers globally. The key obstacles the company encounters include:
1. **Limited Data Analysis**: The lack of data analysis tools hinders the company's ability to gain insights into customer preferences and country trends.
2. **Resource Allocation**: Netflix struggles to allocate resources efficiently in each country, leading to customer dissatisfaction.

### Rationale for the Project
1. **Basic Data Insights**: Enable the company to obtain fundamental data insights, including watched trends, product performance, and customer preferences.
2. **Cost-Efficiency**: Provide a cost-efficient solution that aligns with the company's budget constraints while delivering essential data analysis capabilities.
3. **Streamlined Resource Allocation**: Improve resource allocation by leveraging data-driven decisions to maximize customer satisfaction.

The key task to conduct in this analysis is to understand what content is available in different countries and provide recommendations regarding the types of content that are the most watched. Some interesting task ideas are:
1.	Understanding what content is available in different countries
2.	Identifying similar content by matching text-based features
3.	Network analysis of Actors / Directors and find interesting insights
4.	Does Netflix focus more on TV Shows than movies in recent years?
 
## Aim of the Project
The project aims to achieve the following specific objectives:
1.	Implement basic data analysis techniques to gain insights into watched trends, product performance, and customer preferences.
2.	Create user-friendly dashboards from Netflix data and derive insights.
3.	Carry out basic data analysis and dashboard utilization to enhance decision-making capabilities.
 
## Data Description
This dataset consists of listings of all the movies and TV shows available on Netflix from 2008 to 2021, along with details such as cast, directors, ratings, release year, duration, etc. The dataset contains 10 columns and 8791 rows described as follows:
*	*ShowID*: The ID number of the show made of the letter “s” and a number.
*	*Type*: The type of content such as “Movie” or “TV Show”
*	*Title*: The title of the “Movie” or “TV Show”
*	*Director*: Director of the content “Movie” or “TV Show”
*	*Country*: The country where the “Movie” or “TV Show” is provided
*	*DateAdded*: the date the Movie or TV Show was added to the content
*	*ReleaseYear*: The year the Movie or TV Show was released
*	*Rating*: The rating of the Movie or TV Show from customers 
*	*Duration*: The duration of the Movie or TV Show
*	*ListedIn*: The category in which the Movie or TV Show is listed

## Tech Stack
The analysis tool for this project is basic and focused on data analysis using Microsoft Power BI. I utilize Power BI's built-in features like Visualizations, and filters to analyze content data.

## Project Scope
* **Data Gathering and Integration**
  1. Download Netflix content data from Kaggle.
  2. Store the data in a secure folder for further steps.

* **Data Cleaning**: To clean the data, I will
  1. Check Nulls across all columns
  2. Remove duplicates 
  3. Populate missing rows where necessary
  4. Delete unneeded columns
  5. Split columns appropriately where necessary

* **Data Analysis In Power BI**
  1. Utilize Power BI's built-in features to analyze content data.
  2. Identify customers’ preferences.
  3. Identify trends by visualizing data through simple charts and graphs.
 
* **Dashboard Development**
  1. Create an interactive Power BI dashboard to provide an overview of content.
  2. Include key metrics and charts to monitor watched trends by type, country, and content category.

* **Data Analysis and Visualization**
The analysis was performed in Power BI. To do so,  
*	I used tables to create visuals. 
*	I created several charts such as Bar charts, Line charts, a pie chart, a Map, and Stacked Bar charts.
*	After creating all the charts, I combined them in a dashboard as shown in Figure 1.

<figure>
  <img src="https://github.com/Songonge/CognoRise-Infotech/blob/main/Netflix Project/Netflix Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Netflix Content Analysis Dashboard</figcaption>
</figure>
<br/><br/>

## Data Interpretation
1. **Content Type Distribution**: Movies dominate Netflix's library, comprising nearly 70% of the content, while TV shows make up the remaining 30%. This indicates a significant emphasis on movie content.
2. **Content Addition Over the Years**: The amount of content added has increased significantly from 2015 to 2020, peaking in 2019. There was a slight decline after 2020, potentially due to market saturation or strategic shifts.
3. **Top Countries by Content Type**: The United States is the leading country producing Netflix content, followed by India and the United Kingdom. The U.S. primarily produces movies, while India has a more balanced distribution between TV shows and movies.
4. **Top Directors by Content Type**: Rajiv Chilaka, known for producing movies, leads the list of directors, followed closely by Raúl Campos & Jan Suter, who also predominantly direct movies. TV shows, however, are less represented among top directors.
5. **Top Most Watched Content Categories**: Dramas and international movies are the most-watched categories, closely followed by documentaries and stand-up comedy. The diversity in popular genres suggests a wide range of viewer interests.
6. **Content Release Years**: Most content was released between 2017 and 2020, with 2018 seeing the highest number of releases. The decline in 2021 suggests a reduction in new releases, possibly due to the COVID-19 pandemic.
7. **Content Ratings**: TV-MA (mature audience) content dominates, with TV-14 following. This suggests a significant portion of Netflix's audience prefers mature content.

## Recommendations
1. **Diversify Content Types**: Since movies are predominant, Netflix could consider expanding its TV show offerings to attract a more diverse audience, particularly in countries like India, where TV shows have a significant market share.
2. **Leverage Top Categories**: Since dramas and documentaries are popular, Netflix should invest in producing high-quality content in these categories. Additionally, exploring niche categories like stand-up comedy could further attract and retain subscribers.
3.	Strategic Content Release: The decline in new content after 2020 suggests the need to evaluate current content strategies. Netflix should focus on maintaining a steady flow of releases, even if production is impacted by external factors like pandemics.
4.	Expand Global Presence: With most content originating from the U.S., expanding production in other regions, especially in Asia and Europe, could help cater to local preferences and increase global viewership.
5.	Targeted Marketing: Given the dominance of TV-MA ratings, Netflix could tailor its marketing efforts to highlight mature content while ensuring parental controls and family-friendly content are also emphasized to cater to diverse audiences.
6.	Capitalize on Most Watched Categories: Netflix should consider creating more original content in its top-viewed categories. For example, focusing on cross-genre content that blends drama, international films, and documentaries could drive engagement.

<br/>
   
**Thank you for taking the time to read this report!**

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge)
