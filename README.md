# java-rdbms

## SQL
## RDBMS
## PostgreSQL

# Introduction

The Northwind database was original developed by Microsoft to show case the abilities of MS Access. The database has grown and been adapted to where now it is the defacto database used to introduce SQL and database management systems.

# Instructions

Import the Northwind.db database into PostgreSQL using pgAdmin

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

SELECT companyname, contactname, contacttitle  
FROM customers  
~~~
## SQL Where
~~~
SELECT companyname, contactname, country  
FROM customers  
WHERE country = "Sweden"  

SELECT productname, unitsinstock  
FROM products  
WHERE unitsinstock < 10  
~~~
## SELECT order by
~~~
SELECT companyname, contactname, city, country  
FROM customers  
ORDER BY companyname DESC  

SELECT companyname, contactname, city, country  
FROM customers  
ORDER BY country DESC, city  
 
SELECT companyname, contactname, city, country  
FROM customers  
WHERE country in ('USA', 'Japan', 'Germany')  
ORDER BY country DESC, city  
~~~
## SQL Select Limit
~~~
SELECT productid, productname, unitprice  
FROM products  
ORDER BY unitprice  
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
SELECT MIN(unitprice)  
FROM products  

SELECT *  
FROM products  
WHERE unitprice =  
 (SELECT MAX(unitprice)  
  FROM products)  
~~~
## SQL Count, Sum, Avg
~~~
SELECT count(*)  
FROM products  

SELECT count(DISTINCT unitprice)  
FROM products  

SELECT quantityperunit, count(*)  
FROM products  
GROUP BY quantityperunit  
~~~
## SQL And, Or, Not
~~~
SELECT *  
FROM employees  
WHERE firstname = ‘Anne’ AND lastname = ‘Dodsworth’  

SELECT companyname, city, country  
FROM customers  
WHERE NOT country = 'USA'  
~~~
## SQL Between
~~~
SELECT productid, productname, unitprice  
FROM products  
WHERE unitprice between 10 and 20  
~~~
## SQL In
~~~
SELECT companyname, contactname, city, country  
FROM suppliers  
WHERE upper(country) in ('USA', 'CANADA', 'MEXICO')  

SELECT companyname, contactname, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  
~~~
## SQL Like
~~~
// all products starting with C  
SELECT productname  
FROM products  
WHERE productname LIKE 'C%'  
~~~
## SQL is Null
~~~
// no homepage  
SELECT companyname, contactname, homepage  
FROM suppliers  
WHERE homepage is NULL  

// has homepage  
SELECT companyname, contactname, homepage  
FROM suppliers  
WHERE homepage is NOT NULL  
~~~
## SQL Having
~~~
// countries with 10 or more customers  
SELECT count(customerid), country  
FROM customers  
GROUP BY country  
HAVING count(customerid) > 10  
~~~
## SQL Alias
~~~
SELECT COUNT(c.customerid) as TotalCustomers, c.country as Nation  
FROM customers c  
GROUP BY c.country  
ORDER by TotalCustomers  
~~~
## SQL Join
~~~
// inner join - select records that match in BOTH tables  
// includes those customers with orders and  
// only those orders with customers  

SELECT o.OrderDate, c.CompanyName, c.ContactName  
FROM orders o JOIN customers c  
on o.CustomerID = c.CustomerID  

SELECT o.OrderDate, c.CompanyName, c.ContactName  
FROM orders o, customers c  
WHERE o.CustomerID = c.CustomerID  
~~~
## SQL Left Join
~~~
// Left join - select all records from the left   
// table getting the data from the right table where available.  

// includes all customers and if available their order data  

SELECT o.OrderDate, c.CompanyName, c.ContactName  
FROM customers c LEFT JOIN orders o  
ON o.CustomerID = c.CustomerID  
ORDER BY o.OrderDate  
~~~
## SQL Right Join
~~~
// Right join - select all records from the right table  
// getting the data from the left table where available.  

SELECT o.OrderDate, c.CompanyName, c.ContactName  
FROM customers c RIGHT JOIN orders o  
ON o.CustomerID = c.CustomerID  
ORDER BY o.OrderDate  
~~~
## SQL Full Join
~~~
// Full Join - select all records from both tables joining the  
// data as appropriate.  

SELECT o.OrderDate, c.CompanyName, c.ContactName
FROM customers c FULL INNER JOIN orders o
ON o.CustomerID = c.CustomerID
ORDER BY o.OrderDate
~~~
## SQL Self Join
~~~
// match customers from the same country and city  
SELECT companyname, contactname, city, country  
FROM customers a, customers b  
WHERE a.CustomerID <> b.CustomerID  
  AND a.City = b.City  
  AND a.Country = b.Country  
ORDER BY a.country, a.city  
~~~
## SQL Union
~~~
SELECT companyname, contactname, phone  
FROM customers  
UNION   
SELECT 'Northwind', firstname + ' ' + lastname, homephone  
FROM employees  
ORDER BY companyname  
~~~
## SQL Subquery
~~~
SELECT companyname, contactname, city, country  
FROM customers  
WHERE country IN  
    (SELECT country  
     FROM suppliers)  

SELECT contactname, phone,   
       (SELECT COUNT(o.orderid)   
        FROM orders o   
        WHERE o.customerid = c.customerid) as ordercount  
FROM customers c  
ORDER BY ordercount  
~~~
## SQL Exists
~~~
// list all suppliers who have products with less than 10 units in stock  
SELECT companyname  
FROM suppliers    
WHERE EXISTS  
 (SELECT productname  
  FROM products  
  WHERE supplierid = suppliers.SupplierID  
  AND unitsinstock < 10)  
~~~
## SQL Insert
~~~
INSERT INTO customers(customerid, companyname, contactname)  
VALUES (9191, 'Lambda School', 'John Mitchell’)  

INSERT INTO customers(customerid, companyname, contactname)  
SELECT 9192, companyname, contactname  
FROM suppliers  
WHERE companyname LIKE 'BIG%'  
~~~
## SQL Update
~~~
// discontinuing all products with unit price < 10.00  
UPDATE products  
SET discontinued = 1  
WHERE unitprice < 10.00  

UPDATE suppliers  
SET City = 'Oslo', Phone = '(0)1-953530', Fax = '(0)1-953555'  
WHERE supplierid = 15  
~~~
## SQL Delete
~~~
DELETE   
FROM products  
WHERE unitprice < 10.00  

DELETE   
FROM customers  
WHERE customerid = 15  

