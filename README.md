## Table of Contents :

## Problem Statement :
Introduction:
- In today's competitive market, retaining customers is crucial for the success of any business, especially in the telecommunications industry.
- This case study explores the analysis of customer churn for a subscription-based telecom service provider and aims to develop predictive models to identify potential churners. 
- The dataset used includes customer information such as contract details, services used, and churn status.


Objectives :
- The primary objective is to understand the factors influencing customer churn and build machine learning models to predict churn. 
- By doing so, the telecom company can proactively implement retention strategies, thereby reducing customer attrition and improving overall business performance.

## Data Collection : 
Clean and  High-Quality data is essential for accurate analysis and modeling.
- Dataset : [Telecom Customer Churn Analysis](https://github.com/ganesh0823/Telecom_Customer_Churn_Analysis/blob/main/Telco_Customer_Churn.xlsx)
- Content : Contains customer data for churn prediction.
- Source : Sourced from a telecommunications company.

## Data Preparation:
- Explored demographic information, contract details, and services used by customers.
- Investigated the distribution of gender, seniority, partner, and dependent status among customers.
- Analyzed customer tenure, contract types, and the distribution of services used.

Telco Customer Churn is give table named:

- `Telco Customer Churn` which has `21 columns and 7043 rows` of observation
  
In the new table, one additional conditional columns were added using M-formula:
- Loyalty = `SWITCH(TRUE(),'Telco_Customer_Churn'[tenure] <= 12, "< 1 year",'Telco_Customer_Churn'[tenure] <= 24, "< 2 years",  'Telco_Customer_Churn'[tenure] <= 36, "< 3 years",'Telco_Customer_Churn'[tenure] <= 48, "< 4 years",'Telco_Customer_Churn'[tenure] <= 60, "< 5 years",'Telco_Customer_Churn'[tenure] <= 72, "< 6 years", "6+ years")`

- Removed Unnecessary columns 
- Removed Unnecessary rows
- Each of the columns in the table were validated to have the correct data type

## Data Modeling :
It was ready to the data modeled
- The `Telco Customer Churn` tables as show below:
  
![Screenshot (14)](https://github.com/ganesh0823/Telecom_Customer_Churn_Analysis/assets/164488911/e007736e-70ed-4f1c-a4fa-788bad39f3ac)

## Data Analysis (DAX):
Measures used in  all visualization are:
- Avg Monthly Charges = `AVERAGE('Telco_Customer_Churn'[MonthlyCharges])`
  
- Avg Total Charges = `AVERAGE('Telco_Customer_Churn'[TotalCharges])`
  
- Customer Count = `COUNT('Telco_Customer_Churn'[customerID])`
  
- Total Senior Citizens = `CALCULATE(COUNT('Telco_Customer_Churn'[customerID]),'Telco_Customer_Churn'[SeniorCitizen] = 1)`
  
- Churn Count = `CALCULATE(COUNT('Telco_Customer_Churn'[Churn]), ALLSELECTED('Telco_Customer_Churn'[Churn]), 'Telco_Customer_Churn'[Churn] = "Yes")`
  
- Churn Rate % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[Churn]), 'Telco_Customer_Churn'[Churn]="Yes"), COUNT('Telco_Customer_Churn'[Churn]),0)`
  
- Dependent in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[Dependents]), 'Telco_Customer_Churn'[Dependents]="Yes",'Telco_Customer_Churn'[Churn]="Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[Dependents]),'Telco_Customer_Churn'[Churn]="Yes"), 0)`
  
- Device Protection in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[DeviceProtection]), 'Telco_Customer_Churn'[DeviceProtection]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[DeviceProtection]), 'Telco_Customer_Churn'[Churn]="Yes"), 0)`
  
- Multiple Line in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[MultipleLines]), 'Telco_Customer_Churn'[MultipleLines]= "Yes", 'Telco_Customer_Churn'[Churn]="Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[MultipleLines]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Online Backup in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[OnlineBackup]), 'Telco_Customer_Churn'[OnlineBackup]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[OnlineBackup]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Online Security in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[OnlineSecurity]), 'Telco_Customer_Churn'[OnlineSecurity]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[OnlineSecurity]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Partner in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[Partner]), 'Telco_Customer_Churn'[Partner]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[Partner]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Phone Service in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[PhoneService]), 'Telco_Customer_Churn'[PhoneService]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[PhoneService]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- SeniorCitizen in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[SeniorCitizen]), 'Telco_Customer_Churn'[SeniorCitizen]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[SeniorCitizen]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Streaming Movies in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[StreamingMovies]), 'Telco_Customer_Churn'[StreamingMovies]= "Yes", 'Telco_Customer_Churn'[Churn]="Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[StreamingMovies]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Streaming TV in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[StreamingTV]), 'Telco_Customer_Churn'[StreamingTV]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[StreamingTV]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`
  
- Tech Support in % = `DIVIDE(CALCULATE(COUNT('Telco_Customer_Churn'[TechSupport]), 'Telco_Customer_Churn'[TechSupport]= "Yes", 'Telco_Customer_Churn'[Churn]= "Yes"), CALCULATE(COUNT('Telco_Customer_Churn'[TechSupport]), 'Telco_Customer_Churn'[Churn]= "Yes"), 0)`

## Data Visualization (Dashboard) :
Dashboard: [View Dashboard] 

  












