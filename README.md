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

##  ER Diagram

     C:\Users\thuma\Downloads\A_PDF_document_titled__Online_Retail_Application_D.png
