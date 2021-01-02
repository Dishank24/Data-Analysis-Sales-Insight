# Data-Analysis-Sales-Insight
This is a complete real-world Data Analysis Project. 

MySQL was used to collect the data and perform some initial analysis. Then linked this MySQL Database to PowerBi and performed ETL using PowerBi's Power Query feature. After ETL, I made some custom formulaes that I used in my report. Finally, I built the Dashboard/Report using different charts, cards and slicers. 

Tasks performed-
1. Data Collection
2. Data Cleaning
3. Data Wrangling
4. Data Visualization.

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer. 

Data Analysis Using SQL

1. Show all customer records
SELECT * FROM customers;

2. Show total number of customers
SELECT count(*) FROM customers;

3. Show transactions for Chennai market (market code for chennai is Mark001)
SELECT * FROM transactions where market_code='Mark001';

4. Show distrinct product codes that were sold in chennai
SELECT distinct product_code FROM transactions where market_code='Mark001';

5. Show transactions where currency is US dollars
SELECT * from transactions where currency="USD"

6. Show total revenue in year 2020, January Month
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

7. Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

Data Analysis Using Power BI
Formula to create norm_amount column

= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)

