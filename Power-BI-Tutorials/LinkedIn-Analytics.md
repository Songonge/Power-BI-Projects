# Creating a Dynamic LinkedIn Analytics Dashboard in Power BI 

## Table of Contents
1. [Project Overview](#Project-Overview)
2. [What You’ll Need](#What-Youll-Need)
3. [The Dataset](#The-Dataset)
4. [Step 1: Preparing the Data](#Step-1-Preparing-the-Data)
5. [Step 2: Creating Other Tables](#Step-2-Creating-Other-Tables)
6. [Step 3: Creating DAX Measures](#Step-3-Creating-DAX-Measures)
   * [Measures For Impressions](#Measures-For-Impressions)
   * [Measures For Followers](#Measures-For-Followers)
   * [Measures Engagements](#Measures-Engagements)
   * [Measure to Highlight the Selected Month](#Measure-to-Highlight-the-Selected-Month)
7. [Step 4: Creating Field Parameters](#Step-4-Creating-Field-Parameters)
8. [Step 5: Design the Dashboard](#Step-5-Design-the-Dashboard)
9. [What you Should do Next](#What-you-Should-do-Next)

## Project Overview
This tutorial walks you through how I built a Power BI dashboard that analyzes my LinkedIn Analytics over six months (Jan–Jun 2025). The dashboard uses field parameters and disconnected tables to create interactive slicers for metrics (Impressions, Followers, Engagements) and 
months. The good news is that you can replicate the same for any period of your analytics.

By the end, you will learn:  
1. How to use field parameters for dynamic measures
2. How to create a disconnected table slicer
3. How to design a clean, modern UI for analytics


## What You’ll Need
* Power BI Desktop (latest version)
* LinkedIn Analytics dataset
* Basic knowledge of DAX

## The Dataset
To get the dataset, follow the steps below:  
1. Go to your LinkedIn profile and click on `Show all analytics`.
2. Select the period interval using the drop-down arrow next to `Past 7 days`.
3. Click on **Export**.

This downloads an Excel workbook containing the following sheets:  
* DISCOVERY
* ENGAGEMENT
* TOP POSTS
* FOLLOWERS
* DEMOGRAPHICS

To build the dashboard, you will need the following data:  
* Engagement: This contains 3 columns  
  * Date 
  * Impressions
  * Engagements  

* Followers: This contains 2 columns  
  * Date 
  * New followers


## Step 1: Preparing the Data
1. Launch Power BI.
2. Import your LinkedIn Analytics data into Power Query using the `Get Data` feature.
3. Clean your data and ensure date formats are correct.
4. Then, close and load it to Power BI.

## Step 2: Creating Other Tables
1. Create a Date Table  
This is needed for Time Intelligence Functions. 
```
Date Table = ADDCOLUMNS(
    CALENDARAUTO(),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "MMM"),
    "MonthNo", MONTH([Date])
)
```
When you are done, **Mark it as a Date**.

2. Create a disconnected table from the Date Table
```
Dist Table = ADDCOLUMNS(
    SUMMARIZE('Date Table',
        'Date Table'[Month],
        'Date Table'[MonthNo],
        'Date Table'[Year]
    ),
    "max Date", CALCULATE(MAX('Date Table'[Date]))
```

> [!NOTE]
> Build relationships between the Date Table and the two other tables.


## Step 3: Creating DAX Measures
1. Under the Home Tab, click on `Enter data`. Then give it a name. This is where you will host all your measures.
2. Create all the measures needed

### Measures For Impressions:
* Total Impressions
```
Impressions = SUM('Engagement'[Impressions])
```

* Previous Month Impression
```
PM Impressions = IF(SELECTEDVALUE('Date Table'[Month]) = BLANK(), BLANK(),CALCULATE([Impressions], PREVIOUSMONTH('Date Table'[Date])))
```

* Month on Month Impression
```
MoM% Impressions = 
VAR a = DIVIDE([Impressions], [PM Impressions]) - 1
VAR b = FORMAT(a, "#0.0%")
RETURN IF([PM Impressions] = BLANK(), BLANK(), IF(a > 0, "↑","↓") & " " & b)
```

* Color coding for the Month-on-Month Impression
```
MoM% Color Impressions = IF([Impressions] < [PM Impressions], "#8d0801", "Green")
```

### Measures For Followers
* Total Followers
```
Followers = SUM('Engagement'[Followers])
```

* Previous Month Followers
```
PM Followers = IF(SELECTEDVALUE('Date Table'[Month]) = BLANK(), BLANK(),CALCULATE([Followers], PREVIOUSMONTH('Date Table'[Date])))
```

* Month on Month Followers
```
MoM% Followers = 
VAR a = DIVIDE([Followers], [PM Imp]) - 1
VAR b = FORMAT(a, "#0.0%")
RETURN IF([PM Followers] = BLANK(), BLANK(), IF(a > 0, "↑","↓") & " " & b)
```

* Color coding for the Month-on-Month Followers
```
MoM% Color Followers = IF([Followers] < [PM Followers], "#8d0801", "Green")
```

### Measures Engagements
* Total Engagements
```
Engagements = SUM('Engagement'[Engagements])
```

* Previous Month Engagements
```
PM Engagements = IF(SELECTEDVALUE('Date Table'[Month]) = BLANK(), BLANK(),CALCULATE([Engagements], PREVIOUSMONTH('Date Table'[Date])))
```

* Month-on-Month Engagements
```
MoM% Engagements = 
VAR a = DIVIDE([Engagements], [PM Imp]) - 1
VAR b = FORMAT(a, "#0.0%")
RETURN IF([PM Engagements] = BLANK(), BLANK(), IF(a > 0, "↑","↓") & " " & b)
```

* Color coding for the Month-on-Month Engagements
```
MoM% Color Engagements = IF([Engagements] < [PM Engagements], "#8d0801", "Green")
```

### Measure to Highlight the Selected Month
This measure is needed so that when you select a month from the slicer, it highlights the column on the chart.
```
color = IF(ISFILTERED('d') && 
VALUES('Date Table'[Month]) IN VALUES('d'[Month]), "#3a86ff", "#cae9ff")
```


## Step 4: Creating Field Parameters
To create field parameters:  
1. Go to Modeling > New Parameter > Fields
2. Add these measures:  
   * Impressions
   * Followers
   * Engagements  
3. Rename the parameter table to Metrics Parameter.
4. This creates a slicer that allows switching between metrics.


## Step 5: Design the Dashboard
1. Create a clustered column chart using:  
   * The Month field from the Date Table
   * The Parameter Field  

2. Add slicers to the dashboard  
   * Add the **Month** slicer from the **Date Table**.
   * Add another **Month** slicer from the **Dist Table**. 
   * Make it a Single selection for each.
   * Synchronize the two slicers.
   * Hide the slicer from the **Dist Table**.
   * Customize the color on the Clustered column chart using the color measure you created.

> [!IMPORTANT]
> You should remove the interaction between the **Month** slicer from the **Date Table** and the Clustered column chart.

3. Create A Card Visual
   * Use the Card (new) visual
   * Add the field parameter in the Data section

4. Add the **MoM** measures on the Reference labels for each metric from the field parameter.
5. Format this to appear next to the Callout value.
6. Add the color coding to each **MoM** value.


**Yay! We are done!**
Here is the Dashboard itself.
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Power-BI-Tutorials/LinkedIn_6_Months_Analytics.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: 6-Month LinkedIn Analytics.</figcaption>
</figure>
<br/><br/>


## What you Should do Next
* Share your design
* Tag me in your post. Here is the link to my LinkedIn profile: [Link](https://www.linkedin.com/in/edwigesongong/)
* Have any questions? Send me a message using any means from my GitHub profile.


## Conclusion
This project gives details on how I created a dashboard showcasing my LinkedIn Analytics for the past six months. What is amazing about this is that the same analysis can be done using a dataset from a period larger than that. 
