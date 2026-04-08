# 📘 PostgreSQL Notes

## 🔹 What is PostgreSQL?

PostgreSQL is an open-source relational database management system (RDBMS) used to store and manage structured data.

---

## 🔹 Key Features

- Open-source and free
- Supports SQL (Structured Query Language)
- Highly scalable
- Strong data integrity
- ACID compliant (Atomicity, Consistency, Isolation, Durability)

---

## 🔹 Basic Commands

### 1. Create Database

```sql
CREATE DATABASE mydb;
```

# 🚀 PostgreSQL Advanced Notes

## 📌 1. Introduction

PostgreSQL is an advanced open-source Relational Database Management System (RDBMS) known for reliability, scalability, and performance.

---

# 🧠 2. Database Architecture

## 🔹 Components

- **Database Server** → Manages databases
- **Client** → Sends queries (psql, apps)
- **Tablespaces** → Physical storage location
- **Schemas** → Logical grouping of tables

---

# 🏗️ 3. Schema & Table Design

## 🔹 Create Schema

```sql
CREATE SCHEMA ecommerce;
```

## 🔹 Create Table with Constraints

```sql
CREATE TABLE ecommerce.users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  age INT CHECK (age >= 18),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

# 🔑 4. Constraints

- **PRIMARY KEY** → Unique identifier
- **FOREIGN KEY** → Relationship between tables
- **UNIQUE** → No duplicate values
- **NOT NULL** → Cannot be empty
- **CHECK** → Custom condition

```sql
CREATE TABLE orders (
  id SERIAL PRIMARY KEY,
  user_id INT REFERENCES ecommerce.users(id),
  amount DECIMAL(10,2) CHECK (amount > 0)
);
```

---

# 🔗 5. Relationships

## 🔹 One-to-Many

- One user → Many orders

## 🔹 Many-to-Many

```sql
CREATE TABLE students_courses (
  student_id INT,
  course_id INT,
  PRIMARY KEY (student_id, course_id)
);
```

---

# 🔍 6. Advanced Queries

## 🔹 JOIN

```sql
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id;
```

## 🔹 LEFT JOIN

```sql
SELECT users.name, orders.amount
FROM users
LEFT JOIN orders ON users.id = orders.user_id;
```

## 🔹 GROUP BY

```sql
SELECT user_id, SUM(amount)
FROM orders
GROUP BY user_id;
```

## 🔹 HAVING

```sql
SELECT user_id, SUM(amount)
FROM orders
GROUP BY user_id
HAVING SUM(amount) > 100;
```

---

# ⚡ 7. Indexing (Performance)

## 🔹 Create Index

```sql
CREATE INDEX idx_users_email ON users(email);
```

## 🔹 Why Index?

- Faster search
- Improves query performance

---

# 🔄 8. Transactions

## 🔹 ACID Properties

- Atomicity
- Consistency
- Isolation
- Durability

## 🔹 Example

```sql
BEGIN;

INSERT INTO users (name, email)
VALUES ('Ram', 'ram@gmail.com');

COMMIT;
```

## 🔹 Rollback

```sql
ROLLBACK;
```

---

# 🧩 9. Views

## 🔹 Create View

```sql
CREATE VIEW user_orders AS
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id;
```

---

# ⚙️ 10. Stored Functions

```sql
CREATE FUNCTION get_total_orders(uid INT)
RETURNS INT AS $$
BEGIN
  RETURN (SELECT COUNT(*) FROM orders WHERE user_id = uid);
END;
$$ LANGUAGE plpgsql;
```

---

# 🔐 11. User & Permissions

## 🔹 Create User

```sql
CREATE USER admin WITH PASSWORD '1234';
```

## 🔹 Grant Permission

```sql
GRANT ALL PRIVILEGES ON DATABASE mydb TO admin;
```

---

# 📦 12. JSON Support

PostgreSQL supports JSON (important for modern apps)

```sql
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  data JSON
);
```

---

# 📊 13. Aggregation Functions

- COUNT()
- SUM()
- AVG()
- MAX()
- MIN()

```sql
SELECT AVG(amount) FROM orders;
```

---

# 🔁 14. Subqueries

```sql
SELECT name
FROM users
WHERE id IN (
  SELECT user_id FROM orders WHERE amount > 50
);
```

---

# ⚡ 15. Performance Optimization

- Use indexes
- Avoid SELECT \*
- Use LIMIT
- Normalize data
- Analyze queries using:

```sql
EXPLAIN ANALYZE SELECT * FROM users;
```

---

# 🧱 16. Normalization

## 🔹 Types

- 1NF → No repeating groups
- 2NF → No partial dependency
- 3NF → No transitive dependency

---

# 🧪 17. Backup & Restore

## 🔹 Backup

```bash
pg_dump mydb > backup.sql
```

## 🔹 Restore

```bash
psql mydb < backup.sql
```

---

# 🌐 18. PostgreSQL with Node.js (PERN Stack)

```javascript
const { Pool } = require("pg");

const pool = new Pool({
  user: "postgres",
  password: "1234",
  host: "localhost",
  port: 5432,
  database: "mydb",
});
```

---

# 🔥 19. Best Practices

- Use proper naming conventions
- Always use indexes for large tables
- Avoid unnecessary joins
- Secure passwords
- Use environment variables

---

# 🎯 Conclusion

PostgreSQL is a powerful, scalable, and production-ready database used in real-world applications like banking, eCommerce, and enterprise systems.

---
