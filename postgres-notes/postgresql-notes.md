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
