## Czechoslovakia Banking Financial Data Analysis
Introduction
The Czechoslovakia Bank has provided a dataset containing information about its 
financial activities for the past 5 years. The dataset consists of the following tables:
1. Account: This table contains information about the accounts held by the 
bank's clients. It includes the account ID, the date the account was opened, 
the associated client ID, and the account type.
2. Card: This table contains information about the card issued by the bank. It 
includes the card ID, the date the card was issued, and the card type.
3. Client: This table contains information about the bank's clients. It includes 
the client ID, the client's birthdate, gender, and the district where the client 
lives.
4. Disposition: This table contains information about the relationship between 
clients and their accounts. It includes the disposition ID, the client ID 
associated with the disposition, and the type of disposition (e.g., owner, 
authorized person, etc.).
5. District: This table contains information about the various districts in 
Czechoslovakia. It includes the district ID, the name of the district, and 
various demographic and economic indicators for the district.
6. Loan: This table contains information about the loans issued by the bank. It 
includes the loan ID, the date the loan was issued, the account ID associated 
with the loan, the amount of the loan.
7. Order: This table contains information about the orders issued by the bank's 
clients. It includes the order ID, the account ID associated with the order, the 
date the order was issued, and a description of the order.
8. Transaction: This table contains information about the transactions made by 
the bank's clients. It includes the transaction ID, the account ID associated
with the transaction, the transaction date, the type of transaction, and the 
transaction amount.

#### Data Manipulation and Cleaning work

##### Account Table
1.	Convert the Date attribute into a yyyy-mm-dd by adding 24 in year format in Excel or SQL 
●	1993 -> 2017
●	1994 -> 2018
●	1995 -> 2019
●	1996 -> 2020
●	1997 -> 2021

2.	Replace in frequency attribute “POPLATEK MESICNE” AS Monthly Issuance, “POPLATEKTYDNE” AS Weekly Issuance, and “POPLATEK POBRATU” AS Issuance After a Transaction in Excel or create a case statement in SQL.
  
3.	Create a Custom Column Card_Assigned and assign below : 
●	Silver -> Monthly issuance
●	Diamond - weekly issuance
●	Gold - Issuance after a transaction

##### CARD Table

1.	Replace type attribute value “junior” as Sliver, “Classic” as Gold,
And “Gold” as Diamond by using replace in Excel or by using update in SQL.

2.	Convert issued attribute into yyyy-mm-dd adding 23 in year.

#### CLIENT Table 

1.	Convert bith_number attribute to yyyy-mm-dd format and also create another column named sex by applying in bith_number 0 for females and 1 for males.
(=if(mod(bith_number,2)=0, “Female”, “Male”) in excel or using case statement in SQL.
For Male its in YYMMDD format and for female it is YYMM+50DD for Women


##### DISTRICT Table
1.	Change all column names and delete the attributes a12 and 
	

#### LOAN Table
1.	Convert the Date Attribute into yyyy-mm-dd format adding 23 in year.
2.	Convert Status Attribute value “A” as Contract Finished, “B” as Loan Not Paid, “C” as Running Contract, and “D” Client in debt.

In th Transactions Table do the following , whosoever count is highest sort it in descending order and change the year from 2022,2021,2020 and so on
--DATA TRANSFORMATION
/*
2021 -> 2017
2020 -> 2018
2019 -> 2019 -- NO CHANGE
2018 -> 2020
2017 -> 2021
2016 -> 2022 
UPDATE TRANSACTIONS
SET BANK = 'Sky Bank' WHERE BANK IS NULL AND YEAR(DATE) = 2022;

UPDATE TRANSACTIONS
SET BANK = 'DBS Bank' WHERE BANK IS NULL AND YEAR(DATE) = 2021;

UPDATE TRANSACTIONS
SET BANK = 'Northern Bank' WHERE BANK IS NULL AND YEAR(DATE) = 2019;

UPDATE TRANSACTIONS
SET BANK = 'Southern Bank' WHERE BANK IS NULL AND YEAR(DATE) = 2018;





