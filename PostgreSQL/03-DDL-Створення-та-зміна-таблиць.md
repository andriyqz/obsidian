# DDL — створення та зміна таблиць

## CREATE TABLE

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    age INTEGER CHECK (age > 0),
    created_at TIMESTAMP DEFAULT NOW()
);
```

## Обмеження (Constraints)

- `PRIMARY KEY` — унікальний ідентифікатор
- `FOREIGN KEY` — посилання на іншу таблицю
- `UNIQUE` — унікальне значення
- `NOT NULL` — обов'язкове поле
- `CHECK` — перевірка умови
- `DEFAULT` — значення за замовчуванням

```sql
CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    total NUMERIC(10,2) CHECK (total >= 0),
    status VARCHAR(20) DEFAULT 'pending'
);
```

## ALTER TABLE

```sql
ALTER TABLE users ADD COLUMN phone VARCHAR(20);
ALTER TABLE users DROP COLUMN phone;
ALTER TABLE users ALTER COLUMN name SET NOT NULL;
ALTER TABLE users RENAME COLUMN name TO full_name;
ALTER TABLE users ADD CONSTRAINT unique_email UNIQUE (email);
```

## DROP TABLE

```sql
DROP TABLE users;          -- видалити таблицю
DROP TABLE IF EXISTS users; -- без помилки якщо не існує
TRUNCATE TABLE users;       -- очистити дані, зберегти структуру
```