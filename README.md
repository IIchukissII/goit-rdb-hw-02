#**Початкова таблиця**

| номер замовлення | назва товару і кількість | Адреса клієнта | дата замовлення | клієнт    |
|------------------|--------------------------|----------------|-----------------|-----------|
| 101              | лептоп: 3, мишка: 2      | Хрещатик 1     | 2023-03-15      | Мельник   |
| 102              | принтер: 4               | Басейна 2      | 2023-03-17      | Шевченко  |
| 103              | мишка: 4                 | Комп'ютерна 3  | 2023-03-19      | Коваленко |

#**Приведення до першої нормальної форми (1NF)**
У 1NF кожне поле містить атомарні (неділимими) значення.

### Таблиця `orders`

| `order_id`       |  `order_date`   | `client_name`    | `product_name`     | `product_qty` | `address`       |
|------------------|-----------------|------------------|--------------------|---------------|-----------------|
| 101              | 2023-03-15      | Мельник          | лептоп             | 3             | Хрещатик 1      |
| 101              | 2023-03-15      | Мельник          | мишка              | 2             | Хрещатик 1      |
| 102              | 2023-03-17      | Шевченко         | принтер            | 4             | Басейна 2       |
| 103              | 2023-03-19      | Коваленко        | мишка              | 4             | Комп'ютерна 5   |

#**Приведення до другої нормальної форми (2NF)**
У 2NF усунені часткові залежності, тобто всі не ключові атрибути залежать від всього первинного ключа.

### Таблиця `orders`

| `order_id`       |  `order_date`   | `client_id`|
|------------------|-----------------|------------|
| 101              | 2023-03-15      | 1          |
| 102              | 2023-03-17      | 2          |
| 103              | 2023-03-19      | 3          |


### Таблиця `clients`

| `client_id`| `client_name`    | `address`      |
|------------|------------------|----------------|
| 1          | Мельник          | Хрещатик 1     |
| 2          | Шевченко         | Басейна 2      |
| 3          | Коваленко        | Комп'ютерна 3  |


### Таблиця `order_details`

|  `order_id`      | `product_name` | `product_qty`|
|------------------|----------------|--------------|
| 101              | лептоп         | 3            |
| 101              | мишка          | 2            |
| 102              | принтер        | 4            |
| 103              | мишка          | 4            |



#**Приведення до третьої нормальної форми (3NF)**
У 3NF усунені транзитивні залежності, тобто всі не ключові атрибути залежать тільки від первинного ключа.


### Таблиця `address`

| `address_id` | `street_name` | `house_number` |
|--------------|---------------|----------------|
| 1            | Xрещатик      | 1              |
| 2            | Басейна       | 2              |
| 3            | Комп'ютерна   | 3              |

### Таблиця `clients`

| `client_id` | `client_name` | `address_id` |
|-------------|---------------|--------------|
| 1           | Мельник       | 1            |
| 2           | Шевченко      | 2            |
| 3           | Коваленко     | 3            |

### Таблиця `products`

| `product_id` | `product_name` |
|--------------|----------------|
| 1            | лептоп         |
| 2            | мишка          |
| 3            | принтер        |

### Таблиця `orders`

| `order_id` | `client_id` | `order_date` |
|------------|-------------|--------------|
| 101        | 1           | 2023-03-15   |
| 102        | 2           | 2023-03-16   |
| 103        | 3           | 2023-03-17   |

### Заповнення таблиці `order_details`

| `order_detail_id` | `order_id` | `product_id` | `product_qty` |
|-------------------|------------|--------------|---------------|
| 1                 | 101        | 1            | 3             |
| 2                 | 101        | 2            | 2             |
| 3                 | 102        | 3            | 4             |
| 4                 | 103        | 2            | 4             |
