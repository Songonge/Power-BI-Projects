# Project: Flight Delays and Cancellations Analysis

## Table of Contents  
1. [Introduction](#introduction)
   * [Business Overview or Problem](#business-overview-or-problem)
   * [Rationale for the Project](#rationale-for-the-project)
2. [Aim of the Project](#aim-of-the-project)
3. [Tech Stack](#tech-stack)
4. [Step 1: Loading and preparing data in Power BI](#step-1-loading-and-preparing-data-in-power-bi)
   * [Data Gathering and Integration](#data-gathering-and-integration)
   * [Data Description and Exploration](#data-description-and-exploration)
   * [Data Cleaning and Transformation](#data-cleaning-and-transformation)
5. [Step 2: Building a Relational Model Between Tables](#step-2-building-a-relational-model-between-tables)
6. [Step 3: Adding Data Analysis Expression (DAX) Measures to the tables](#step-3-adding-data-analysis-expression-DAX-measures-to-the-tables)
7. [Step 4: Designing an Interactive Dashboard](#step-4-designing-an-interactive-dashboard)
8. [Data Interpretation](#data-interpretation)
9. [Recommendations](#recommendations)


## Introduction
Every day, data is generated about flights including airport names, departure and arrival airports, flight status, etc. It is interesting to analyze the data generated through those processes to understand how customers can be better satisfied.  
This project focuses on analyzing flight status based on data collected from different airports during the year 2015. The project was completed during my internship at CognoRise Infotech.

### Business Overview or Problem
This project leverages data analytics to analyze flight status from different airports. It provides actionable insights to better understand flight delays and cancellations and highlights the most common reasons for flight cancellations. The goal is to better understand flight status and improve customer experience in different airports.
The key obstacles involving technical and regulatory challenges could include:
1. **Data Accuracy and Availability**: Flight data may be incomplete, inaccurate, or delayed, making it difficult to perform real-time or historical analysis effectively.
2. **Data Integration**: Integrating data from multiple sources, such as airlines, airports, and weather services, can be challenging due to differing data formats and standards.
3. **External Factors**: Factors like sudden weather changes or security issues are unpredictable and can complicate the analysis or forecasting of delays and cancellations.
4. **Seasonal and Geographical Variations**: Flight delays and cancellations can vary greatly depending on location and time of year, making it difficult to generalize insights across different regions or seasons.

### Rationale for the Project
The rationale behind the flight delays and cancellations analysis project is to provide operational and customer-focused perspectives to enhance data-driven decisions for better customer satisfaction.
Here is a list of rationales for this project:
1. **Improve Operational Efficiency**: Identifying patterns in delays and cancellations will help airlines and airports optimize flight schedules and reduce downtime.
2. **Enhance Customer Satisfaction**: By minimizing delays and proactively managing cancellations, airlines can improve customer experience and retain loyalty.
3. **Cost Reduction**: Analyzing the root causes of delays allows airlines to reduce fuel, staffing, and compensation costs associated with prolonged delays or unexpected cancellations.
4. **Predictive Capabilities**: Leveraging historical data for predictive analytics can help airlines anticipate delays and cancellations, allowing for proactive communication with passengers and resource allocation.
5. **Weather Impact Analysis**: Identifying the impact of weather conditions on flight schedules allows airlines and airports to take preventive measures, reducing weather-related disruptions.
6. **Competitiveness**: Airlines that minimize delays and cancellations will gain a competitive edge by offering more reliable services compared to competitors.

## Aim of the Project
This project aims to analyze flight delays and cancellations data to provide actionable insights for airlines, airports, and travel agencies. Using data analytics and Power BI features, the project identifies patterns and causes of delays, such as weather conditions, 
airline-specific issues, or airport congestion. The analysis conducted in this project could help stakeholders optimize flight schedules, improve customer satisfaction, and reduce operational costs by minimizing delays. Additionally, predictive analytics could help 
airlines anticipate potential delays or cancellations, enabling proactive communication with passengers and resource allocation to ensure smoother operations.
The key tasks in this project are: 
1. Providing a comprehensive flight status analysis by visualizing flight status such as On-Time, Delayed, and Canceled.
2. Determining key factors driving delays and cancellations.
3. Visualizing key metrics such as average delay times and the most common causes of cancellations.
4. Developing an interactive dashboard using Power BI to visualize delay trends, predict upcoming issues, and monitor key performance indicators.
5. Providing recommendations for better resource allocation and for avoiding flight delays and cancellations.

## Tech Stack
The analysis tool for this project focused on data analysis using Microsoft Power BI. Power Query was used to transform data. Then, Power BI's built-in features were used to analyze data and design an interactive dashboard. The project was completed in four steps.
 
## Step 1: Loading and preparing data in Power BI

### Data Gathering and Integration
  1. Download Flight delays and cancellations data from Kaggle.
  2. Store the data in a secure folder for further steps.

### Data Description and Exploration
The dataset used in this project was downloaded from Kaggle. It was made of three tables. 
1. **airlines.csv**: This table contains two columns and 15 rows defined as follows: 
   * *IATA_CODE*: Identification of each airline
   * *AIRLINE*: Name of the airline
2. **airports.csv**: This table contains 7 columns and 323 rows defined as follows: 
   * *IATA_CODE*: The Identification of each airline
   * *AIRPORT*: Airport's name
   * *CITY*: City name of the airport
   * *STATE*: Name of the state of the airport, provided as an abbreviation
   * *COUNTRY*: Country Name of the Airport
   * *LATTITUDE*: Latitude of the Airport
   * *LONGITUDE*: Longitude of the Airport
3. **flights.csv**: This table contains 31 columns and more than 6 million rows. 
   * *YEAR*: Year of the Flight Trip
   * *MONTH*: Month of the Flight Trip
   * *DAY*: Day of the Flight Trip
   * *DAY_OF_WEEK*: Week's day of the Flight Trip
   * *AIRLINE*: Airline Identifier
   * *FLIGHT_NUMBER*: Flight Identifier number
   * *TAIL_NUMBER*: Aircraft Identifier
   * *ORIGIN_AIRPORT*: Starting Airport
   * *DESTINATION_AIRPORT*: Destination Airport
   * *SCHEDULE_DEPARTURE*: Planned Departure Time
   * *DEPARTURE_TIME*: Obtained from WHEELS_OFF - TAXI_OUT
   * *DEPARTURE_DELAY*: Total Delay on Departure
   * *TAXI_OUT*: The time duration elapsed between departure from the origin airport gate and wheels off
   * *WHEELS_OFF*: The time point that the aircraft's wheels leave the ground
   * *SCHEDULED_TIME*: Planned time amount needed for the flight trip
   * *ELAPSED_TIME*: Obtained from AIR_TIME+TAXI_IN+TAXI_OUT
   * *AIR_TIME*: The time duration between wheels_off and wheels_on time
   * *DISTANCE*: Distance between two airports
   * *WHEELS_ON*: The time point that the aircraft's wheels touch on the ground
   * *TAXI_IN* The time duration elapsed between wheels-on and gate arrival at the destination airport
   * *SCHEDULED_ARRIVAL*: Planned arrival time
   * *ARRIVAL_TIME*: WHEELS_ON+TAXI_IN
   * *ARRIVAL_DELAY*: ARRIVAL_TIME-SCHEDULED_ARRIVAL
   * *DIVERTED*: Aircraft landed at an airport that was out of schedule
   * *CANCELED*: Flight Cancelled (1 = cancelled)
   * *CANCELLATION_REASON*: Reason for Cancellation of flight: A - Airline/Carrier; B - Weather; C - National Air System; D - Security
   * *AIR_SYSTEM_DELAY*: Delay caused by air system
   * *SECURITY_DELAY*: Delay caused by security
   * *AIRLINE_DELAY*: Delay caused by the airline
   * *LATE_AIRCRAFT_DELAY*: Delay caused by aircraft
   * *WEATHER_DELAY*: Delay caused by weather

### Data Cleaning and Transformation
The data was loaded in Power BI using the Get Data feature. Then, using Power Query the data was cleaned and transformed. To complete this process, I
1. For the airlines' table, the first row was promoted as Header
2. For the airports' table, the data was left as is
3. For the flights' table:
   * 22 columns were removed
   * A conditional column named *STATUS* was created using the following description:
     * `If CANCELED equals 1 Then Canceled`
     * `Else If DEPARURE_DALAY is greater than 0 Then Delayed`
     * `Else On-Time`
   * The column named *CANCELLATION_REASON* was used to create another table. This table, named *cancellation_codes* was designed with two columns and 5 columns including headers and defined as follows:
     * *CANCELLATION_REASON*: Reason the flight was canceled
     * *CANCELLATION_DESCRIPTION*: Description for flight cancellation
   * Overall, the flights' table was transformed into 10 columns.

## Step 2: Building a Relational Model Between Tables
To complete this step, 1 to many relationships were created between the four tables.
* The IATA_CODE column from the airlines' table connected to the AIRLINE column in the flights' table
* The CANCELLATION_REASON column from the airlines cancellation_codes table to the CANCELLATION_REASON column in the flights table
* The IATA_CODE column from the airports table connected to the ORIGIN_AIRPORT column in the flights table
The following figure shows the relationships created.
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Flight%20Delays%20and%20Cancelation%20Analysis/Relationship.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Relationships between tables</figcaption>
</figure>
<br/><br/>

## Step 3: Adding Data Analysis Expression (DAX) Measures to the tables
DAX measures were used to define custom calculations. This was to enhance my data model and create new metrics to support my analysis.  The following new measures were calculated.
1. **Total Flights**: The total amount of flights defined as
`Total Flights = COUNTROWS(flights)`
2. The Total Amount of flights given a status
   * **Canceled Flights**: The total amount of canceled flights defined as
`Canceled Flights = CALCULATE([Total Flights], flights[STATUS] = "Canceled")`
   * **Delayed Flights**: The total amount of delayed flights defined as
`Delayed Flights = CALCULATE([Total Flights], flights[STATUS] = "Delayed")`
   * **On-Time Flights**: The total amount of On-Time flights defined as
`On-Time Flights = CALCULATE([Total Flights], flights[STATUS] = "On-Time")`
3. The percentage of flights given a status
   * **% Canceled**: The percentage of canceled flights defined as
`Canceled Flights = DIVIDE([Canceled Flights], [Total Flights], "-")`
   * **% Delayed**: The percentage of delayed flights defined as
`Delayed Flights = DIVIDE([Delayed Flights], [Total Flights], "-")`
   * **% On-Time**: The percentage of On-Time flights defined as
`On-Time Flights = DIVIDE([On-Time Flights], [Total Flights], "-")`
> [!NOTE]
> The dash (-) is put here so that if there is a division by 0, the output should be a dash instead of an Error.

## Step 4: Designing an Interactive Dashboard
This step involves creating visuals and charts in Power BI to show a comprehensive overview of the flights' data.
1. I created several charts such as
   * Bar charts to show total flights by city, delayed and canceled flights by airline
   * A Line chart to show both canceled and delayed flights by airport
   * Line charts to show total flights by month for On-Time, Delayed, and Canceled
   * A donut chart to show canceled flights for different cancellation reasons
   * Column charts to show total flights by the percentage of Ontime by day; delayed flights by the percentage of delayed by day, and canceled flights by the percentage of canceled by day.
   * A Stacked Bar chart to show the percentage of flights by status.
2. Designed a dashboard by combining the charts all together. The dashboard is shown in the following figure.

<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Flight%20Delays%20and%20Cancelation%20Analysis/Flights%20Analysis%20Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure: Flight Delays and Cancellations Analysis Dashboard</figcaption>
</figure>
<br/><br/>

## Data Interpretation
1. **Delayed Flights**
   * Out of 6 million total flights, 2 million (36%) were delayed.
   * Out of the total of more than 6 million flights, 2 million flights were delayed.
   * Southwest Airlines Co. was the leading airline with a huge number of delayed flights (566.6K) followed by Delta Air Lines (282.4K) and United Airlines (256.2K).

2. **Canceled Flights**
   * Out of the total of 6 million flights, 90 thousand (2%) were canceled.
   * The primary cause of flight cancellations was weather (54.3%), followed by airline/carrier-related issues (28.1%), national air system problems (17.5%), and security reasons (minor percentage).
   * Southwest Airlines Co. was the leading airline with a maximum number of canceled flights (16K) followed by Atlantic Southeast Airlines (15.2K) and American Eagle Airlines (15K).
3. **On-Time Flights**
   * Out of the total of 6 million flights, 4 million (62%) were on time.
   * Chicago is the leading city with the maximum number of flights (366.8K) followed by Atlanta (346.8K) and Dallas-Fort Worth (239.6K)
   * Saturday was the day with the maximum of On-Time flights whereas Monday was the day with fewer On-Time flights.
4. **Cancellation by Day**
   * Flight cancellations peaked on Monday (2.6%) followed by Tuesday (1.9%) and Sunday (1.7%).
   * Flight cancellations were lowest on Friday 4 (1.1%) followed by Wednesday and Saturday (1.3%).
5. **Delays by Day**
   * The percentage of delayed flights ranged between 34% to 38%, with day Saturday showing the lowest delay percentage and day Thursday showing the highest delay percentage.
6. **Cancellations and Delays by Airport**
   * Hartsfield-Jackson Atlanta, Chicago O'Hare, and Dallas International Airports were among the hardest-hit cities by both cancellations and delays.
   * Gustavus, King Salmon, and Ithaca Tompkins Regional airports were those with the lowest canceled and delayed flights.
   * The chart shows a general decline in the number of canceled and delayed flights from major airports over time.

## Recommendations:
The following recommendations are provided to help airlines and airports enhance their performance, reduce delays and cancellations, and improve customer satisfaction.
1. **Improve Weather Forecasting and Planning**
   * Since the weather was the largest cause of flight cancellations, investing in better predictive weather technology and scheduling buffer times for adverse conditions could reduce cancellation rates.
2. **Optimize Airline Operations**
   * Southwest Airlines and Delta Air Lines had the highest number of delays. These airlines could improve by reviewing operational efficiency, staffing adequacy, and maintenance schedules to reduce delays.
3. **Strengthen National Air System Coordination**
   * A significant portion of cancellations were due to national air system problems. Better communication and coordination between airlines and air traffic control could help reduce these disruptions.
4. **Address Frequent Issues at Busy Airports**
   * Airports like Hartsfield-Jackson Atlanta, Chicago O'Hare, and Dallas International experience the most cancellations and delays. Implementing more effective contingency plans and increasing staff during high-traffic times could reduce the impact.
5. **Improve Security Procedures**
   * Although a minor contributor, security-related cancellations should be further minimized by enhancing security processes and pre-screening measures to avoid unnecessary delays.
6. **Focus on Peak Delay and Cancellation Days**
   * Monday saw the highest cancellations. Airlines should focus more resources on this high-risk day, possibly by reducing the number of scheduled flights or allocating extra staff and equipment.

   
<br/>
   
**Thank you for taking the time to read this report!**

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge)
