# SQL Joins : Natural, equi and outer joins
## 1.Natural join to retrieve orders with customer details
```mysql
SELECT order.order_id, order.order_date, order.total_amount, order.status, customer.name AS customer_name FROM order NATURAL JOIN customer;
```
## 2.Equi join to retrive menu and their prices for a specific cafe
```mysql
SELECT menu.item_name, menu.price FROM menu JOIN cafe ON menu.cafe_id=cafe.cafe_id WHERE cafe.name='cafe A';
```
## 3.Left outer join to retrieve all cafes and their orders( Including cafes without orders)
```mysql
SELECT cafe.name, order>order_id, order.order_date, order.total_amount, order.status FROM cafe LEFT JOIN ordeer ON cafe.cafe_id=order.cafe_id; 
```
## 4.Right Outer Join to retrive all employees and their associated cafes ( including employee without cafes)
```mysql
SELECT employee.name, employee.position, cafe.name AS cafe_name FROM employee RIGHT JOIN cafe ON employee.cafe_id=cafe.cafe_id;
```
## 5.self join to retrieve ordes from the same cafe with different customers
```mysql
SELECT o1.order_id, o1.customer_id AS customer_id_1, o2.customer_id AS customer_id_2 FROM order1 AS o1 JOIN order2 AS o2 ON o1.cafe_id=o2.cafe_id AND o1.order_id <> o2.order_id;
```
## 6.Cross join to retrieve all combinations of cafe and menu items
```mysql
SELECT cafe.name AS cafe_name, menu.item_name FROM cafe CROSS JOIN menu;
```
## 7.Inner join with Multiple conditions to retrieve employees and their associates cafes with a specific position
```mysql
SELECT employee.name, employee.position, cafe.name AS cafe_name FROM employee INNER JOIN cafe ON employee.cafe_id=cafe.cafe_id WHERE employee.position='Barista';
```
## 8.Left Outer join with Aggrigation to find cafes and their total order amounts
```mysql
SELECT cafe.name, SUM(order.total_amount) AS total_order_amount FROM cafe LEFT OUTER JOIN order ON cafe.cafe_id=order.cafe_id GROUP BY cafe.name;
```
