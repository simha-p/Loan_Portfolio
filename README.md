# Loan_Portfolio_Risk

MyBank, a financial Security and Prosperity Bank that has carved as a leader in banking Industry,empowering millions of spectrum of financial services.


## Business overview Problem
Managing Risks associated with these loans to ensure Sustainable growth and Customer Satisfaction.

MyBank challenge revolves around the management of their vast and diverse loan portfolio—a portfolio that has been the cornerstone of the bank's success. There is an immediate need to effectively assess and mitigate this loan portfolio risk as this exposes the bank to constant threat of financial losses, regulatory hurdles, and reputational damage. The problem at hand is not just about safeguarding the bank's own interests but also ensuring the financial well-being of countless clients who have entrusted their dreams and aspirations to this esteemed institution.

Risk analytics provides the tools and methodologies to analyze vast datasets, identify hidden patterns, and extract actionable insights in real-time. Unlike traditional methods that rely on historical data, risk analytics offers the advantage of adaptability. It can continuously process incoming data, enabling the bank to respond promptly to shifting market dynamics, economic indicators, and emerging risks. By harnessing the predictive power of analytics, the bank can proactively identify potential trouble spots within the portfolio, enabling timely interventions that mitigate losses and uphold the institution's financial.


### Aim of Project

This project carries a lofty mission: to revolutionize the bank's approach to loan portfolio risk assessment. Our endeavor is rooted in the belief that data analytics, powered by advanced tools like Power BI, holds the key to unlocking unparalleled insights. These insights will not only empower the bank to make more informed lending decisions but also to optimize their risk management strategies. 


### Data Description

**Default**:a loan occurs when payments are missed and no longer going to paid.
**Arrears**: a loan occurs when payments that are late,but making the payment later. 

The bank has a database with 1500 rows of expense information for analysis, with the following attributes:
 Loan ID: A unique identifier for each loan in the portfolio.
 Borrower ID: A unique identifier for each borrower associated with the loan.
 Borrower Name: The full name of the borrower.
 Gender: The gender of the borrower.
 Borrower Age: The age of the borrower.
 Marital Status: The marital status of the borrower.
 Borrower Address: The address of the borrower.
 Borrower Email: The email address of the borrower.
 Borrower Phone Number: The phone number of the borrower.
 Loan Amount: The amount of money borrowed by the borrower.
 Loan Type: The type of loan, such as personal loan, mortgage, auto loan, or commercial loan.
 Interest Rate: The annual interest rate charged on the loan.
 Loan Term: The duration of the loan, in years.
 Loan Status: The status of the loan, such as "Paid Off," "Defaulted," or "In Arrears."
 Credit Score: The credit score of the borrower, which reflects their creditworthiness.
 Income: The income of the borrower.
 Employment Status: The employment status of the borrower, such as "Employed," "Self-Employed," 
 or "Unemployed."
 Loan Origination Date: The date when the loan was initially issued.
 Loan Paid Date: The date when the loan was paid off or settled.

 ### Tech Stack
The data analysis for this project will be carried out Power BI. 
   ####  Data Importation: Import the data into the environment.
   ####  Data Cleaning and Manipulation
   ####  Data Exploration and Analysis.
   ####  Data Visualization.


**Data Importation & Cleansing: Import data into the power BI  environment and cleanse it by identifying and rectifying errors, missing values, and 
   inconsistencies in the data to ensure its accuracy and reliability.**


**Exploratory Data Analysis: Power BI is utilized to generate descriptive statistics, such as summary statistics, distribution plots.**


**Data Visualization: Power BI interactive dashboards and visualization capabilities enable the creation of charts, graphs, and heatmaps to uncover patterns and 
    trends within the loan portfolio data.**

**Reporting & Recommendation: Power BI facilitates the creation of customized reports for stakeholders, including bank executives, risk management teams, and 
   regulators. These reports provide actionable insights and support data-driven decision-making.**




## Data Transformation
For the Visualization Purpose,we add custom columns like age,income,credit score  to simple structure the data for the Loan Dataset file.


####            Age Range
if [Borrower's age ] >=28 and [Borrower's age]<=34 then "28-34" 
else if [Borrower's age ] >=35 and [Borrower's age]<=41 then "35-41" 
else if [Borrower's age ] >=42 and [Borrower's age]<=48 then "42-48"
else "Above 48"

####           Credit Score Range
if [Credit Score ] >=300 and [Credit Score]<=410 then "300-410" 
else if [Credit Score ] >=411 and [Credit Score]<=521 then "411-521" 
else if [Credit Score] >=522 and [Credit Score]<=632 then "522-632"
else if [Credit Score ] >=633 and [Credit Score]<=743 then "633-743"
else "Above 743"

####            Loan Amount Range
if [Loan Amount] >=1000 and [Loan Amount]<=11000 then "1k-11k" 
else if [Loan Amount] >=12000 and [Loan Amount]<=22000 then "12k-22k" 
else if [Loan Amount] >=23000 and [Loan Amount]<=33000 then "23k-33k"
else if [Loan Amount] >=34000 and [Loan Amount]<=44000 then "34k-44k"
else "Above 44k"

####             Income Range
if [income]>=8000 and [income]<=21000 then "8k-21k"
else if [income]>=22000 and [income]<=35000 then "22k-35k"
else if [income]>=36000 and [income]<=49000 then "36k-49k"
else if [income]>=50000 and [income]<=63000 then "50k-63k"
else "Above 64k"

####             Interest Sum
if [Loan Status] = "Paid Off" or [Loan Status]= "In Arrears" then 
  ([Interest Rate])/100 * [Loan Amount]
else 0.0


![Screenshot 2024-07-25 185107](https://github.com/user-attachments/assets/0ea64d9d-a60a-4226-a958-7cc477dda2e7)



## Date Table

so we need date table for time intelligence analysis.This DataSet contains the loans distribution analysis of Four Years(2018-2021)

#### create StartDate(1/1/2018),EndDate(31/12/2021)

#### Calculate Total Days: 

Duration=[Duration.Days(EndDate-StartDate)+1]:  1461 days


### List Dates in TimeFrame

List.Dates(StatDate, Duration, #duration(1,0,0,0)) ex:[#duration(day,hour,min,sec)]

Covert list Format of Dates to table to extract Year,Month,Quater,Monthname

![Screenshot 2024-07-25 184933](https://github.com/user-attachments/assets/67cfc901-9b5a-482b-b1c1-4141c422ebda)



###             Data Modelling
Create Relationship Between Loan Organisation Date in Loan Dataset to Date Table. 


![Screenshot 2024-07-25 134044](https://github.com/user-attachments/assets/ac2aae1e-ed0b-4ee2-8295-b2ff29cedfb0)



###             Measures Table(KPI's)

**Total Approved Loan = COUNTROWS('loan dataset')**
**Male = CALCULATE(COUNTROWS('loan dataset'),'loan dataset'[Gender]="Male")**
**Female = CALCULATE(COUNTROWS('loan dataset'),'loan dataset'[Gender]="Female")**
**Loan Volume = SUM('loan dataset'[Loan Amount])**
**Interest Earned = SUM('loan dataset'[Interest_Range] )**
**Avg_Income = AVERAGE('loan dataset'[Income])**
**Avg_Credit Score = AVERAGE('loan dataset'[Credit Score])**


![Screenshot 2024-07-25 150903](https://github.com/user-attachments/assets/df46310e-0882-4001-907e-195154ea9494)




#                 Loan Portfolio Ovrview

**Calculate year wise Quaterly **
**Total_Loans(2018)=Total_Loan(2018) = CALCULATE(SUM('loan dataset'[Loan Amount]),'DateTable'[Year] =2018)**

![Screenshot 2024-07-25 151539](https://github.com/user-attachments/assets/eda35d18-9e23-427a-88b8-2c00c6fadfdf)

**Total_Loan(2019) = CALCULATE(SUM('loan dataset'[Loan Amount]),'DateTable'[Year] =2019)**


![Screenshot 2024-07-25 151551](https://github.com/user-attachments/assets/2b578617-cfe8-423c-b630-0b94560089f4)



**Total_Loan(2020) = CALCULATE(SUM('loan dataset'[Loan Amount]),'DateTable'[Year] =2020)**


![Screenshot 2024-07-25 151602](https://github.com/user-attachments/assets/fa53df11-f8d3-40bd-b08f-4c9780ba0fa2)



**Total_Loan(2021) = CALCULATE(SUM('loan dataset'[Loan Amount]),'DateTable'[Year] =2021)**



![Screenshot 2024-07-25 151626](https://github.com/user-attachments/assets/38a030c1-1bae-49be-afc4-8b9589d1f4eb)



**Loan Volume by Marital Status**



![Screenshot 2024-07-25 151944](https://github.com/user-attachments/assets/b83ab17e-a558-45ed-921f-43196db0527b)


**Loan Volume By Employment Status**


![Screenshot 2024-07-25 151813](https://github.com/user-attachments/assets/37dab747-bf32-4e28-be19-57c110b01d28)


**Loan Volume by Age**


![Screenshot 2024-07-25 151732](https://github.com/user-attachments/assets/ce1d49f4-cb34-49d9-af43-212db552b32a)


**Loan Trendline by Year and MonthName**


![Screenshot 2024-07-25 152027](https://github.com/user-attachments/assets/2f71441c-e4ae-495f-8a3d-943458720b95)



##                 Data Visualiation of Loan Portfolio Overview



![Screenshot 2024-07-25 153554](https://github.com/user-attachments/assets/de792b27-32ef-4917-9f44-760325b67eaa)




##                     Loan Status and Types


**Paid Off Loan = CALCULATE(COUNTROWS('loan dataset'),'loan dataset'[Loan Status]="Paid Off")**

**Repayment_rate = DIVIDE([Paid Off Loan],[Total Approved Loan],0)**

**Loan In Arrears = CALCULATE(COUNTROWS('loan dataset'),'loan dataset'[Loan Status]="In Arrears")**

**Delinquency_rate = DIVIDE([Loan In Arrears],[Total Approved Loan],0)**

**Defaulted Loans = CALCULATE(COUNTROWS('loan dataset'),'loan dataset'[Loan Status]="defaulted")**

**Default Rate = DIVIDE([Defaulted Loans],[Total Approved Loan],0)**


![Screenshot 2024-07-25 154237](https://github.com/user-attachments/assets/6bbc4271-0adb-4d6b-8f8a-3a8110ea1fe8)


##                       Types of Loans:

![Screenshot 2024-07-25 154536](https://github.com/user-attachments/assets/d8b267c2-0c57-45cb-86d5-441747047ead)


### Observations:

**Total Mortage Loans= 400 and Mortgage Percentage=26.7%**

**Total Commercial Loans= 372 and Commercial rate=24.8%**

**Total Personal Loans= 370 and Personal rate=24.7%**

**Total Auto Loan= 358 and Auto rate=23.9%**



####                  Loan Volume by Income

![Screenshot 2024-07-25 154442](https://github.com/user-attachments/assets/ee19623f-8741-4f12-8d89-7aae324b9549)


####                  Loan Volume by Terms


![Screenshot 2024-07-25 154425](https://github.com/user-attachments/assets/37710bd8-aa62-4dac-9d0d-00230e71857f)


####                  Loan Volume by Amount Range

![Screenshot 2024-07-25 154552](https://github.com/user-attachments/assets/ffa8ca25-c101-402b-beda-272a9b008686)


####                  Loan Volume by Credit Score

![Screenshot 2024-07-25 154520](https://github.com/user-attachments/assets/486c15ad-c5b2-4147-86e5-df6950221daf)



####                 Data Visualization of Loan Status and Types


![Screenshot 2024-07-25 153859](https://github.com/user-attachments/assets/1514626d-08de-40c0-bca7-96c0ebf20f20)




#                              INSIGHTS:

*Repayment Rate at 61.8% might be considered healthy depending on industry.However Delinquency rate at 21.2% and Default Rate at 17.13% indicating a significant portion of loan portfolio at risk *

*The most loan and interest was seen in 2019 the most borrowed product is Mortage Type *

*35-41 age group had highest sum loan Amount accounted for 26.29 % of Loan Amount*

*Loan Type with highest rate of default was Commercial loan for 2018 and 2019 and mortgage loans for 2020 and 2021*

*In Arrears had $5,322,866 Sum Loan Amount ,Paid off had $16,790,481 and Defaulted had $4,973,421,Signifying that number of borrowers has paid off their debt *


 #                            Recommendation

## Enhanced Credit Scoring:
*Borrowers with Credit scores between 633-743 have highest delay and default rates ,it may be benefical to review and adjust credit scoring model to better predict risk among borrowers within this range.*

## Targeted Risk Management for Loan Type
*Given that Commercial loans had the highest rate of default in 2018-2019 and Mortage in 2020-2021,revising their interest rates to better reflect the associated risk. *

## Age Group Analysis 
*The age group of 35-41 has the highest sum loan amount and hence might be a critical demographic for business.Diversifying Portfolio across different age-groups could mitigate the risk.*

## Delinquency and Default Interventions:
*The delinquency rate and default rates are high.Early Interventions strategiess such as proactive communications and restructuring options could help reduce these rates*

## Review Interest Rates
*Since 2019 had the most loan and interest, review the interst rates from that year to determine if they are competative and sustainable,Particulary given high default rates.*

## Loan Performing Monitoring
*Regulary monitor loans that are "In Arrears" to prevent them from moving into default.Offer assistance such as rpayment plans or financial counselling to help borrowers stay on track*

## Financial Education
*Offer financial literacy programs to borrowers, particularly in high-risk categories to help them understand the importance of maintaining good credit score and managing their loans effctively.*





