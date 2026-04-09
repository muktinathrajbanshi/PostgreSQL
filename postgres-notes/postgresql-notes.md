🔹 1. Introduction

PostgreSQL is a powerful, open-source Relational Database Management System (RDBMS) used to store, manage, and process structured data efficiently.

🔹 2. Key Features
Open-source and free
Supports SQL (Structured Query Language)
Highly scalable and reliable
Strong data integrity
ACID compliant:
Atomicity
Consistency
Isolation
Durability
🧠 3. Database Architecture
🔹 Core Components
Database Server → Handles database operations
Client → Tools like psql, apps, APIs
Tablespaces → Physical storage locations
Schemas → Logical grouping of tables
🏗️ 4. Schema & Table Design
🔹 Create Database
CREATE DATABASE mydb;
🔹 Create Schema
CREATE SCHEMA ecommerce;
🔹 Create Table with Constraints
CREATE TABLE ecommerce.users (
id SERIAL PRIMARY KEY,
name VARCHAR(100) NOT NULL,
email VARCHAR(100) UNIQUE NOT NULL,
age INT CHECK (age >= 18),
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
🔑 5. Constraints
PRIMARY KEY → Unique identifier
FOREIGN KEY → Relationship between tables
UNIQUE → Prevent duplicate values
NOT NULL → Cannot be empty
CHECK → Custom validation
CREATE TABLE orders (
id SERIAL PRIMARY KEY,
user_id INT REFERENCES ecommerce.users(id),
amount DECIMAL(10,2) CHECK (amount > 0)
);

🔗 6. Relationships
🔹 One-to-Many
One user → Many orders
🔹 Many-to-Many
CREATE TABLE students_courses (
student_id INT,
course_id INT,
PRIMARY KEY (student_id, course_id)
);
🔍 7. Advanced Queries
🔹 INNER JOIN
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id;
🔹 LEFT JOIN
SELECT users.name, orders.amount
FROM users
LEFT JOIN orders ON users.id = orders.user_id;
🔹 GROUP BY
SELECT user_id, SUM(amount)
FROM orders
GROUP BY user_id;
🔹 HAVING
SELECT user_id, SUM(amount)
FROM orders
GROUP BY user_id
HAVING SUM(amount) > 100;
⚡ 8. Indexing (Performance)
🔹 Create Index
CREATE INDEX idx_users_email ON users(email);
🔹 Benefits
Faster data retrieval
Improves query performance
🔄 9. Transactions
🔹 Example
BEGIN;

INSERT INTO users (name, email)
VALUES ('Ram', 'ram@gmail.com');

COMMIT;
🔹 Rollback
ROLLBACK;
🧩 10. Views
CREATE VIEW user_orders AS
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id;

⚙️ 11. Stored Functions
CREATE FUNCTION get_total_orders(uid INT)
RETURNS INT AS $$
BEGIN
RETURN (SELECT COUNT(\*) FROM orders WHERE user_id = uid);
END;

$$
LANGUAGE plpgsql;
🔐 12. Users & Permissions
🔹 Create User
CREATE USER admin WITH PASSWORD '1234';
🔹 Grant Access
GRANT ALL PRIVILEGES ON DATABASE mydb TO admin;
📦 13. JSON Support
CREATE TABLE products (
  id SERIAL PRIMARY KEY,
  data JSON
);
📊 14. Aggregation Functions
COUNT()
SUM()
AVG()
MAX()
MIN()
SELECT AVG(amount) FROM orders;
🔁 15. Subqueries
SELECT name
FROM users
WHERE id IN (
  SELECT user_id FROM orders WHERE amount > 50
);
⚡ 16. Performance Optimization
Use indexes
Avoid SELECT *
Use LIMIT
Normalize data
Analyze queries:
EXPLAIN ANALYZE SELECT * FROM users;
🧱 17. Normalization
1NF → No repeating groups
2NF → No partial dependency
3NF → No transitive dependency
🧪 18. Backup & Restore
🔹 Backup
pg_dump mydb > backup.sql
🔹 Restore
psql mydb < backup.sql
🌐 19. PostgreSQL with Node.js
const { Pool } = require("pg");

const pool = new Pool({
  user: "postgres",
  password: "1234",
  host: "localhost",
  port: 5432,
  database: "mydb",
});
$$

🔥 20. Best Practices
Use clear naming conventions
Index large tables
Avoid unnecessary joins
Secure credentials properly
Use environment variables
🎯 Conclusion

PostgreSQL is a robust, scalable, and production-ready database widely used in:

Banking systems
eCommerce platforms
Enterprise applications
