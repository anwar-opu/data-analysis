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

## Data Insert  for all table [e_commerce data insert.txt](https://github.com/anwar-opu/data-analysis/files/10790244/e_commerce.data.insert.txt)

# Show table (all) :

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
                
 ## Rename Table :
 
  Syntex : RENAME TABLE old_table_name TO new_table_name;
  
  example : RENAME TABLE accounts TO account;
  
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
                       accounts                
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
                       account
