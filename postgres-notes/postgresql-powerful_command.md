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
