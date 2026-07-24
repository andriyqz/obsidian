# DML — SELECT, INSERT, UPDATE, DELETE

## INSERT

```sql
INSERT INTO users (name, email, age)
VALUES ('Іван', 'ivan@example.com', 25);

INSERT INTO users (name, email)
VALUES ('Марія', 'maria@example.com'), ('Петро', 'petro@example.com');

INSERT INTO users (name, email, age)
SELECT name, email, age FROM temp_users WHERE active = true;
```

## SELECT

```sql
SELECT * FROM users;
SELECT name, email FROM users WHERE age > 18;
SELECT DISTINCT city FROM users;
SELECT * FROM users ORDER BY created_at DESC LIMIT 10 OFFSET 20;
```

## UPDATE

```sql
UPDATE users SET age = 26 WHERE id = 1;
UPDATE users SET age = age + 1, updated_at = NOW() WHERE id = 1;
```

## DELETE

```sql
DELETE FROM users WHERE id = 1;
DELETE FROM users; -- видалити всі рядки (повільніше ніж TRUNCATE)
```

## RETURNING

```sql
INSERT INTO users (name, email) VALUES ('Олег', 'oleh@example.com') RETURNING id;
UPDATE users SET age = 30 WHERE id = 1 RETURNING *;
DELETE FROM users WHERE id = 1 RETURNING id, name;
```