# JOINs — об'єднання таблиць

## Види JOIN

### INNER JOIN
Співпадаючі рядки в обох таблицях
```sql
SELECT u.name, o.total
FROM users u
INNER JOIN orders o ON u.id = o.user_id;
```

### LEFT JOIN
Всі рядки з лівої + співпадаючі з правої (NULL якщо немає)
```sql
SELECT u.name, o.total
FROM users u
LEFT JOIN orders o ON u.id = o.user_id;
```

### RIGHT JOIN
Всі рядки з правої + співпадаючі з лівої
```sql
SELECT u.name, o.total
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id;
```

### FULL OUTER JOIN
Всі рядки з обох таблиць
```sql
SELECT u.name, o.total
FROM users u
FULL OUTER JOIN orders o ON u.id = o.user_id;
```

### CROSS JOIN
Декартів добуток (кожний з кожним)
```sql
SELECT u.name, p.product_name
FROM users u
CROSS JOIN products p;
```

### SELF JOIN
Таблиця об'єднується сама з собою
```sql
SELECT e1.name AS employee, e2.name AS manager
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.id;
```

## Фільтрація після JOIN

```sql
-- WHERE фільтрує після об'єднання
-- ON фільтрує до об'єднання (важливо для LEFT JOIN)
```