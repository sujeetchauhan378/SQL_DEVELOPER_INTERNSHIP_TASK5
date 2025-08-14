# SQL_DEVELOPER_INTERNSHIP_TASK5

# SQL Joins – Task 5 (SQL Developer Internship)

## 📌 Objective
Learn to combine data from multiple tables using different SQL join types:
- **INNER JOIN**
- **LEFT JOIN**
- **RIGHT JOIN**
- **FULL OUTER JOIN**

Tools: **DB Browser for SQLite** / **MySQL Workbench**  
Outcome: **Mastery of merging data** and understanding relationships.

---

## 🗄️ Database Schema

### Tables

#### 1. Customers
| Column       | Type         | Description                |
|--------------|-------------|----------------------------|
| customer_id  | INT (PK)    | Unique ID for each customer |
| name         | VARCHAR(50) | Customer name              |
| city         | VARCHAR(50) | City name                  |

#### 2. Orders
| Column       | Type         | Description                           |
|--------------|-------------|---------------------------------------|
| order_id     | INT (PK)    | Unique ID for each order              |
| customer_id  | INT (FK)    | ID referencing Customers table        |
| order_date   | DATE        | Order date                            |
| amount       | DECIMAL     | Order amount                          |

---

## 📝 Sample Data

```sql
-- Drop tables if exist
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS customers;

-- Create Customers table
CREATE TABLE customers (
  customer_id INT PRIMARY KEY,
  name VARCHAR(50),
  city VARCHAR(50)
);

-- Create Orders table
CREATE TABLE orders (
  order_id INT PRIMARY KEY,
  customer_id INT NULL,
  order_date DATE,
  amount DECIMAL(10,2),
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

-- Insert Customers
INSERT INTO customers (customer_id, name, city) VALUES
(1, 'Alice', 'Delhi'),
(2, 'Bob',   'Mumbai'),
(3, 'Cara',  'Pune'),
(4, 'Dan',   'Jaipur'); -- Dan has no orders

-- Insert Orders
INSERT INTO orders (order_id, customer_id, order_date, amount) VALUES
(101, 1, '2025-08-01', 1200.00),
(102, 1, '2025-08-02',  800.00),
(103, 2, '2025-08-03',  500.00),
(104, NULL, '2025-08-04', 300.00); -- guest/unknown customer
