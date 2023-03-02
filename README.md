# data-analysis
## Create e_commerce database
`CREATE DATABASE e_commerce;`

Query OK, 1 row affected (0.01 sec)

`USE e_commerce;`

Database changed
## Create a region table



`CREATE TABLE region(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(25)
    );`
    
| id    | name                   | 
|-------|------------------------|
| NULL  | NULL                   |

Query OK, 0 rows affected (0.11 sec)
## Create a sales_repos table


`CREATE TABLE sales_repos(
	  id INT NOT NULL PRIMARY KEY,
    name VARCHAR(25) NOT NULL,
    region_id INT NOT NULL,
    FOREIGN KEY (region_id) REFERENCES region(id) );`

| id   | name                   | region_id    | 
|------|------------------------|--------------| 
| NULL | NULL                   | NULL         |


Query OK, 0 rows affected (0.11 sec)
## Create a accounts table

`CREATE TABLE accounts(
	  id INT NOT NULL PRIMARY KEY,
    name VARCHAR(25) NOT NULL,
    age INT,
    phone_number INT,
    password VARCHAR(25),
    sales_rep_id INT,
    FOREIGN KEY (sales_rep_id) REFERENCES sales_repos(id) );`

| id   | name                   | age   | phone_number | password | sales_rep_id |
|------|------------------------|-------|--------------|----------|--------------|
| NULL | NULL                   | NULL  | NULL         | NULL     | NULL         |

## Create a  orders table

`CREATE TABLE  orders(
	  id INT PRIMARY KEY,
    amount INT,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES accounts(id) );`
    

| id   | amount                  | customer_id |
|------|-------------------------|-------------|
| NULL | NULL                    | NULL        |

## Data Insert  for all table  [e_commerce_data.zip](https://github.com/anwar-opu/data-analysis/files/10823474/e_commerce_data.zip)


Syntex   : `INSERT INTO table_name(col_name1,col_name2)
	   VALUES(value_1, value_2);`
	   
Example	 : `INSERT INTO e_commerce.region (id, name)
	   VALUES (1, 'Dhaka'), (2, 'Cumilla'), (3, 'Chittagong'), (4, 'Sylhet');`
 

## Show table (all) :

  `SELECT * FROM region;`
  
      +----+------------+
      | id | name       |
      +----+------------+
      |  1 | Dhaka      |
      |  2 | Cumilla    |
      |  3 | Chittagong |
      |  4 | Sylhet     |
      +----+------------+
           region

  `SELECT * FROM sales_repos;`

      +------+--------------+-----------+
      | id   | name         | region_id |
      +------+--------------+-----------+
      | 3301 | Abul Kalam   |         1 |
      | 3302 | Rahim Ahmed  |         2 |
      | 3303 | Shanaj Akter |         3 |
      | 3304 | Amit Deb     |         4 |
      +------+--------------+-----------+
                  sales_repos
                  
   `SELECT  * FROM  accounts;`
   
      +----+---------+------+--------------+-------------+--------------+
      | id | name    | age  | phone_number | password    | sales_rep_id |
      +----+---------+------+--------------+-------------+--------------+
      |  1 | Sohan   |   23 |       123546 | hghdgfjdj   |         3304 |
      |  2 | Salman  |   22 |       123546 | wrytuyet    |         3301 |
      |  3 | Arman   |   22 |       123546 | sjerthjsdfg |         3304 |
      |  4 | Humayun |   22 |       123546 | password    |         3301 |
      |  5 | Himu    |   23 |       235468 | sdfgdsfgdfg |         3302 |
      |  6 | Omi     |   32 |        35405 | sfdgsdfg    |         3302 |
      |  7 | Alfi    |   27 |      3546111 | sdfgsdfg    |         3301 |
      |  8 | Minhaj  |   21 |      3254163 | sfdsgfsd    |         3303 |
      |  9 | Maruf   |   35 |      9465555 | sfgsdgsdf   |         3303 |
      | 10 | Shakil  |   19 |       546416 | agsdfgs     |         3303 |
      +----+---------+------+--------------+-------------+--------------+                 
                       accounts
                       
   `SELECT * FROM orders;`
    
      +----+--------+-------------+
      | id | amount | customer_id |
      +----+--------+-------------+
      |  1 |   1000 |           2 |
      |  2 |   2050 |           4 |
      |  3 |   5000 |           2 |
      |  4 |   1520 |           1 |
      |  5 |   2150 |           4 |
      |  6 |   9000 |           7 |
      |  7 |   1800 |           1 |
      |  8 |   5000 |           6 |
      |  9 |   1520 |           8 |
      | 10 |   2150 |           5 |
      | 11 |   8500 |           2 |
      | 12 |   1750 |          10 |
      | 13 |   1800 |           1 |
      | 14 |   5000 |           6 |
      | 15 |   6200 |           8 |
      | 16 |   2150 |           5 |
      | 17 |   8000 |           2 |
      | 18 |   3600 |          10 |
      +----+--------+-------------+
                orders
                
 ## Rename Table : "RENAME TABLE" statement is used to rename an existing table.
 
  Syntex : `RENAME TABLE old_table_name TO new_table_name;`
  
  Example : `RENAME TABLE accounts TO account;`
  
  Before :
  
      +----+---------+------+--------------+-------------+--------------+
      | id | name    | age  | phone_number | password    | sales_rep_id |
      +----+---------+------+--------------+-------------+--------------+
      |  1 | Sohan   |   23 |       123546 | hghdgfjdj   |         3304 |
      |  2 | Salman  |   22 |       123546 | wrytuyet    |         3301 |
      |  3 | Arman   |   22 |       123546 | sjerthjsdfg |         3304 |
      |  4 | Humayun |   22 |       123546 | password    |         3301 |
      |  5 | Himu    |   23 |       235468 | sdfgdsfgdfg |         3302 |
      |  6 | Omi     |   32 |        35405 | sfdgsdfg    |         3302 |
      |  7 | Alfi    |   27 |      3546111 | sdfgsdfg    |         3301 |
      |  8 | Minhaj  |   21 |      3254163 | sfdsgfsd    |         3303 |
      |  9 | Maruf   |   35 |      9465555 | sfgsdgsdf   |         3303 |
      | 10 | Shakil  |   19 |       546416 | agsdfgs     |         3303 |
      +----+---------+------+--------------+-------------+--------------+                 
                       accounts                
  After :
  
      +----+---------+------+--------------+-------------+--------------+
      | id | name    | age  | phone_number | password    | sales_rep_id |
      +----+---------+------+--------------+-------------+--------------+
      |  1 | Sohan   |   23 |       123546 | hghdgfjdj   |         3304 |
      |  2 | Salman  |   22 |       123546 | wrytuyet    |         3301 |
      |  3 | Arman   |   22 |       123546 | sjerthjsdfg |         3304 |
      |  4 | Humayun |   22 |       123546 | password    |         3301 |
      |  5 | Himu    |   23 |       235468 | sdfgdsfgdfg |         3302 |
      |  6 | Omi     |   32 |        35405 | sfdgsdfg    |         3302 |
      |  7 | Alfi    |   27 |      3546111 | sdfgsdfg    |         3301 |
      |  8 | Minhaj  |   21 |      3254163 | sfdsgfsd    |         3303 |
      |  9 | Maruf   |   35 |      9465555 | sfgsdgsdf   |         3303 |
      | 10 | Shakil  |   19 |       546416 | agsdfgs     |         3303 |
      +----+---------+------+--------------+-------------+--------------+                 
                       account
		       
## Select statement : "SELECT" statement is used to retrieve data from a database.

Syntex  : `SELECT col_name
		FROM table_name;`

Example : `SELECT id,name,age 
		FROM accounts;`
		
Output : 

	+----+---------+------+
	| id | name    | age  |
	+----+---------+------+
	|  1 | Sohan   |   23 |
	|  2 | Salman  |   22 |
	|  3 | Arman   |   22 |
	|  4 | Humayun |   22 |
	|  5 | Himu    |   23 |
	|  6 | Omi     |   32 |
	|  7 | Alfi    |   27 |
	|  8 | Minhaj  |   21 |
	|  9 | Maruf   |   35 |
	| 10 | Shakil  |   19 |
	+----+---------+------+
	        accounts
		
## Select_all statement : "*" symbol is used as a wildcard character in the "SELECT" statement to select all columns from a table.

Syntex  : `SELECT *
		FROM table_name;`

Example : `SELECT * 
		FROM accounts;`
		
Outout :

	+----+---------+------+--------------+-------------+--------------+
	| id | name    | age  | phone_number | password    | sales_rep_id |
	+----+---------+------+--------------+-------------+--------------+
	|  1 | Sohan   |   23 |       123546 | hghdgfjdj   |         3304 |
	|  2 | Salman  |   22 |       123546 | wrytuyet    |         3301 |
	|  3 | Arman   |   22 |       123546 | sjerthjsdfg |         3304 |
	|  4 | Humayun |   22 |       123546 | password    |         3301 |
	|  5 | Himu    |   23 |       235468 | sdfgdsfgdfg |         3302 |
	|  6 | Omi     |   32 |        35405 | sfdgsdfg    |         3302 |
	|  7 | Alfi    |   27 |      3546111 | sdfgsdfg    |         3301 |
	|  8 | Minhaj  |   21 |      3254163 | sfdsgfsd    |         3303 |
	|  9 | Maruf   |   35 |      9465555 | sfgsdgsdf   |         3303 |
	| 10 | Shakil  |   19 |       546416 | agsdfgs     |         3303 |
	+----+---------+------+--------------+-------------+--------------+
				accounts
## Distinct : "DISTINCT" keyword is used in the "SELECT" statement to retrieve unique or distinct values from a column or set of columns.

Syntex  : `SELECT DISTINCT col_name
		FROM table_name;`

Example : `SELECT DISTINCT city
		FROM region;`
		
Before :

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	|  5 | Dhaka      |
	+----+------------+
		region
After :

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	+----+------------+
		region
## Order by : "ORDER BY" clause is used in the "SELECT" statement to sort the results of a query in ascending or descending order based on one or more columns.

ascending order:

Syntex  : `SELECT  col_name
		FROM table_name ORDER BY col_name; `

Example : `SELECT id,name 
		FROM accounts ORDER BY id; `

Output :

	+----+---------+
	| id | name    |
	+----+---------+
	|  1 | Sohan   |
	|  2 | Salman  |
	|  3 | Arman   |
	|  4 | Humayun |
	|  5 | Himu    |
	|  6 | Omi     |
	|  7 | Alfi    |
	|  8 | Minhaj  |
	|  9 | Maruf   |
	| 10 | Shakil  |
	+----+---------+
	    accounts
	    
descending order :

Syntex  : `SELECT  col_name
		FROM table_name ORDER BY col_name DESC; `

Example : `SELECT id,name 
		FROM accounts ORDER BY id DESC; `
	
Output :
	
	+----+---------+
	| id | name    |
	+----+---------+
	| 10 | Shakil  |
	|  9 | Maruf   |
	|  8 | Minhaj  |
	|  7 | Alfi    |
	|  6 | Omi     |
	|  5 | Himu    |
	|  4 | Humayun |
	|  3 | Arman   |
	|  2 | Salman  |
	|  1 | Sohan   |
	+----+---------+
	   accounts
	   
## Limit : "LIMIT" clause is used in the "SELECT" statement to limit the number of rows returned by a query.

Syntex  : `SELECT  col_name
		FROM table_name LIMIT row_number;`

Example : `SELECT id,name FROM accounts ORDER BY id LIMIT 5; `

Output :

	+----+---------+
	| id | name    |
	+----+---------+
	|  1 | Sohan   |
	|  2 | Salman  |
	|  3 | Arman   |
	|  4 | Humayun |
	|  5 | Himu    |
	+----+---------+
	   accounts
## Where clause : "WHERE" clause is used in the "SELECT" statement to filter the results of a query based on one or more conditions.

Syntex : `SELECT col_name_1,col_name_2
		FROM table_name
			WHERE condition;`
			
Example : `SELECT id,amount
		FROM orders
			WHERE amount >5000;`
			
Before :

	+----+--------+
	| id | amount |
	+----+--------+
	|  1 |   1000 |
	|  2 |   2050 |
	|  3 |   5000 |
	|  4 |   1520 |
	|  5 |   2150 |
	|  6 |   9000 |
	|  7 |   1800 |
	|  8 |   5000 |
	|  9 |   1520 |
	| 10 |   2150 |
	| 11 |   8500 |
	| 12 |   1750 |
	| 13 |   1800 |
	| 14 |   5000 |
	| 15 |   6200 |
	| 16 |   2150 |
	| 17 |   8000 |
	| 18 |   3600 |
	+----+--------+
	   orders
After :

	+----+--------+
	| id | amount |
	+----+--------+
	|  6 |   9000 |
	| 11 |   8500 |
	| 15 |   6200 |
	| 17 |   8000 |
	+----+--------+
	   orders
	  
## Between : "BETWEEN" operator is used in the "WHERE" clause to retrieve rows that fall within a specified range of values.

Syntex : `SELECT col_name_1,col_name_2
		FROM table_name
			WHERE col_name BETWEEN condition;`
			
Example : `SELECT * 
		FROM orders 
			WHERE amount BETWEEN 1000  AND 3000;`
			
Output :

	+----+--------+-------------+
	| id | amount | customer_id |
	+----+--------+-------------+
	|  1 |   1000 |           2 |
	|  2 |   2050 |           4 |
	|  4 |   1520 |           1 |
	|  5 |   2150 |           4 |
	|  7 |   1800 |           1 |
	|  9 |   1520 |           8 |
	| 10 |   2150 |           5 |
	| 12 |   1750 |          10 |
	| 13 |   1800 |           1 |
	| 16 |   2150 |           5 |
	+----+--------+-------------+
		  orders 

## Logical Operator (AND , OR, NOT , IN) : logical operators are used to combine multiple conditions in the "WHERE" clause of a "SELECT" statement.


(AND) Example : `SELECT * 
		FROM orders 
			WHERE amount  = 2050  AND customer_id = 4;`
			
			
Output : 

	+----+--------+-------------+
	| id | amount | customer_id |
	+----+--------+-------------+
	|  2 |   2050 |           4 |
	+----+--------+-------------+
		orders
		
(OR) Example :  `SELECT * 
			FROM orders 
				WHERE amount  = 2050 OR  customer_id = 5;`
				
Output : 

	+----+--------+-------------+
	| id | amount | customer_id |
	+----+--------+-------------+
	|  2 |   2050 |           4 |
	| 10 |   2150 |           5 |
	| 16 |   2150 |           5 |
	+----+--------+-------------+
		 orders
		 
(NOT) Example : `SELECT * 
			FROM region 
				WHERE name  <> 'Dhaka';`
				
Before :

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	+----+------------+
	      region
	      
After :

	+----+------------+
	| id | name       |
	+----+------------+
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	+----+------------+
	      region

IN & NOT IN: 

(IN) 

Syntex : `SELECT col_name FROM 
	WHERE col_name IN (value1, value2)`

Example : `SELECT * FROM region WHERE name IN('dhaka','sylhet');`

Output :

	+----+--------+
	| id | name   |
	+----+--------+
	|  1 | Dhaka  |
	|  4 | Sylhet |
	+----+--------+
	    region 
(NOT IN ) 

Syntex : `SELECT col_name FROM 
	WHERE col_name NOT IN (value1, value2)`

Example : `SELECT * FROM region WHERE name NOT IN('dhaka','sylhet');`

Output :

	+----+------------+
	| id | name       |
	+----+------------+
	|  2 | Cumilla    |
	|  3 | Chittagong |
	+----+------------+
		region


## AS : "AS" is used to give an alias or a temporary name to a column.

Syntex : `SELECT col_name AS tamp_col_name 
		FROM table_name;`

Example : `SELECT name  AS district_name 
		FROM region;`
		
Output :

	+---------------+
	| district_name |
	+---------------+
	| Dhaka         |
	| Cumilla       |
	| Chittagong    |
	| Sylhet        |
	+---------------+
	    region
	    
## Alter table : "ALTER TABLE" statement allows to add, modify, or drop columns, constraints, and indexes.

ADD (column)  :

Syntex : `ALTER TABLE table_name
	 ADD col_name datatype[size];`
	 
Example : `ALTER TABLE accounts
    	 ADD email VARCHAR(30);`
	 
Output : 

	+----+---------+------+--------------+-------------+--------------+-------+
	| id | name    | age  | phone_number | password    | sales_rep_id | email |
	+----+---------+------+--------------+-------------+--------------+-------+
					accounts
Modify (column) :

Syntex : `ALTER TABLE table_name
	 CHANGE old_col_name  new_col_name datatype[size];`
	 
Example : `ALTER TABLE accounts  
	 CHANGE email  e_mail VARCHAR(30);`
	 
Output : 

	+----+---------+------+--------------+-------------+--------------+--------+
	| id | name    | age  | phone_number | password    | sales_rep_id | e_mail |
	+----+---------+------+--------------+-------------+--------------+--------+
					accounts
DROP (column) :

Syntex : `ALTER TABLE table_name
	 DROP col_name;`
	 
Example : `ALTER TABLE accounts
	  DROP e_mail;`
	 
Output : 

	+----+---------+------+--------------+-------------+--------------+
	| id | name    | age  | phone_number | password    | sales_rep_id |
	+----+---------+------+--------------+-------------+--------------+
					accounts
## Null & Not Null:

NULL :

Syntex : `SELECT * FROM table_name 
		WHERE col_name IS NULL;`

Example: `SELECT * FROM region WHERE name IS NULL;`
	
Output : 

	+----+------+
	| id | name |
	+----+------+
	|  5 | NULL |
	+----+------+
	   region
	   
NOT NULL :

Syntex : `SELECT * FROM table_name 
		WHERE col_name IS NOT NULL;`

Example: `SELECT * FROM region WHERE name IS NOT NULL;`
	
Output : 

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	+----+------------+
		region

## Update record :

Syntex : `UPDATE table_name
	 SET col_name = update_record
	 WHERE location/condition ;`
	 
Example : UPDATE region
    	  SET name = 'Noakhali'
    	  WHERE id = 5;
	  
Output : 

 Before  :
 
 	+----+------------+
	| id | name       |
	+----+------------+
	|  5 | NULL	  |
	+----+------------+
 		region
 
 After :
 
	+----+------------+
	| id | name       |
	+----+------------+
	|  5 | Noakhali   |
	+----+------------+
		region
		
## Search Record :

Syntex : `SELECT col_name FROM table_name
	 	WHERE col_name LIKE 'search_record' ; `
	 
Example : `SELECT * FROM accounts WHERE name  LIKE  'Omi'; `

Output :

	+----+------+------+--------------+----------+--------------+
	| id | name | age  | phone_number | password | sales_rep_id |
	+----+------+------+--------------+----------+--------------+
	|  6 | Omi  |   32 |        35405 | sfdgsdfg |         3302 |
	+----+------+------+--------------+----------+--------------+
				accounts
				
## Delete Record : 

Syntex :`DELETE FROM table_name
	 WHERE condition / location ;`
	 
Example :`DELETE FROM region WHERE id = 5; `

Output :

Before :

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	|  5 | Noakhali   |
	+----+------------+
	     region

After : 

	+----+------------+
	| id | name       |
	+----+------------+
	|  1 | Dhaka      |
	|  2 | Cumilla    |
	|  3 | Chittagong |
	|  4 | Sylhet     |
	+----+------------+
	      region
	      
## Function : 

SUM :

Syntex : `SELECT SUM(col_name) FROM table_name ;`

Example : `SELECT SUM(orders.amount) AS total_amount FROM orders;`

Output : 

	+--------------+
	| total_amount |
	+--------------+
	|        68190 |
	+--------------+
	     orders
	    
AVG : 

Syntex : `SELECT AVG(col_name) FROM table_name ;`

Example : `SELECT AVG(orders.amount) AS average_amount FROM orders;`

Output :

	+----------------+
	| average_amount |
	+----------------+
	|      3788.3333 |
	+----------------+
	     orders
	     
Count : 

Syntex : `SELECT COUNT(col_name) FROM table_name ;`

Example : `SELECT COUNT(orders.customer_id) AS total_orders FROM orders;`

Output :

	+--------------+
	| total_orders |
	+--------------+
	|           18 |
	+--------------+
	      orders

Upper/lower case :

Syntex : `SELECT UPPER / LOWER(col_name) FROM table_name ;`


Example : `SELECT UPPER(region.name),LOWER(region.name) FROM region; `

Output :

	+--------------------+--------------------+
	| UPPER(region.name) | LOWER(region.name) |
	+--------------------+--------------------+
	| DHAKA              | dhaka              |
	| CUMILLA            | cumilla            |
	| CHITTAGONG         | chittagong         |
	| SYLHET             | sylhet             |
	+--------------------+--------------------+
			region

Max/Min :

Syntex : `SELECT MAX / MIN(col_name) FROM table_name ;`


Example : `SELECT MAX(amount),MIN(amount) FROM orders;`

Output : 

	+-------------+-------------+
	| MAX(amount) | MIN(amount) |
	+-------------+-------------+
	|        9000 |        1000 |
	+-------------+-------------+
		 orders

## Sub Query :

Syntex : `SELECT column(s)
	  FROM table
	 WHERE column operator (SELECT column(s) FROM table WHERE condition);`
	 
Example : `SELECT orders.amount 
		FROM orders 
			WHERE amount > (SELECT AVG(orders.amount) FROM orders) ;`
			
Output : 

	+--------+
	| amount |
	+--------+
	|   5000 |
	|   9000 |
	|   5000 |
	|   8500 |
	|   5000 |
	|   6200 |
	|   8000 |
	+--------+
	  orders

Group Clause :

Syntex : `SELECT column_name, aggregate_function(column_name)
		FROM table_name
		WHERE condition
		GROUP BY column_name; `
	
Example : `SELECT orders.customer_id, SUM(orders.amount) FROM e_commerce.orders GROUP BY orders.customer_id;`

Output : 

	+-------------+--------------------+
	| customer_id | SUM(orders.amount) |
	+-------------+--------------------+
	|           1 |               5120 |
	|           2 |              22500 |
	|           4 |               4200 |
	|           5 |               4300 |
	|           6 |              10000 |
	|           7 |               9000 |
	|           8 |               7720 |
	|          10 |               5350 |
	+-------------+--------------------+
			orders
			
## Turncate : the TRUNCATE function is used to delete all rows from a table in a single command.

Syntex : `TRUNCATE TABLE table_name;`

Example : `TRUNCATE TABLE orders;`

Output : 

	+----+--------+-------------+
	| id | amount | customer_id |
	+----+--------+-------------+
		 orders 
		 
## Join (INNER ) : In an INNER JOIN, only the rows from both tables that match the join condition are returned in the result set. This means that any rows from one table that do not have a matching row in the other table are not included in the result set.

Syntex : `SELECT column_name(s)
	  FROM table1
	  INNER JOIN table2
	  ON table1.column_name = table2.column_name;`
	  
Example : `SELECT accounts.id , accounts.name , SUM(orders.amount) AS total_amount 
		FROM accounts INNER JOIN orders 
			ON orders.customer_id = accounts.id 
				GROUP BY accounts.id;`
				
Output : 

	+----+---------+--------------+
	| id | name    | total_amount |
	+----+---------+--------------+
	|  2 | Salman  |        22500 |
	|  4 | Humayun |         4200 |
	|  1 | Sohan   |         5120 |
	|  7 | Alfi    |         9000 |
	|  6 | Omi     |        10000 |
	|  8 | Minhaj  |         7720 |
	|  5 | Himu    |         4300 |
	| 10 | Shakil  |         5350 |
	+----+---------+--------------+
 
 ## Join (Left) : LEFT JOIN is a type of join in SQL that returns all the rows from the left table and matching rows from the right table. If there are no matching rows in the right table, NULL values are returned for all columns in the right table.
 
 Syntex : `SELECT column_name(s)
	FROM table1
		LEFT JOIN table2
			ON table1.column_name = table2.column_name;`
			
Example : `SELECT accounts.id , accounts.name , SUM(orders.amount) AS total_amount 
		FROM accounts LEFT JOIN orders 
			ON orders.customer_id = accounts.id 
				GROUP BY accounts.id;`
				
Output : 

	+----+---------+--------------+
	| id | name    | total_amount |
	+----+---------+--------------+
	|  1 | Sohan   |         5120 |
	|  2 | Salman  |        22500 |
	|  3 | Arman   |         NULL |
	|  4 | Humayun |         4200 |
	|  5 | Himu    |         4300 |
	|  6 | Omi     |        10000 |
	|  7 | Alfi    |         9000 |
	|  8 | Minhaj  |         7720 |
	|  9 | Maruf   |         NULL |
	| 10 | Shakil  |         5350 |
	+----+---------+--------------+
	
## join (Right) : RIGHT JOIN is a type of join in SQL that returns all the rows from the right table and matching rows from the left table. If there are no matching rows in the left table, NULL values are returned for all columns in the left table.

Syntex : `SELECT column_name(s)
		FROM table1
			RIGHT JOIN table2
				ON table1.column_name = table2.column_name;`
				
Example : `SELECT accounts.id , accounts.name , SUM(orders.amount) AS total_amount 
		FROM accounts RIGHT JOIN orders
			ON orders.customer_id = accounts.id 
				GROUP BY accounts.id;`


Output : 

	+------+---------+--------------+
	| id   | name    | total_amount |
	+------+---------+--------------+
	|    2 | Salman  |        22500 |
	|    4 | Humayun |         4200 |
	|    1 | Sohan   |         5120 |
	|    7 | Alfi    |         9000 |
	|    6 | Omi     |        10000 |
	|    8 | Minhaj  |         7720 |
	|    5 | Himu    |         4300 |
	|   10 | Shakil  |         5350 |
	+------+---------+--------------+


## Join (Natural) :  it joins the two tables based on columns with the same name in both tables.

Syntex : `SELECT *
		FROM orders
			NATURAL JOIN customers;`

 ## Joining 3 Tables : 
 
 Exercise : Find out the individual Sales representative's selling amount with the Sales representative name 
 	
	   ` SELECT MAX(sales_repos.id),MAX(sales_repos.name), SUM(e_commerce.orders.amount)
		FROM sales_repos LEFT JOIN accounts
			ON sales_repos.id = accounts.sales_rep_id
				JOIN orders
					ON orders.customer_id = accounts.id 
						GROUP BY accounts.sales_rep_id;`
						
Output : 

	+---------------------+-----------------------+-------------------------------+
	| MAX(sales_repos.id) | MAX(sales_repos.name) | SUM(e_commerce.orders.amount) |
	+---------------------+-----------------------+-------------------------------+
	|                3301 | Abul Kalam            |                         35700 |
	|                3302 | Rahim Ahmed           |                         14300 |
	|                3303 | Shanaj Akter          |                         13070 |
	|                3304 | Amit Deb              |                          5120 |
	+---------------------+-----------------------+-------------------------------+
 
## join 4 tables : 

 Exercise : Find out the individual Sales representative's selling amount with the Sales representative name and region name
 
 	`SELECT MAX(sales_repos.id),MAX(sales_repos.name), SUM(e_commerce.orders.amount), MAX(region.name)
 		FROM sales_repos 
	LEFT JOIN accounts
		ON sales_repos.id = accounts.sales_rep_id
	JOIN orders
		ON orders.customer_id = accounts.id
	JOIN region
		ON sales_repos.region_id = region.id
	GROUP BY accounts.sales_rep_id
		LIMIT 0,1000;`
		
Output : 

	+---------------------+-----------------------+-------------------------------+------------------+
	| MAX(sales_repos.id) | MAX(sales_repos.name) | SUM(e_commerce.orders.amount) | max(region.name) |
	+---------------------+-----------------------+-------------------------------+------------------+
	|                3301 | Abul Kalam            |                         35700 | Dhaka            |
	|                3302 | Rahim Ahmed           |                         14300 | Cumilla          |
	|                3303 | Shanaj Akter          |                         13070 | Chittagong       |
	|                3304 | Amit Deb              |                          5120 | Sylhet           |
	+---------------------+-----------------------+-------------------------------+------------------+
	

 
