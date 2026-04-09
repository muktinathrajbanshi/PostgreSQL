🔍 1. View Table Structure
\d users;

👉 Displays:

Columns
Data types
Constraints
🔍 2. Case-Insensitive Search (ILIKE)
SELECT \* FROM users
WHERE name ILIKE '%mukti%';

👉 Useful for:

Flexible text search
Case-insensitive matching
🧠 3. UPSERT (Insert or Update)
INSERT INTO users (id, name, email)
VALUES (1, 'Mukti', 'mukti@gmail.com')
ON CONFLICT (id)
DO UPDATE SET name = EXCLUDED.name;

👉 Best for:

Avoiding duplicate data
Real-world applications
⚡ 4. RETURNING (Get Data After Insert)
INSERT INTO users (name, email)
VALUES ('Ram', 'ram@gmail.com')
RETURNING \*;

👉 Instantly returns inserted data

🔄 5. DELETE with RETURN
DELETE FROM users
WHERE id = 1
RETURNING \*;

👉 See what data was deleted

📊 6. Window Function (Ranking)
SELECT name, salary,
RANK() OVER (ORDER BY salary DESC) AS rank
FROM employees;

👉 Used for:

Ranking
Analytics
Reports
🔗 7. CTE (WITH - Clean Queries)
WITH high_orders AS (
SELECT _ FROM orders WHERE amount > 100
)
SELECT _ FROM high_orders;

👉 Makes complex queries:

Cleaner
More readable
⚡ 8. JSON Query (Modern Apps)
SELECT data->>'name' AS name
FROM products;

👉 Works like:

MongoDB-style queries
JSON data extraction
🔍 9. EXISTS (Efficient Check)
SELECT name
FROM users u
WHERE EXISTS (
SELECT 1 FROM orders o WHERE o.user_id = u.id
);

👉 Often faster than JOIN for checks

⚡ 10. Bulk Insert
INSERT INTO users (name, email)
VALUES
('A', 'a@gmail.com'),
('B', 'b@gmail.com'),
('C', 'c@gmail.com');

👉 Insert multiple rows efficiently

🧠 11. CASE (Conditional Logic)
SELECT name,
CASE
WHEN age >= 18 THEN 'Adult'
ELSE 'Minor'
END
FROM users;

👉 Adds logic inside SQL queries

⚡ 12. DISTINCT ON (Unique Rows)
SELECT DISTINCT ON (email) \*
FROM users;

👉 Powerful for:

Removing duplicates
Getting unique records
🚀 13. EXPLAIN ANALYZE (Performance Check)
EXPLAIN ANALYZE SELECT \* FROM users;

👉 Shows:

Execution time
Query performance
🔐 14. Row Locking (Concurrency Control)
SELECT \* FROM users
WHERE id = 1
FOR UPDATE;

👉 Prevents:

Data conflicts
Race conditions
⚡ 15. Generate Data (Testing)
