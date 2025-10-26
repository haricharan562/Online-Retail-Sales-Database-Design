# Online-Retail-Sales-Database-Design
This project focuses on designing a normalized SQL database for an online retail (e-commerce) platform. It includes complete database design steps — from entity identification and ER diagram creation to normalization (up to 3NF), SQL schema generation, sample data insertion, and analytical queries for sales reports. 
Table Customers {
  CustomerID int [pk, increment]
  Name varchar(100)
  Email varchar(100) [unique]
  City varchar(50)
}

Table Products {
  ProductID int [pk, increment]
  ProductName varchar(100)
  Category varchar(50)
  Price decimal(10,2)
}

Table Orders {
  OrderID int [pk, increment]
  CustomerID int [ref: > Customers.CustomerID]
  OrderDate date
}

Table OrderDetails {
  OrderDetailID int [pk, increment]
  OrderID int [ref: > Orders.OrderID]
  ProductID int [ref: > Products.ProductID]
  Quantity int
}

Table Payments {
  PaymentID int [pk, increment]
  OrderID int [ref: > Orders.OrderID]
  PaymentDate date
  Amount decimal(10,2)
  Method varchar(30)
}

Ref: Orders.CustomerID > Customers.CustomerID
Ref: OrderDetails.OrderID > Orders.OrderID
Ref: OrderDetails.ProductID > Products.ProductID
Ref: Payments.OrderID > Orders.OrderID
