#  Online Retail Application Database

This project demonstrates the design and implementation of a **relational database** system for an **Online Retail Application**. It covers everything from schema design, SQL implementation, to sample queries for managing products, customers, orders, and payments.

---

##  Table of Contents
- [Project Overview](#project-overview)
- [Database Schema](#database-schema)
- [ER Diagram](#er-diagram)
- [SQL Scripts](#sql-scripts)
  - [Create Tables](#create-tables)
  - [Insert Sample Data](#insert-sample-data)
  - [Query Examples](#query-examples)
- [Normalization](#normalization)
- [Future Enhancements](#future-enhancements)
- [Screenshots](#screenshots)

---

##  Project Overview

The goal is to create a normalized and structured relational database for an online retail system with the following objectives:

- Manage **products, categories, customers, orders, and payments**.
- Maintain **referential integrity** through foreign key constraints.
- Perform **SQL operations** for inserting, updating, deleting, and querying data.

---

##  Database Schema

- `Categories(category_id, category_name)`
- `Products(product_id, product_name, price, quantity_in_stock, category_id)`
- `Customers(customer_id, name, email, phone)`
- `Orders(order_id, customer_id, order_date, status)`
- `OrderDetails(order_detail_id, order_id, product_id, quantity, subtotal)`
- `Payments(payment_id, order_id, payment_date, amount_paid, method)`

---

##  Database Design
![Database Design](https://github.com/ThumatiTeja/sql-major-project/blob/main/A_PDF_document_titled__Online_Retail_Application_D.png)

---

##  SQL Scripts

###  Create Tables

```sql
CREATE TABLE Categories (
    category_id INT PRIMARY KEY,
    category_name VARCHAR(100) NOT NULL
);

CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    quantity_in_stock INT NOT NULL,
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES Categories(category_id)
);

CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100),
    phone VARCHAR(15)
);

CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    status VARCHAR(50),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE OrderDetails (
    order_detail_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    subtotal DECIMAL(10,2),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);

CREATE TABLE Payments (
    payment_id INT PRIMARY KEY,
    order_id INT,
    payment_date DATE,
    amount_paid DECIMAL(10,2),
    method VARCHAR(50),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id)
);
```

---

### Sample Data

---
Categories
```sql
INSERT INTO Categories VALUES (1, 'Electronics'), (2, 'Books');
```

 Products
 ```sql
INSERT INTO Products VALUES 
(101, 'Laptop', 70000, 50, 1),
(102, 'Smartphone', 30000, 100, 1),
(103, 'Fiction Book', 500, 200, 2);
```
Customers
```sql
INSERT INTO Customers VALUES 
(1, 'Ravi Kumar', 'ravi@mail.com', '9876543210');
```

Orders
 ```sql
INSERT INTO Orders VALUES 
(201, 1, '2025-06-10', 'Shipped');
```
Order Details
```sql
INSERT INTO OrderDetails VALUES 
(301, 201, 101, 1, 70000);
```
Payments
 ```sql
INSERT INTO Payments VALUES 
(401, 201, '2025-06-11', 70000, 'Credit Card');

```
---
## Key SQL Queries
List all products in stock
```sql
SELECT product_name, price FROM Products WHERE quantity_in_stock > 0;
```
--- 
Get customer orders
```sql
SELECT o.order_id, c.name, o.order_date 
FROM Orders o
JOIN Customers c ON o.customer_id = c.customer_id;
```
--- 
Total order cost
```sql
SELECT order_id, SUM(subtotal) AS total_amount
FROM OrderDetails
GROUP BY order_id;
```
---
Full order details
```sql
SELECT c.name, p.product_name, od.quantity, od.subtotal
FROM OrderDetails od
JOIN Orders o ON od.order_id = o.order_id
JOIN Products p ON od.product_id = p.product_id
JOIN Customers c ON o.customer_id = c.customer_id;
```
---

# Conclusion
The development of the Online Retail Application Database demonstrates the importance of structured data management in modern e-commerce platforms. The use of SQL and relational schema design enables efficient handling of transactions, customer information, inventory control, and billing.

By completing this project, we gain practical experience in:

- Designing ER diagrams and relational databases

- Writing efficient and reliable SQL scripts

- Understanding real-world data relationships in e-commerce systems

This project not only reinforces core database concepts but also serves as a ready-to-integrate backend system for future frontend development. It is a scalable solution suitable for academic demonstration and real-world application in the retail domain.
