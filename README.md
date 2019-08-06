# java-rdbms

* SQL
* RDBMS
* PostgreSQL

# Introduction

The Northwind database was original developed by Microsoft to show case the abilities of MS Access. The database has grown and been adapted to where now it is the defacto database used to introduce SQL and database management systems.

# Instructions

Import the Northwind database into PostgreSQL using pgAdmin

clone https://github.com/pthom/northwind_psql.git

## pgAdmin

* Right Click Databases
  * Create
    * type in northwind

* Tools -> Query Tool
  * Open file northwind.sql (from cloned repo)
  * Execute

* Look under
  * northwind -> Schemas -> public -> tables

* Clear query windows

## SQL Syntax Overview
~~~
SELECT <fields>  
FROM <TABLES>  
WHERE <criteria>  
ORDER BY <order>  

INSERT <table> (<fields>)  
VALUES (<data>)  

UPDATE <table>  
SET <field> = <data>  
WHERE <criteria>  

DELETE <table>  
WHERE <criteria>  
~~~
## SQL Select
~~~
SELECT *  
FROM customers  

SELECT company_name, contact_name, contact_title  
FROM customers  
~~~
## SQL Where
~~~
SELECT company_name, contact_name, country  
FROM customers  
WHERE country = 'Sweden'

SELECT product_name, units_in_stock  
FROM products  
WHERE units_in_stock < 10  
~~~
## SELECT order by
~~~
SELECT company_name, contact_name, city, country  
FROM customers  
ORDER BY company_name DESC  

SELECT company_name, contact_name, city, country  
FROM customers  
ORDER BY country DESC, city  
 
SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country in ('USA', 'Japan', 'Germany')  
ORDER BY country DESC, city  
~~~
## SQL Select Limit
~~~
SELECT product_id, product_name, unit_price  
FROM products  
ORDER BY unit_price  
LIMIT 5  
~~~
## SQL Select Distinct
~~~
SELECT DISTINCT country  
FROM customers  
ORDER BY country  
~~~
## SQL Min, Max
~~~
SELECT MIN(unit_price)  
FROM products  

SELECT *  
FROM products  
WHERE unit_price =  
 (SELECT MAX(unit_price)  
  FROM products)  
~~~
## SQL Count, Sum, Avg
~~~
SELECT count(*)  
FROM products  

SELECT count(DISTINCT unit_price)  
FROM products  

SELECT quantity_per_unit, count(*)  
FROM products  
GROUP BY quantity_per_unit  
~~~
## SQL And, Or, Not
~~~
SELECT *  
FROM employees  
WHERE first_name = 'Anne' AND last_name = 'Dodsworth'  

SELECT company_name, city, country  
FROM customers  
WHERE NOT country = 'USA'  
~~~
## SQL Between
~~~
SELECT product_id, product_name, unit_price  
FROM products  
WHERE unit_price between 10 and 20  
~~~
## SQL In
~~~
SELECT company_name, contact_name, city, country  
FROM suppliers  
WHERE upper(country) in ('USA', 'CANADA', 'MEXICO')  

SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  
~~~
## SQL Like
~~~
// all products starting with C  
SELECT product_name  
FROM products  
WHERE product_name LIKE 'C%'  
~~~
## SQL is Null
~~~
// no homepage  
SELECT company_name, contact_name, homepage  
FROM suppliers  
WHERE homepage is NULL  

// has homepage  
SELECT company_name, contact_name, homepage  
FROM suppliers  
WHERE homepage is NOT NULL  
~~~
## SQL Having
~~~
// countries with 10 or more customers  
SELECT count(customer_id), country  
FROM customers  
GROUP BY country  
HAVING count(customer_id) > 10  
~~~
## SQL Alias
~~~
SELECT COUNT(c.customer_id) as TotalCustomers, c.country as Nation  
FROM customers c  
GROUP BY c.country  
ORDER by TotalCustomers  
~~~
## SQL Join
~~~
// inner join - select records that match in BOTH tables  
// includes those customers with orders and  
// only those orders with customers  

SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM orders o JOIN customers c  
on o.Customer_ID = c.Customer_ID  

SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM orders o, customers c  
WHERE o.Customer_ID = c.Customer_ID  
~~~
## SQL Left Join
~~~
// Left join - select all records from the left   
// table getting the data from the right table where available.  

// includes all customers and if available their order data  

SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM customers c LEFT JOIN orders o  
ON o.Customer_ID = c.Customer_ID  
ORDER BY o.Order_Date  
~~~
## SQL Right Join
~~~
// Right join - select all records from the right table  
// getting the data from the left table where available.  

SELECT o.Order_Date, c.Company_Name, c.Contact_Name  
FROM customers c RIGHT JOIN orders o  
ON o.Customer_ID = c.Customer_ID  
ORDER BY o.Order_Date  
~~~
## SQL Full Join
~~~
// Full Join - select all records from both tables joining the  
// data as appropriate.  

SELECT o.Order_Date, c.Company_Name, c.Contact_Name
FROM customers c INNER JOIN orders o
ON o.Customer_ID = c.Customer_ID
ORDER BY o.Order_Date

http://www.postgresqltutorial.com/postgresql-joins/

~~~
## SQL Self Join
~~~
// match customers from the same country and city  
SELECT a.company_name, a.contact_name, a.city, a.country  
FROM customers a, customers b  
WHERE a.Customer_ID <> b.Customer_ID  
  AND a.City = b.City  
  AND a.Country = b.Country  
ORDER BY a.country, a.city  
~~~
## SQL Union
~~~
SELECT company_name, contact_name, phone  
FROM customers  
UNION   
SELECT 'Northwind', CONCAT(first_name, ' ', last_name), home_phone  
FROM employees  
ORDER BY company_name 
~~~
## SQL Subquery
~~~
SELECT company_name, contact_name, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  

SELECT contact_name, phone,   
       (SELECT COUNT(o.order_id)   
        FROM orders o   
        WHERE o.customer_id = c.customer_id) as ordercount  
FROM customers c  
ORDER BY ordercount  
~~~
## SQL Exists
~~~
// list all suppliers who have products with less than 10 units in stock  
SELECT company_name  
FROM suppliers    
WHERE EXISTS  
 (SELECT product_name  
  FROM products  
  WHERE supplier_id = suppliers.Supplier_ID  
  AND units_in_stock < 10)  
~~~
## SQL Insert
~~~
INSERT INTO customers(customer_id, company_name, contact_name)  
VALUES (9191, 'Lambda School', 'John Mitchell')  

INSERT INTO customers(customer_id, company_name, contact_name)  
SELECT 9192, company_name, contact_name  
FROM suppliers  
WHERE company_name LIKE 'BIG%'  
~~~
## SQL Update
~~~
// discontinuing all products with unit price < 10.00  
UPDATE products  
SET discontinued = 1  
WHERE unit_price < 10.00  

UPDATE suppliers  
SET City = 'Oslo', Phone = '(0)1-953530', Fax = '(0)1-953555'  
WHERE supplier_id = 15  
~~~
## SQL Delete
~~~
DELETE   
FROM products  
WHERE unit_price < 10.00  

DELETE   
FROM customers  
WHERE customer_id = '15'  
~~~

# Data Normalization

<details><summary>Original Data</summary>

<p>

Data Table

| First name | Last Name | Full Name     | email                  | company name      | company tax id |
|------------|-----------|---------------|------------------------|-------------------|----------------|
| John       | Mitchell  | John Mitchell | john@lambdaschool.com, | Lambda School     | 99-999999      | 
|            |           |               | jrmmba@outlook.com,    |                   |                |
|            |           |               | jrmmba8314@gmail.com   |                   |                |
| Steve      | Green     | Steve Green   | steve@email.local      | Home              | 88-888888      |
| Amy        | Found     | Amy Found     | amy@email.local        | A Perfect Company | 77-777777      |
|            |           |               | afound@home.email      |                   |                |    

</p>
</details>



<details><summary>1NF - Email broken into separate rows</summary>
<p>

Person Table

| Person Id  |First name | Last Name | Full Name     |  company name      | company tax id |
|------------|-----------|-----------|---------------|--------------------|----------------|
| 1          | John      | Mitchell  | John Mitchell |  Lambda School     | 99-999999      | 
| 2          | Steve     | Green     | Steve Green   |  Home              | 88-888888      |
| 3          | Amy       | Found     | Amy Found     |  A Perfect Company | 77-777777      |



Email Table

| Email id | Person id | email                 |
|----------|-----------|-----------------------|
| 1        | 1         | john@lambdaschool.com |
| 2        | 1         | jrmmba@outlook.com    |
| 3        | 1         | jrmmba8314@gmail.com  |
| 4        | 2         | steve@email.local     |
| 5        | 3         | amy@email.local       |
| 6        | 3         | afound@home.email     |



</p>
</details>


<details><summary>2NF - Company Tax Id is moved to company table</summary>
<p>

Person Table

| Person Id  |First name | Last Name | Full Name     |  company id |
|------------|-----------|-----------|---------------|-------------|
| 1          | John      | Mitchell  | John Mitchell |  1          | 
| 2          | Steve     | Green     | Steve Green   |  2          |
| 3          | Amy       | Found     | Amy Found     |  3          |



Company Table

| Company Id | Company Name      | Company Tax Id |
|------------|-------------------|----------------|
| 1          | Lambda School     | 99-999999      |
| 2          | Home              | 88-888888      |
| 3          | A Perfect Company | 77-777777      |



Email Table

| Email id | Person id | email                 |
|----------|-----------|-----------------------|
| 1        | 1         | john@lambdaschool.com |
| 2        | 1         | jrmmba@outlook.com    |
| 3        | 1         | jrmmba8314@gmail.com  |
| 4        | 2         | steve@email.local     |
| 5        | 3         | amy@email.local       |
| 6        | 3         | afound@home.email     |



</p>
</details>

<details><summary>3NF - Derived column Full Name is removed</summary>
<p>

Person Table

| Person Id  |First name | Last Name | company id |
|------------|-----------|-----------|------------|
| 1          | John      | Mitchell  | 1          | 
| 2          | Steve     | Green     | 2          |
| 3          | Amy       | Found     | 3          |



Company Table

| Company Id | Company Name      | Company Tax Id |
|------------|-------------------|----------------|
| 1          | Lambda School     | 99-999999      |
| 2          | Home              | 88-888888      |
| 3          | A Perfect Company | 77-777777      |



Email Table

| Email id | Person id | email                 |
|----------|-----------|-----------------------|
| 1        | 1         | john@lambdaschool.com |
| 2        | 1         | jrmmba@outlook.com    |
| 3        | 1         | jrmmba8314@gmail.com  |
| 4        | 2         | steve@email.local     |
| 5        | 3         | amy@email.local       |
| 6        | 3         | afound@home.email     |


</p>
</details>
