# Sales_insights_of_data_analysis-AtliQ_Hardware-

![image](https://github.com/user-attachments/assets/5227d1d1-dbb7-4c71-b62b-b37edef7ccd7)

## Table of Contents:
- [Problem Statement]
- [Data Discovery]
- [Data Analysis using MySQL ]
- [Data Cleaning and ETL (Extract, Transform, Load)]
- [Data Modeling]
- [Build Dashboard Or a Report]
- [Tools, Software and Libraries]
- [References]


## Problem Statement :
In this project, performed India-based AtliQ hardware company sales insights - A Data Analysis project. 

AtliQ Hardware is a company that supplies computer hardware and peripherals to many clients, such as surge stores, Nomad stores, etc., across India. The Company's head office is situated in Delhi, India, and it has many regional offices throughout the country.

The sales director for this company is facing a lot of challenges. The market is growing dynamically, and the sales director is facing issues in terms of tracking the sales in this dynamic growth market. He is having issues with the growth of this business, as overall sales are declining. He is the regional manager for North India, South and Central India. Whenever he wanted to get insights into these regions, he would call these people, and on the phone regional manager would give him some insights, to him that this was the sales last quarter and we are going to grow by this much in the next quarter.

The problem was that all these things happening were verbal and there was no proof with facts that how the business is affected. He could see that overall sales were declining but when he asked regional manager, there was no clear picture. so to see clear insights and to take data-driven decisions to increase sales of his company.
He needs a simple data visualization tool that he can access on a daily basis. So, in this project, we will help a company make a simple sales-related dashboard using Power BI.


## Data Discovery :

- #### Project Planning using AIMS Grid -

  It is a project management tool that consists of four components-
  
     - Purpose - (What to do exactly)
     - Stackholder - (Who will be involved)
     - End result - (What do you want to achieve)
     - Success Criteria - (Cost optimization and time save)
- #### AIMS Grid -
   **1. Purpose :-** To unlock sales insights that were not visible before for the sales team for decision support and automate them to reduce manual time spent in data gathering.

   **2. Stakeholders :-**
   - Sales Director
   - Marketing Team
   - Customer Service Team
   - Data and Analytics Team
   - IT

**3. End result :-** An automated dashboard providing quick and latest sights to support Data driven decision making.

**4. Success Criteria :-**
- Dashboard uncovering sales order insights with the latest data available.
- Sales team able to make better decisions and prove 10% cost saving of total spend.
- Sales analysis stop data gathering manually to save business time and reinvest into value added activities.


## Data Analysis using MySQL :
Completed the Data discovery and then used mySQL for data analysis.

SQL database dump is in db_dump.sql file above     
     
- Importing Data to MySQL workbench
  
   The import of data is done from an already existing MySQL file. This file has to be loaded into MySQL workbench for further data analysis.

- Analysis of data by looking into different tables and reflecting garbage values
 
   We can see that garbage value that the table market cantains certain values which are incorrect.
   
     `SELECT * FROM sales.market;`
     
   And then we can check that transacation table we can see that ceratin negative value in amount which is not possible. and we can see that certain transactions are      in USD. Hence, filtration of that is also needed by converting into INR.
     
     `SELECT * FROM sales.transactions;`
     
 - Analysis of different SQL statement on data base
     
   1.To find of all customers records 
     
     `SELECT * FROM sales.customers;`
      
   2.To find total number of customers 
     
     `SELECT count(*) From sales.customers;`

   3.To find transactions for Chennai market (market code for chennai is Mark001
     
      `SELECT * FROM sales.transactions where market_code='Mark001';`

   4.To find distrinct product codes that were sold in chennai
     
      `SELECT distinct product_code FROM sales.transactions where market_code='Mark001';`

   5.To find transactions for Chennai market (market code for chennai is Mark002
     
      `SELECT * FROM sales.transactions where market_code='Mark002';`

   6.To find distrinct product codes that were sold in mumbai
     
      `SELECT distinct product_code FROM sales.transactions where market_code='Mark002';`
      
   7.To find transactions where currency is US dollars
     
      `SELECT * from sales.transactions where currency="USD";` 
      
   8.To find transactions in 2020 join by date table
     
      `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;`  

   8.To find transactions in 2019 join by date table
     
      `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;`  

   9.To find total revenue in year 2020,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";` 
      
   10.To find total revenue in year 2019,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`       

   11.To find total revenue in year 2020, January Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   12.To find total revenue in year 2020, February Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   13.To find total revenue in year 2019, January Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   14.To find total revenue in year 2019, February Month,
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");` 

   15.To find total revenue in year 2020 in Chennai
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";` 

   16.To find total revenue in year 2020 in Mumbai
     
      `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark002";` 

Similarly, if we want different of any other particular city the market code of that city is used on the mysql workbench.

## Data Cleaning and ETL (Extract, Transform, Load):
In this process, we are work on data cleaning and ETL.

 Step 1: Connect the MySQL database with the PowerBI desktop.
 
 Step 2: Loading data into the Power BI deskstop.
 This step load all the tables and created in the data base. This load option will connect with the SQL and pull all the records into power BI environment.
         
 In that model view looking up for model which form the star schema.
         
![Data modeling](https://github.com/user-attachments/assets/9dbe37e1-d070-4d7f-9178-4c0a0faadcea)

 Setp 3: Transform data with the help of Power Query
 
 Perform filtration in market’s table: In the tables perform when we click on the transform data option, we are directed to Power query editor. Power query editor is where we perform out ETL.and then we can perform data transformation i.e. Data Cleaning, Data Wrangling, Data Munging. we need to filter the rows where the values are null and filtering the data and deselecting the blank option. 

 Perform filtration in Transaction’s table: In the table perform when we check the query in the MySQL to filter some negative values and also 0 values that appears in the table, the desired output is received.and we will perform the similar filtration in PowerBI. we have deselecting the values, don’t want in the table. The result after filtration. the zero values represent some garbage values which is not possible so we need to clean that data.

Convert USD into INR in the transaction’s table: the AtliQ Hardware only works in India so the USD values are not possible. we need to convert those USD values into INR by using some formulas. Add new column - Conditional column - normalized currency where sales amount will be in INR

In power query editore finding the total values having USD as currency.

     `=Table.AddColumn(#"Filtered Rows", "norm_sales_amount",each if [currency] = "USD" then [sales_amount]*75 else [sales_amount]`
 
 using this correct formula of the conversion,and converted the USD currency into INR.
 
 In MySQL Workbench find that there are duplicates of USD and INR
 
     `SELECT count(*) from sales.transactions where sales.transactions.currency="INR\r";` 
     150000 - can't removed as it is large amount

     `SELECT count(*) from sales.transactions where sales.transactions.currency="INR";` 
     279 - we can remove it as it is small record and can be considered as bad data

     `SELECT count(*) from sales.transactions where sales.transactions.currency="USD\r";` 
 
     `SELECT count(*) from sales.transactions where sales.transactions.currency="USD";`

     `SELECT * from sales.transactions where sales.transactions.currency='USD\r' or sales.transactions.currency='USD';`

we can see that it is duplicate and for analysis its better to delete anyone of them so lets delete USD and keep USD/r. finally we will keep data with INR/r and USD/r- 


## Build Dashboard Or a Report:

Data visualization for the data analysis was done in Microsoft Power BI Desktop:

Shows visualizations from Sales insights :

![image](https://github.com/user-attachments/assets/cf759b08-108a-4452-b14b-d29d7039c75a)
![image](https://github.com/user-attachments/assets/ec0a488d-27ae-42ad-9914-b359ac999217)
![image](https://github.com/user-attachments/assets/7300afed-f103-431d-a37d-bcfc7e28dfec)

## Tools, Software and Libraries :

1.MySQL
     
2.Microsoft Power BI

3.Power Query Editor

## References :

https://codebasics.io/resources/sales-insights-data-analysis-project
---
