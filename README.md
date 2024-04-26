You have been hired to design and implement a database system for Shoals Woodcraft (SW) - a small company that manufactures high-quality wood and epoxy tables. SW uses premium walnut wood slabs to handcraft tables that are beautiful and functional. SW custom builds tables for their clients and offers three different packages.

Large - 4 ft by 12 ft table ($20,000)

Medium - 4 ft by 8 foot table ($15,000)

Small - 4 ft by 4 foot table ($10,000)  

Currently, SW has a 12 month waiting list for new clients. SW needs to be able to track customer order information including the product ordered, when the order is placed, and expected delivery. They also need to be able to generate an invoice for the customer that includes sales tax (use 9%) and shipping costs (you can make this up).

In part one, create a detailed ERD of your design using LucidChart.

[ My Database ] 
![image](https://github.com/ConnorLBrown/ShoalsWoodWork-Database/assets/122556149/77d6536c-c137-4f67-9210-080b8d5fbb2d)


Create the database you designed in Part 1 including appropriate constraints. Add data to each table for at least 3 purchases including you as one customer. Execute queries on each table to display all the data. Create a document with the queries and results 

RESULTS:
mysql> describe customer;
+-------+-------------+------+-----+---------+----------------+
| Field | Type        | Null | Key | Default | Extra          |
+-------+-------------+------+-----+---------+----------------+
| cid   | int         | NO   | PRI | NULL    | auto_increment |
| fname | varchar(30) | YES  |     | NULL    |                |
| lname | varchar(30) | YES  |     | NULL    |                |
| email | varchar(30) | YES  |     | NULL    |                |
| phone | varchar(30) | YES  |     | NULL    |                |
+-------+-------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> select * from customer;
+-----+--------+---------+------------+--------------------+
| cid | fname  | lname   | email      | phone              |
+-----+--------+---------+------------+--------------------+
|   1 | Connor | Brown   | 2563662438 | cbrown30@una.edu   |
|   2 | James  | Madison | 2563661212 | jmadison@gmail.com |
|   3 | Larry  | Byrd    | 2567403215 | Lbyrd@yahoo.com    |
+-----+--------+---------+------------+--------------------+
3 rows in set (0.00 sec)

mysql> describe tax;
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| tid   | int          | NO   | PRI | NULL    |       |
| tax   | decimal(3,2) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
2 rows in set (0.00 sec)

mysql> describe invoice;
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| oid      | int          | NO   | PRI | NULL    |       |
| date     | int          | YES  |     | NULL    |       |
| shipping | decimal(5,2) | YES  |     | NULL    |       |
| cid      | int          | YES  | MUL | NULL    |       |
| tid      | int          | YES  | MUL | NULL    |       |
| pid      | int          | YES  | MUL | NULL    |       |
+----------+--------------+------+-----+---------+-------+
6 rows in set (0.00 sec)

mysql> select * from invoice;
+-----+------+----------+------+------+------+
| oid | date | shipping | cid  | tid  | pid  |
+-----+------+----------+------+------+------+
|   1 | 2011 |   400.25 | NULL | NULL | NULL |
|   2 | 2015 |   300.25 | NULL | NULL | NULL |
|   3 | 2017 |   200.25 | NULL | NULL | NULL |
+-----+------+----------+------+------+------+
3 rows in set (0.00 sec)

mysql> describe productorder;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| pid     | int         | YES  |     | NULL    |       |
| oid     | int         | YES  |     | NULL    |       |
| quanity | int         | YES  |     | NULL    |       |
| type    | varchar(50) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> describe productorder;select * from productorder;
+---------+-------------+------+-----+---------+-------+
| Field   | Type        | Null | Key | Default | Extra |
+---------+-------------+------+-----+---------+-------+
| pid     | int         | YES  |     | NULL    |       |
| oid     | int         | YES  |     | NULL    |       |
| quanity | int         | YES  |     | NULL    |       |
| type    | varchar(50) | YES  |     | NULL    |       |
+---------+-------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

+------+------+---------+---------------+
| pid  | oid  | quanity | type          |
+------+------+---------+---------------+
|    1 |    1 |       3 | Large         |
| NULL | NULL |       2 | small tables  |
| NULL | NULL |       4 | medium tables |
+------+------+---------+---------------+
3 rows in set (0.00 sec)

mysql> describe products;
+--------+-------------+------+-----+---------+----------------+
| Field  | Type        | Null | Key | Default | Extra          |
+--------+-------------+------+-----+---------+----------------+
| pid    | int         | NO   | PRI | NULL    | auto_increment |
| large  | varchar(50) | YES  |     | NULL    |                |
| medium | varchar(50) | YES  |     | NULL    |                |
| small  | varchar(50) | YES  |     | NULL    |                |
+--------+-------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)

mysql> select * from products;
+-----+-------------------------------+---------------------------------+---------------------------------+
| pid | large                         | medium                          | small                           |
+-----+-------------------------------+---------------------------------+---------------------------------+
|   1 | 4 ft by 12 ft table ($20,000) |  4 ft by 8 foot table ($15,000) |  4 ft by 4 foot table ($10,000) |
+-----+-------------------------------+---------------------------------+---------------------------------+
1 row in set (0.00 sec)




