# Project: Credit Scoring Analysis

## Table of Contents
1. [Introduction](#introduction)
2. [Project Description](#project-description)
3. [About the Dataset](#About-the-dataset)
4. [Importing the Dataset to the Database](#Importing-the-Dataset-to-the-Database)
5. [Preparation of the Dataset: Cleaning and Transforming](#Preparation-of-the-Dataset-Cleaning-and-Transforming)
   * [Renamed columns](#Renamed-columns)
   * [Replaced NA in some Columns](#Replaced-NA-in-some-Columns)
   * [Checked and Deleted NA values](#Checked-and-Deleted-NA-values)
6. [Importing the Cleaned Data to Power BI](#Importing-the-Cleaned-Data-to-Power-BI)
7. [Data Analysis in Power BI](#Data-Analysis-in-Power-BI)
   * [Created DAX Measures for Analysis](#Created-DAX-Measures-for-Analysis)
   * [Created a Calculated Column](#Created-a-Calculated-Column)
8. [Data Visualization in Power BI](#Data-Visualization-in-Power-BI)
9. [Insights from the Data Analysis](#Insights-from-the-Data-Analysis)
10. [Recommendations from the Data Analysis](#Recommendations-from-the-Data-Analysis)
11. [Conclusion](#Conclusion)

## Introduction
This project is the first project launched by DataBeez for interested candidates to participate in a technical test as part of their recruitment process for the profile of Data Scientist/Analyst with skills in modeling, development, and data visualization.

## Project Description
The project involves the analysis of credit scoring for the German Credit Data. The tasks to be completed are as follows:  
1. Explore the data to look for the greatest correlations with whether or not credit is granted
2. Develop a credit scoring prediction model.
3. Create a Dockerfile for deployment.
4. Host the code on GitHub or GitLab.
5. Create an interactive dashboard via Power BI or Looker Studio to visualize the model results.

## About the Dataset
The dataset was downloaded from Kaggle using the link provided by the Recruitment Team. It contains 1000 entries with 20 categorical/symbolic attributes prepared by Prof. Hofmann. In this dataset, each entry represents a person who takes credit from a bank. Each person is classified as having good or bad credit risk according to the set of attributes.  
[Link to the dataset](https://www.kaggle.com/datasets/kabure/german-credit-data-with-risk?resource=download)

The dataset was made of 1000 rows and 11 columns with demographic and financial information. The columns are described as follows:
* *Age*: The age of the person asking for credit
* *Sex*: The sex of the person asking for credit
* *Job*: The job category of the person asking for credit
* *Housing*: The status of the housing of the person asking for credit
* *Saving accounts*: The savings account owned by the person asking for credit
* *Checking account*: The checking account owned by the person asking for credit
* *Credit amount*: The credit amount the person is asking for credit
* *Duration*: Duration of the credit in a month
* *Purpose*: Purpose for the credit

## Importing the Dataset to the Database
To import the dataset to the SQL Server database, I proceeded as follows:  
* Launched the database and connected to it
* Right-clicked on the database name > selected Tasks > selected Import data from the menu
* In the new window that appears, I clicked on Next
* Used the drop-down menu and selected Flat File Source > Next
* Clicked on Browse > selected the file from my computer > Open
* Selected Microsoft OLE DB Provider for SQL Server from the drop-down menu > Next > Next > Finish  
The above steps successfully imported the dataset into my database in SQL Server.

## Preparation of the Dataset: Cleaning and Transforming
In SQL Server, the following tasks were completed.

### Renamed Columns
To rename columns for consistency, the queries below were executed.
* Renamed the Saving accounts column to SavingAccount
```sql
EXEC sp_rename 'dbo.Project1.[Saving accounts]', 'SavingAccount', 'COLUMN';
```

* Renamed the Checking accounts column to CheckingAccount
```sql
EXEC sp_rename 'dbo.Project1.[Checking account]', 'CheckingAccount', 'COLUMN';
```

* Renamed the Credit amount column to CreditAmount
```sql
EXEC sp_rename 'dbo.Project1.[Credit amount]', 'CreditAmount', 'COLUMN'; 
```

* Renamed the Risk column to CreditRisk
```sql
EXEC sp_rename 'dbo.Project1.Risk', 'CreditRisk', 'COLUMN';
```

### Replaced NA in some Columns 
* To reduce the amount of NA in the SavingAccount column, I filled rows with NA in the SavingAccount column with values in the CheckingAccount column using the query below:
```sql
UPDATE p1
SET p1.SavingAccount = p2.CheckingAccount
FROM [DataBeez].dbo.Project1 p1
JOIN [DataBeez].dbo.Project1 p2
	ON p1.id = p2.id
WHERE p1.SavingAccount = 'NA' 
``` 
**Output**: 183 rows were updated in the SavingAccount column.

* To reduce the amount of NA in the CheckingAccount column, I filled rows with NA in the SavingAccount column with values in the SavingAccount column using the query below:
```sql
UPDATE p1
SET p1.CheckingAccount = p2.SavingAccount
FROM [DataBeez].dbo.Project1 p1
JOIN [DataBeez].dbo.Project1 p2
	ON p1.id = p2.id
WHERE p1.CheckingAccount = 'NA';
```
**Output**: 183 rows were updated in the CheckingAccount column.

### Checked and Deleted NA Values  
* Checked rows with NA in both the SavingAccount and the CheckingAccount columns.
```sql
SELECT *
FROM [DataBeez].dbo.Project1
WHERE SavingAccount = 'NA' AND CheckingAccount = 'NA';  
```
Output:  99 rows

* Deleted rows with NA in the SavingAccount and CheckingAccount columns.
```sql
DELETE FROM [DataBeez].dbo.Project1
WHERE SavingAccount = 'NA' AND CheckingAccount = 'NA';  
```
Output: 99 rows were deleted 

* Now, running the query below returned 901 rows.
```sql
SELECT *
FROM [DataBeez].dbo.Project1;
```

## Importing the Cleaned Data to Power BI to Analyse it  
After launching Power BI, I connected to the data as follows:  
* Clicked on Get Data under the Home tab within the Data group
* Selected SQL Server from the list
* Entered the Server name and the database name in each cell
* Clicked on OK. This opened a pop-up window.
* Ticked on the table and clicked on Load. This loaded the data in Power BI.

## Data Analysis in Power BI
1. **Created DAX Measures for Analysis**  
   * *Total Male*
```sql
Total Male = COUNTROWS(FILTER(Project1, Project1[Sex] = "male"))
```
   * *Total Female*
```sql
Total Female = COUNTROWS(FILTER(Project1, Project1[Sex] = "female"))
```
   * *Total Credit Amount*
```sql
Total Credit Amount = SUM(Project1[CreditAmount])
```
   * *Average Credit Amount by Risk Level*
```sql
Avg Credit Amount = AVERAGE(Project1[CreditAmount])
```
   * *Percentage of "Good" and "Bad" Risks*
```sql
Good Credit Risk Percentage = DIVIDE(CALCULATE(COUNTROWS(Project1), Project1[Risk] = "good"), COUNTROWS(Project1), 0) 
```
```sql
Bad Credit Risk Percentage = DIVIDE(CALCULATE(COUNTROWS(Project1), Project1[Risk] = "bad"), COUNTROWS(Project1), 0)
``` 
   * *Average Age*
```sql
Average Age = AVERAGE(Project1[Age])
```
   * *Average Credit Duration*
```sql
Average Credit Duration = AVERAGE(Project1[Duration])
```

2. **Created a Calculated Column**  
* Risk Classification based on Credit Amount
```sql
Risk Category =  IF(Project1[CreditAmount] > 5000, "High Risk", "Low Risk")
```

## Data Visualization in Power BI
* Created Bar charts to showcase the credit amount by purpose and by checking and savings accounts.
* Created Line charts to showcase the credit amount by duration, age, risk category, and age and sex.
* Created donut charts to showcase the credit amount by risk category and housing.
* Created donut charts to showcase the percentage of good vs. bad credit risk.
* Used cards to show the total credit amount, average credit amount, total number of people who applied for credit, the average age, and the average credit duration. 
* Used slicers for sex, housing, credit risk, and risk categories to make the dashboard interactive.

| Figure: Credit Scoring Analysis Dashboard |
| :------------: |
<figure>
  <img src="https://github.com/Songonge/Power-BI-Projects/blob/main/Credit%20Scoring%20Analysis/Credit%20Scoring%20Analysis%20Dashboard.png" width=100% height=100% alt="alt text">
<!--   <figcaption>Figure: Credit Scoring Analysis Dashboard</figcaption> -->
</figure>
<!-- <br/><br/> -->

Here is the [Link to the Interactive Dashboard](https://app.powerbi.com/groups/me/reports/25b71013-82ea-423e-b684-e57c5b89c366?ctid=92454335-564e-4ccf-b0b0-24445b8c03f7&pbi_source=linkShare).
 
## Insights from the Data Analysis
1. **Total Credit Distribution by Purpose**  
   * *Observation*: The majority of credit was issued for cars ($1.05M), followed by radio/TV ($609K) and furniture/equipment ($541K). 
   * *Insight*: These top three loan purposes make up a significant share of the total credit portfolio. Education loans and repairs contribute very little comparatively. The least credit was for domestic appliances.

2. **Credit Risk Analysis**  
   * *Observation*:
     * Good Risk accounts for 60.8%, while Bad Risk makes up 39.2% of the credit issued.
     * High Risk (55.1%) slightly outweighs Low Risk (44.9%), indicating moderate portfolio risk.
   * *Insight*: Despite a majority of "good risk" borrowers, a significant proportion of loans are in the "bad risk" category, requiring further risk management strategies.

3. **Savings and Checking Accounts vs. Credit Amount**  
   * *Observation*:
     * Borrowers with little savings accounts took the highest credit amount ($2.03M), followed by those with moderate savings ($543K).
     * Similarly, borrowers with little checking accounts account for the largest credit amount ($1.42M).
   * *Insight*: Borrowers with minimal financial reserves (savings or checking) are receiving the majority of the loans, which could lead to a higher default risk.
4. **Credit by Age and Duration**  
   * *Observation*:
     * Credit amounts are concentrated among borrowers aged 20–40 years.
     * Loan durations vary widely, with peaks around 20-40 months.
   * *Insight*: The age group 20–40 is highly active in borrowing. Longer durations could lead to repayment challenges for certain risk categories.
5. **Housing Status and Credit Distribution**  
   * *Observation*:
     * Borrowers who own housing account for the largest share of the credit ($1.94M), followed by those renting ($494K) and those with free housing ($452K).
   * *Insight*: Housing ownership correlates with a higher credit share, which may indicate a lower default likelihood compared to renters.

## Recommendations from the Data Analysis
1. **Strengthen Risk Management for High-Risk Borrowers**    
   * Implement stricter risk evaluation criteria for borrowers with little savings and checking accounts, as they dominate the loan portfolio but may struggle with repayments.  
2. **Focus on Diversifying Loan Purpose**  
   * Reduce overreliance on car loans by incentivizing loans for purposes like education or business that offer long-term societal and economic benefits.
3.	**Segment by Age and Duration**  
   * For the 20-40 age group, offer shorter-duration loan products to reduce repayment risks.  
   * Monitor repayment patterns on loans exceeding 40 months.
4.	**Encourage Savings Accounts**  
   * Promote savings-linked loans, where borrowers must demonstrate financial reserves before taking loans. This will improve borrower resilience and motivate repayment within delays.
5.	**Housing and Credit Policy**  
   * For renters and those with "free housing," introduce additional collateral requirements or pre-approval processes to mitigate risk.
6.	**Enhanced Monitoring of 'Bad Risk' Loans**  
   * Use predictive analytics to identify early warning signals for borrowers categorized as "bad risk" and implement intervention strategies (e.g., repayment reminders and restructuring options).

## Conclusion
The dashboard reveals that a large portion of loans are issued to younger borrowers (20–40 years old) with minimal financial reserves and are concentrated in car-related purposes. While most borrowers fall under the "good risk" category, a significant proportion are still high-risk borrowers.
To improve credit portfolio stability:  
* Diversify loan purposes,
* Implement risk-based loan policies,
* Encourage savings-linked borrowing practices.  
By addressing these areas, the organization can better manage credit risk and optimize loan performance for long-term sustainability.


<br/>
   
**Thank you for taking the time to read this report!**

**Please reach out for any updates.**

### Author
[Edwige Songong](https://github.com/Songonge)
