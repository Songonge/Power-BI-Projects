# Project: HR Analytics

## Table of Contents  
1. [Introduction](#introduction)
2. [Project Aim](#project-aim)
3. [Project Description](#project-description)
4. [Data Acquisition and Preparation](#data-acquisition-and-preparation)
5. [Data Cleaning and Transformation](#data-cleaning-and-transformation)
6. [Data Analysis and Visualization](#data-analysis-and-visualization)
   * [HR Attrition Dashboard](#hr-attrition-dashboard)
   * [Demographics Dashboard](#demographics-dashboard)
   * [Turnover Analysis I Dashboard](#turnover-analysis-I-dashboard)
   * [Turnover Analysis II Dashboard](#turnover-analysis-II-dashboard)
   * [Employee Wellness Dashboard](#employee-wellness-dashboard)
7. [Interpretation of Data](#interpretation-of-data)
8. [Recommendations](#recommendations)
   
## Introduction
This project about HR Analytics focuses on data analytics which aims at evaluating the current human resources practices within the organization, identifying key areas for improvement, and providing actionable recommendations aimed at enhancing workforce efficiency, employee satisfaction, and overall organizational performance. Power Query in Power BI will be used to clean and transform the data. Then, dashboards will be built to communicate critical insights.

## Project Aim
Delve into the world of human resources, with a keen eye on data analysis to optimize talent management and organizational performance. The project seeks to address pressing questions and uncover meaningful conclusions based on data.   

## Project Description
This project involves a detailed analysis of various aspects of HR, including demographics, employee turnover analysis, and employee wellness. Details are given regarding employee statistics, attrition, performance management, training and development, compensation and benefits, and employee retention. The analysis will utilize both qualitative and quantitative data to provide a comprehensive understanding of the HR landscape. Overall, this project demonstrates my capacity to work with and extract meaning from large datasets, allowing me to provide insights into workforce diversity and communicate patterns for informed decision-making and enhanced HR practices.  

The following are the deliverables from this project:
*	Comprehensive HR analysis report with detailed findings and recommendations.
*	Executive summary highlighting key insights and strategic recommendations.
*	Implementation plan with timelines and resource requirements.
*	Presentation to key stakeholders summarizing the report's findings and recommendations.
  
## Data Acquisition and Preparation
MeriSKILL provided the dataset. I downloaded it from Google Drive. Then, I uploaded it in Power BI using the Get Data option. This dataset was unclean and had 35 columns and 1471 rows. 

## Data Cleaning and Transformation 
The first row of the data was used as headers using the option Use First Row as Headers under the Home tab. Then, using the Transform tab, I selected Detect Data Type to automatically identify the data type of each column and convert them where needed. Next, I
•	Deleted redundant columns: this reduced the columns to 26.
•	Renamed the columns appropriately.
•	Deleted null and duplicate values.
•	Cleaned individual columns.
•	Removed the NaN (Not a Number) values from the dataset.
•	Checked for some more Transformations to ensure the remaining data was ready for analysis.

## Data Analysis and Visualization

### HR Attrition Dashboard
In Power BI, I used Visualizations to create five dashboards. The first dashboard about **HR Attrition** provides an overview of all four dashboards I created. This is shown in Figure 1.

<figure>
  <img src="https://github.com/Songonge/MeriSKILL/blob/main/HR Analytics Project/HR Attrition - Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure 1: HR Attrition Dashboard</figcaption>
</figure>
<br/><br/>

### Demographics Dashboard
The second dashboard about Demographics summarizes employee statistics is shown in Figure 2. The following steps were performed. 
1.	I calculated the total number of employees.
2.	I created a clustered bar chart for total attrition by the education field.
3.	I used the formula `Attrition Count=SWITCH(true(),‘HR-Employee-Attrition’ [Attrition]=“Yes”,1,‘HR-Employee-Attrition’[Attrition]=“No”,0,0)`
Summing all the 1s gave the total of 237 attrition count. Then, subtracting this number from the employee count using the formula `AE=SUM(‘HR-Employee-Attrition’ [EMployeeCount])- SUM(‘HR-Employee-Attrition’ [Attrition Count])` This gave `1233` as the count of active employees.
4.	I used groups to aggregate certain values together to form meaningful subsets. These were done for Age (18-30, 31-45, 46-60), Work-Life Balance (1 as "Bad", 2 as "Average", 3 as "Good", and 4 as "Excellent"), and Distance From Home (1-10 as “Near-by”, 11-20 as “Far” and 21 – 29 as “Very far”).

<figure>
  <img src="https://github.com/Songonge/MeriSKILL/blob/main/HR Analytics Project/Demographic - Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure 2: Demographics Dashboard</figcaption>
</figure>
<br/><br/>

### Turnover Analysis I Dashboard
The third and fourth dashboards about Turnover Analysis I and II contain details about employee attrition. The steps below were performed:
1.	Created a stacked bar chart for Total attrition by job role distinguishing males and females.
2.	Created a stacked column chart for Total attrition by business travel.
3.	Created a donut chart for Total attrition by the department.
4.	Created a stacked column chart for Total attrition by years in current role.
5.	Created a Treemap for Total attrition by job role counting the total number of “Yes” attritions for each category.

<figure>
  <img src="https://github.com/Songonge/MeriSKILL/blob/main/HR Analytics Project/Turnover Analysis 1 - Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure 3: Turnover Analysis I Dashboard</figcaption>
</figure>
<br/><br/>

### Turnover Analysis II Dashboard
The fourth dashboard about Turnover Analysis II contains additional details about employee attrition. The dashboard is shown in Figure 4. I performed the steps below:
1.	Created a clustered column chart for total attrition by age and gender.
2.	Created a pie chart for total attrition by performance and rating.
3.	Created a stacked column chart for total attrition by overtime. To do this, I first grouped values: 1 for “Entry Level”, 2 for “Junior or Associate”, 3 for “Middle-level Specialist”, 4 for “Senior”, and 5 for “Executive”.
4.	Created a funnel for total attrition by job level based on the groups from step 3.
5.	Created a line chart for monthly income and attrition by job role.

<figure>
  <img src="https://github.com/Songonge/MeriSKILL/blob/main/HR Analytics Project/Turnover Analysis 2 - Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure 3: Turnover Analysis II Dashboard</figcaption>
</figure>
<br/><br/>

### Employee Wellness Dashboard
The fifth dashboard about Employee Wellness focuses on employee satisfaction regarding several factors. Figure 5 presents the dashboard which was built following the steps below:
1.	Created a clustered column chart for Total attrition by environmental satisfaction. Note that Environmental satisfaction was rated on a scale ranging from 1 to 4 (1 for "Very Dissatisfied," 2 for "Dissatisfied," 3 for "Satisfied," and 4 for "Very Satisfied").
2.	Created a clustered bar chart for Total attrition by job involvement. The job involvement was also grouped (1 for "Very Low," 2 for "Low," 3 for "Moderate," and 4 for "High").
3.	Created two clustered column charts for Total attrition by job satisfaction and by relationship satisfaction. Both fields were also rated: 1 for "Very Dissatisfied," 2 for "Dissatisfied," 3 for "Satisfied," and 4 for "Very Satisfied".
4.	Created a clustered column chart for Total attrition by performance rating. Performance rating was rated: 3 for “Low” and 4 for “High”.
5.	Created a pie chart for total attrition by work-life balance. Note that on the work-life balance, 1 represents "Bad", 2 stands for "Average", 3 signifies "Good", and 4 indicates "Excellent".

<figure>
  <img src="https://github.com/Songonge/MeriSKILL/blob/main/HR Analytics Project/Employee Wellness - Dashboard.png" width=100% height=100% alt="alt text">
  <figcaption>Figure 3: Employee Wellness Dashboard</figcaption>
</figure>
<br/><br/>

> [!NOTE]
> In these dashboards, grouping played a crucial role in organizing and presenting data effectively. The design of the dashboards was tailored to utilize the power of grouping for enhanced data visualization and analysis.

## Interpretation of Data
The following insights were derived from the data analysis:
*	Many employees traveled rarely.
*	There was a correlation between the hourly rate and the daily rate.
*	Concerning environmental satisfaction, employees living nearby accounted for the majority. These employees were also seen as more active and traveled rarely. On the other hand, Entry Level and Junior or Associate employees were noticeably satisfied with the environment and were mostly males.
*	 Most of the jobs involvement fell under the Research & Development category. 
*	The majority of employees were between 31-45 years old.
*	Most employees who rated “Good” for Work-Life Balance were female.

## Recommendations
Based on the insights from the HR analysis report, here are several recommendations I derived to address the identified trends and enhance employee satisfaction and organizational efficiency:
*	Since many employees traveled rarely and those living nearby were more active, the organization should consider expanding flexible remote work options to improve work-life balance and reduce commuting stress.
*	Promote initiatives that encourage local engagement and activities for employees who live nearby, as this group shows higher activity levels and environmental satisfaction. 
*	The correlation between hourly rate and daily rate suggests a need to review the compensation structure to ensure fairness and competitiveness. Implementing a transparent and equitable pay scale could help in retaining talent and boosting morale.
*	Entry-level and Junior/Associate employees, who are predominantly male, are notably satisfied with the environment. Therefore, consider implementing more targeted improvements in workplace facilities and amenities to maintain or enhance this satisfaction across other employee groups as well. 
*	Given that most females rated "Good" for work-life balance, ensure inclusivity by creating programs that support all employees' needs, such as gender-neutral parental leave policies and flexible scheduling. In addition, continue to develop and promote work-life balance initiatives, such as flexible work hours, remote working options, and wellness programs, to sustain and improve overall employee satisfaction.
*	With most job involvement in Research & Development, offering specialized training and professional development opportunities in this area can enhance skills and keep employees engaged. 
*	Implement recognition programs to reward and acknowledge contributions to Research & Development, fostering a culture of innovation and dedication. 
*	The majority of employees being between 31-45 years old suggests a need for wellness programs tailored to this age group, focusing on physical health, mental well-being, and career progression. 
*	Provide clear career advancement pathways and mentorship programs to support employees in this age bracket in achieving their professional goals and maintaining high levels of job satisfaction.

By implementing these recommendations, the organization can address key insights from the HR analysis, leading to a more satisfied, efficient, and productive workforce.


<br/><br/>

**Thank you for taking the time to read this report!** 

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge) Powered by [MeriSKILL](https://meriskill.in/)


