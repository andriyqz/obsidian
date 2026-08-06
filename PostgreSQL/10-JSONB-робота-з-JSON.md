# JSONB — робота з JSON:

## JSON vs JSONB

| JSON                     | JSONB                    |
|--------------------------|--------------------------|
| зберігає текст як є      | бінарний формат          |
| повільніший при обробці  | швидший при обробці      |
| зберігає порядок ключів  | не зберігає порядок      |
| дублікати ключів         | тільки останнє значення  |
| НЕ підтримує індекси     | підтримує GIN індекси    |

> **Завжди використовуйте JSONB**, якщо не потрібна сумісність з форматом.

## Оператори JSONB

```sql
-- "->"  — отримати як JSON
SELECT metadata -> 'color' FROM products;

-- "->>" — отримати як TEXT
SELECT metadata ->> 'color' FROM products;

-- "#>", "#>>" — вкладений доступ
SELECT metadata #>> '{specs, weight}' FROM products;

-- "?" — чи існує ключ
SELECT * FROM products WHERE metadata ? 'color';

-- "?|" — чи існує хоча б один із ключів
SELECT * FROM products WHERE metadata ?| ARRAY['color', 'size'];

-- "?&" — чи існують всі ключі
SELECT * FROM products WHERE metadata ?& ARRAY['color', 'size'];

-- "@>" — чи містить
SELECT * FROM products WHERE metadata @> '{"color": "red"}';

-- "<@" — чи є підмножиною
SELECT * FROM products WHERE '{"color": "red"}' <@ metadata;
```

## Індекс для JSONB

```sql
CREATE INDEX idx_products_meta ON products USING GIN (metadata);

-- Конкретний шлях
CREATE INDEX idx_products_color ON products USING GIN ((metadata -> 'color'));
```

## Функції JSONB

```sql
SELECT jsonb_each(metadata) FROM products;
SELECT jsonb_object_keys(metadata) FROM products;
SELECT jsonb_array_elements(tags) FROM products;
SELECT jsonb_typeof(metadata -> 'price') FROM products;
```