create database customers;
use customers;
#q1
create table customers(
customerid int primary key auto_increment,
name varchar(100),
email varchar(100),
address  varchar(255)
);

#1
 INSERT INTO customers (name, email, address) VALUES 
('Alice Smith', 'alice@example.com', '123 Maple St'),
('Bob Johnson', 'bob@example.com', '456 Oak Ave'),
('Alice Brown', 'abrown@example.com', '789 Pine Rd'),
('Charlie Davis', 'charlie@example.com', '321 Elm St'),
('Diana Prince', 'diana@example.com', '555 Amazon Blvd');

#2
select * from customers;

#3
update customers set address='999 New Skyline' where customerid=1;

#4 
DELETE FROM Customers 
WHERE CustomerID = 4;

#5
select * from customers where name like 'Alice%';

#q2

create table orders(
orderid int primary key auto_increment,
customerid int,
orderdate date,
totalamount decimal(10,2),
foreign key (customerid) references customers(customerid)
);

#1
insert into orders (customerid, orderdate, totalamount) VALUES 
(1, '2026-01-20', 150.50),
(1, '2026-02-10', 85.00),
(2, '2026-02-01', 210.00),
(3, '2026-02-14', 45.25),
(5, '2026-02-15', 300.00);

#2
select * from orders;

#3
update orders set totalamount=175.00 where orderid=2;

#4
delete from orders where orderid = 4;

#6
select 
max(totalamount) as highestamount,
min(totalamount) as highestamount,
avg(totalamount) as highestamount 
from orders;

create table product(
productid int primary key,
productname varchar(50),
price decimal(10,2),
stock int
);

#1
insert into product(productid, productname, price, stock) VALUES
(1, 'Laptop', 55000, 10),
(2, 'Mouse', 450, 50),
(3, 'Keyboard', 1200, 0),
(4, 'Monitor', 8500, 15),
(5, 'USB Cable', 600, 100);

#2
select * from product;

#3
update product set price = 52000 
WHERE productid = 1;

#4
delete from product where stock = 0;

#5
SELECT * FROM product 
WHERE Price BETWEEN 500 AND 2000;

#6
select max(price) AS MostExpensive, min(price) AS Cheapest 
from Product;

#q4
SELECT * FROM Orders WHERE CustomerID = 1;

UPDATE Orders SET TotalAmount = 550.00 WHERE OrderID = 1;
SELECT SUM(SubTotal) AS TotalRevenue FROM OrderDetails;
SELECT ProductID, SUM(Quantity) AS TotalQty 
FROM OrderDetails 
GROUP BY ProductID 
ORDER BY TotalQty DESC 
LIMIT 3;


SELECT COUNT(*) FROM OrderDetails WHERE ProductID = 2;
