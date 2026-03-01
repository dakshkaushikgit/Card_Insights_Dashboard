# Credit-Card-Financial-Analytics-End-to-End-Dashboard
<br/>
:clipboard: Executive Summary
Overview
Credit card portfolios operate on thin margins driven by transaction volume, interest income, activation rates, and delinquency risk. Weekly monitoring is not optional — it’s operationally critical.
This project builds a structured analytics pipeline that transforms raw transaction and customer data into an executive-ready performance monitoring system. By integrating SQL-based data preparation with Power BI modeling and DAX-driven KPI logic, the dashboard enables stakeholders to track revenue drivers, customer segmentation, geographic concentration, and credit risk indicators in near real time.
Rather than presenting static visuals, this solution replicates how a financial operations team would monitor portfolio health on a weekly cadence.



# Credit_Card_Financial_Dashboard
Credit Card Transaction and Customer Dashboard using Power BI.

 • Developed an interactive dashboard using transaction and customer data from a SQL database, to provide real-time insights. 
 
• Streamlined data processing & analysis to monitor key performance metrics and trends.

 • Shared actionable insights with stakeholders based on dashboard findings to support decision-making processes.

# Project Objective
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

# Import data to SQL database
 1. Prepare csv file 
2. Create tables in SQL
 3. import csv file into SQL

# DAX Queries

 AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )
 IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
 )

  week_num2 = WEEKNUM('public cc_detail'[week_start_date])
 Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
 Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]))) 
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

# Project Insights- Week 53 (31st Dec)

 WoW change: 
• Revenue increased by 28.8%,
 Overview YTD:
 • Overall revenue is 57M
 • Total interest is 8M
 • Total transaction amount is 46M
 • Male customers are contributing more in revenue 31M, female 26M
 • Blue & Silver credit card are contributing to 93% of overall 
transactions
 • TX, NY & CA is contributing to 68%
 • Overall Activation rate is 57.5%
 • Overall Delinquent rate is 6.06%
 
