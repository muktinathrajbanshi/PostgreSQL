<!-- most powerful commands  -->

⚡ 1. View Table Structure
\d users;

👉 Shows columns, types, constraints

🔍 2. Search Data Fast (ILIKE)
SELECT \* FROM users
WHERE name ILIKE '%mukti%';

👉 Case-insensitive search (very useful)

🧠 3. UPSERT (Insert or Update)
INSERT INTO users (id, name, email)
VALUES (1, 'Mukti', 'mukti@gmail.com')
ON CONFLICT (id)
DO UPDATE SET name = EXCLUDED.name;

👉 Super powerful for real apps

⚡ 4. RETURNING (Get Data After Insert)
INSERT INTO users (name, email)
VALUES ('Ram', 'ram@gmail.com')
RETURNING \*;

👉 Instantly get inserted data

🔄 5. DELETE with RETURN
DELETE FROM users
WHERE id = 1
RETURNING \*;

👉 See what got deleted

📊 6. Window Function (Advanced)
SELECT name, salary,
RANK() OVER (ORDER BY salary DESC) AS rank
FROM employees;

👉 Ranking, analytics (VERY IMPORTANT)

🔗 7. WITH (CTE - Clean Queries)
WITH high*orders AS (
SELECT * FROM orders WHERE amount > 100
)
SELECT \_ FROM high_orders;

👉 Makes complex queries clean

⚡ 8. JSON Query (Modern Apps)
SELECT data->>'name' AS name
FROM products;

👉 Works like MongoDB style

🔍 9. EXISTS (Fast Check)
SELECT name
FROM users u
WHERE EXISTS (
SELECT 1 FROM orders o WHERE o.user_id = u.id
);

👉 Faster than JOIN in many cases

⚡ 10. Bulk Insert
INSERT INTO users (name, email)
VALUES
('A', 'a@gmail.com'),
('B', 'b@gmail.com'),
('C', 'c@gmail.com');
🧠 11. CASE (Conditional Logic)
SELECT name,
CASE
WHEN age >= 18 THEN 'Adult'
ELSE 'Minor'
END
FROM users;
⚡ 12. DISTINCT ON (Unique Rows)
SELECT DISTINCT ON (email) \*
FROM users;

👉 Very powerful but less known

🚀 13. EXPLAIN ANALYZE (Performance)
EXPLAIN ANALYZE SELECT \* FROM users;

👉 Shows query execution time

🔐 14. Lock Row (Concurrency)
SELECT \* FROM users
WHERE id = 1
FOR UPDATE;

👉 Prevents conflicts in transactions

⚡ 15. Generate Data (Testing)
SELECT generate_series(1, 10);

👉 Creates numbers instantly

🧩 16. Array Support
SELECT ARRAY[1,2,3,4];
🔥 17. Full Text Search
SELECT _
FROM users
WHERE to_tsvector(name) @@ to_tsquery('mukti');
⚡ 18. LIMIT + OFFSET (Pagination)
SELECT _ FROM users
LIMIT 10 OFFSET 20;
💣 19. Truncate (Fast Delete)
TRUNCATE TABLE users RESTART IDENTITY;

👉 Faster than DELETE

🧠 20. Copy Data (Super Fast Import/Export)
COPY users TO '/tmp/users.csv' DELIMITER ',' CSV HEADER;
🔥 Pro Developer Tip

If you master these:

JOIN + GROUP BY
CTE (WITH)
WINDOW FUNCTIONS
INDEX + EXPLAIN

👉 You’re already industry-level backend developer
