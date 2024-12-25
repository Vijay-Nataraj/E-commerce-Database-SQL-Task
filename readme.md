# E-commerce System Database

This repository contains SQL scripts to create a simple e-commerce system database. The database includes tables for managing customers, orders, products, and order items and provides useful queries to interact with the system.

## Table of Contents

- [Getting Started](#getting-started)
- [Setup Instructions](#setup-instructions)
- [Database Structure](#database-structure)
- [Sample Data](#sample-data)
- [Queries](#queries)
- [Contributing](#contributing)

## Getting Started

Follow the instructions below to set up the e-commerce database on your local system.

## Setup Instructions

1. **Clone the Repository**

   Clone the repository to your local machine:

   ```bash
       git clone https://github.com/Vijay-Nataraj/E-commerce-Database-SQL-Task.git
       cd E-commerce-Database-SQL-Task
   ```

2. **Create the Database**

   Create a new database in your SQL environment:

   ```sql
       CREATE DATABASE ecommerce;
   ```

3. **Use the Database**

   Switch to the newly created database:

   ```sql
       USE ecommerce;
   ```

4. **Run the SQL Scripts**

Execute the SQL scripts provided in this repository to create tables and insert sample data.

## Database Structure

The database consists of the following tables:

- **customers**: Stores customer information.
- **products**: Stores product details.
- **orders**: Stores order information linked to customers.
- **order_items**: Stores details of products in each order.

### Table Definitions

1. **Customers Table**

   ```sql
   CREATE TABLE customers (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL,
       email VARCHAR(255) NOT NULL UNIQUE,
       address VARCHAR(255) NOT NULL
   );
   ```

2. **Products Table**

   ```sql
   CREATE TABLE customers (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL,
       email VARCHAR(255) NOT NULL UNIQUE,
       address VARCHAR(255) NOT NULL
   );
   ```

3. **Orders Table**

   ```sql
   CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
    );
   ```

4. **Order Items Table**

   ```sql
   CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10, 2),
    total_price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
   );
   ```

## Sample Data

The following SQL commands are provided to insert sample data into each table.

- ### To insert data into the customers table

```sql
INSERT INTO customers (name, email, address) VALUES
('John Doe', 'john@example.com', '123 Elm St'),
('Jane Smith', 'jane@example.com', '456 Oak St'),
('Alice Johnson', 'alice@example.com', '789 Pine St'),
('Bob Brown', 'bob@example.com', '321 Maple St'),
('Charlie Black', 'charlie@example.com', '654 Cedar St'),
('Diana White', 'diana@example.com', '987 Birch St'),
('Eve Green', 'eve@example.com', '159 Spruce St'),
('Frank Blue', 'frank@example.com', '753 Willow St'),
('Grace Yellow', 'grace@example.com', '852 Fir St'),
('Hank Red', 'hank@example.com', '369 Ash St');
```

- ### To insert data into the products table

```sql
INSERT INTO products (name, price, description) VALUES
('Product A', 30.00, 'Description for Product A'),
('Product B', 20.00, 'Description for Product B'),
('Product C', 50.00, 'Description for Product C'),
('Product D', 15.00, 'Description for Product D'),
('Product E', 25.00, 'Description for Product E'),
('Product F', 40.00, 'Description for Product F'),
('Product G', 10.00, 'Description for Product G'),
('Product H', 60.00, 'Description for Product H'),
('Product I', 35.00, 'Description for Product I'),
('Product J', 45.00, 'Description for Product J');
```

- ### To insert data into the orders table

```sql
INSERT INTO orders (customer_id, order_date, total_amount) VALUES
(1, '2024-12-20', 100.00),
(2, '2024-12-18', 200.00),
(3, '2024-11-10', 150.00),
(4, '2024-12-22', 300.00),
(5, '2024-12-15', 120.00),
(6, '2024-11-05', 80.00),
(7, '2024-12-23', 90.00),
(8, '2024-12-19', 60.00),
(9, '2024-12-17',110.00),
(10, '2024-11-28', 50.00);
```

- To select all the columns from the customers table

```sql
SELECT * FROM customers;
```

---

| id  | name          | email               | address       |
| --- | ------------- | ------------------- | ------------- |
| 1   | John Doe      | john@example.com    | 123 Elm St    |
| 2   | Jane Smith    | jane@example.com    | 456 Oak St    |
| 3   | Alice Johnson | alice@example.com   | 789 Pine St   |
| 4   | Bob Brown     | bob@example.com     | 321 Maple St  |
| 5   | Charlie Black | charlie@example.com | 654 Cedar St  |
| 6   | Diana White   | diana@example.com   | 987 Birch St  |
| 7   | Eve Green     | eve@example.com     | 159 Spruce St |
| 8   | Frank Blue    | frank@example.com   | 753 Willow St |
| 9   | Grace Yellow  | grace@example.com   | 852 Fir St    |
| 10  | Hank Red      | hank@example.com    | 369 Ash St    |

---

- To select all the columns from the products table

```sql
SELECT * FROM products;
```

---

| id  | name      | price | description               |
| --- | --------- | ----- | ------------------------- |
| 1   | Product A | 30.00 | Description for Product A |
| 2   | Product B | 20.00 | Description for Product B |
| 3   | Product C | 50.00 | Description for Product C |
| 4   | Product D | 15.00 | Description for Product D |
| 5   | Product E | 25.00 | Description for Product E |
| 6   | Product F | 40.00 | Description for Product F |
| 7   | Product G | 10.00 | Description for Product G |
| 8   | Product H | 60.00 | Description for Product H |
| 9   | Product I | 35.00 | Description for Product I |
| 10  | Product J | 45.00 | Description for Product J |

---

- To select all the columns from the orders table

```sql
SELECT * FROM orders;
```

---

| id  | customer_id | order_date | total_amount |
| --- | ----------- | ---------- | ------------ |
| 1   | 1           | 2024-12-20 | 100.00       |
| 2   | 2           | 2024-12-18 | 200.00       |
| 3   | 3           | 2024-11-10 | 150.00       |
| 4   | 4           | 2024-12-22 | 300.00       |
| 5   | 5           | 2024-12-15 | 120.00       |
| 6   | 6           | 2024-11-05 | 80.00        |
| 7   | 7           | 2024-12-23 | 90.00        |
| 8   | 8           | 2024-12-19 | 60.00        |
| 9   | 9           | 2024-12-17 | 110.00       |
| 10  | 10          | 2024-11-28 | 50.00        |

---

## Queries:

- Retrieve all customers who have placed an order in the last 30 days.

```sql
SELECT DISTINCT c.id, c.name, o.total_amount
FROM customers c
JOIN orders o ON c.id = o.customer_id
WHERE o.order_date >= CURDATE() - INTERVAL 30 DAY;
```

---

| id  | name          | total_amount |
| --- | ------------- | ------------ |
| 1   | John Doe      | 100.00       |
| 2   | Jane Smith    | 200.00       |
| 4   | Bob Brown     | 300.00       |
| 5   | Charlie Black | 120.00       |
| 7   | Eve Green     | 90.00        |
| 8   | Frank Blue    | 60.00        |
| 9   | Grace Yellow  | 110.00       |
| 10  | Hank Red      | 50.00        |

---

- Get the total amount of all orders placed by each customer.

```sql
SELECT c.id, c.name, SUM(o.total_amount) as total_spent
FROM customers c
JOIN orders o ON c.id = o.customer_id
GROUP BY c.id;
```

| id  | name          | total_amount |
| --- | ------------- | ------------ |
| 1   | John Doe      | 100.00       |
| 2   | Jane Smith    | 200.00       |
| 3   | Alice Johnson | 150.00       |
| 4   | Bob Brown     | 300.00       |
| 5   | Charlie Black | 120.00       |
| 6   | Diana White   | 80.00        |
| 7   | Eve Green     | 90.00        |
| 8   | Frank Blue    | 60.00        |
| 9   | Grace Yellow  | 110.00       |
| 10  | Hank Red      | 50.00        |

- Update the price of Product C to 45.00.

```sql
UPDATE products
SET price = 45.00
WHERE name = 'Product C';
```

- To check the updated the products table

```sql
SELECT * FROM products;
```

---

| id  | name      | price | description               |
| --- | --------- | ----- | ------------------------- |
| 1   | Product A | 30.00 | Description for Product A |
| 2   | Product B | 20.00 | Description for Product B |
| 3   | Product C | 45.00 | Description for Product C |
| 4   | Product D | 15.00 | Description for Product D |
| 5   | Product E | 25.00 | Description for Product E |
| 6   | Product F | 40.00 | Description for Product F |
| 7   | Product G | 10.00 | Description for Product G |
| 8   | Product H | 60.00 | Description for Product H |
| 9   | Product I | 35.00 | Description for Product I |
| 10  | Product J | 45.00 | Description for Product J |

---

- Add a new column discount to the products table.

```sql
ALTER TABLE products
ADD COLUMN discount DECIMAL(5, 2) DEFAULT 0.00;
```

- To check the updated the products table

```sql
SELECT * FROM products;
```

---

| id  | name      | price | description               | discount |
| --- | --------- | ----- | ------------------------- | -------- |
| 1   | Product A | 30.00 | Description for Product A | 0.00     |
| 2   | Product B | 20.00 | Description for Product B | 0.00     |
| 3   | Product C | 45.00 | Description for Product C | 0.00     |
| 4   | Product D | 15.00 | Description for Product D | 0.00     |
| 5   | Product E | 25.00 | Description for Product E | 0.00     |
| 6   | Product F | 40.00 | Description for Product F | 0.00     |
| 7   | Product G | 10.00 | Description for Product G | 0.00     |
| 8   | Product H | 60.00 | Description for Product H | 0.00     |
| 9   | Product I | 35.00 | Description for Product I | 0.00     |
| 10  | Product J | 45.00 | Description for Product J | 0.00     |

---

- Retrieve the top 3 products with the highest price.

```sql
SELECT p.name, p.price
FROM products p
ORDER BY price DESC
LIMIT 3;
```

---

| name      | price |
| --------- | ----- |
| Product H | 60.00 |
| Product J | 45.00 |
| Product C | 45.00 |

---

- Normalize the database by creating a separate table for order items and updating the orders table to reference the order_items table.

```sql
CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    unit_price DECIMAL(10, 2),
    total_price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

```sql
INSERT INTO order_items (order_id, product_id, quantity, unit_price, total_price)
VALUES
(1, 1, 2, 25.00, 50.00),
(1, 3, 1, 50.00, 50.00),
(2, 2, 3, 20.00, 60.00),
(2, 5, 4, 25.00, 100.00),
(2, 6, 1, 40.00, 40.00),
(3, 4, 5, 15.00, 75.00),
(3, 7, 2, 20.00, 40.00),
(3, 9, 1, 35.00, 35.00),
(4, 6, 3, 40.00, 120.00),
(4, 9, 2, 35.00, 70.00),
(4, 10, 2, 45.00, 90.00),
(5, 5, 2, 25.00, 50.00),
(5, 4, 1, 15.00, 15.00),
(5, 7, 1, 10.00, 10.00),
(5, 8, 1, 60.00, 60.00),
(6, 2, 4, 20.00, 80.00),
(7, 1, 1, 30.00, 30.00),
(7, 10, 1, 45.00, 45.00),
(8, 3, 1, 50.00, 50.00),
(8, 2, 1, 10.00, 10.00),
(9, 5, 2, 25.00, 50.00),
(9, 4, 1, 15.00, 15.00),
(9, 9, 1, 35.00, 35.00),
(10, 6, 1, 40.00, 40.00),
(10, 7, 1, 10.00, 10.00);
```

- Get the names of customers who have ordered Product A.

```sql
SELECT DISTINCT c.name
FROM customers c
JOIN orders o ON c.id = o.customer_id
JOIN order_items oi ON o.id = oi.order_id
JOIN products p ON oi.product_id = p.id
WHERE p.name = 'Product A';
;
```

---

| name      |
| --------- |
| John Doe  |
| Eve Green |

---

- Join the orders and customers tables to retrieve the customer's name and order date for each order.

```sql
SELECT c.name, o.order_date
FROM customers c
JOIN orders o ON c.id = o.customer_id;
;
```

---

| name          | order_date |
| ------------- | ---------- |
| John Doe      | 2024-12-20 |
| Jane Smith    | 2024-12-18 |
| Alice Johnson | 2024-11-10 |
| Bob Brown     | 2024-12-22 |
| Charlie Black | 2024-12-15 |
| Diana White   | 2024-11-05 |
| Eve Green     | 2024-12-23 |
| Frank Blue    | 2024-12-19 |
| Grace Yellow  | 2024-12-17 |
| Hank Red      | 2024-11-28 |

---

-Retrieve the orders with a total amount greater than 150.00.

```sql
SELECT *
FROM orders o
WHERE total_amount >= 150.00;
```

---

| id  | customer_id | order_date | total_amount |
| --- | ----------- | ---------- | ------------ |
| 2   | 2           | 2024-12-18 | 200.00       |
| 3   | 3           | 2024-11-10 | 150.00       |
| 4   | 4           | 2024-12-22 | 300.00       |

---

- Retrieve the average total of all orders.

```sql
SELECT AVG(total_amount) AS average_order_total
FROM orders;
```

---

| average_order_total |
| ------------------- |
| 126.000000          |

---

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for any suggestions or improvements.
