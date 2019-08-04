# **Course8：Group by - Group by语句**
GROUP BY语句是用于分析目的的最重要的语句，它使我们能够聚合一组行并从中汇总结果。 例如 - 使用客户和订单数据库，我们可以使用GROUP BY语句来计算每个客户的订单数量。

让我们来看看我们的客户数据库并计算每个客户有多少订单：
```
CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    first_name TEXT,
    last_name TEXT
);

CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    product_name TEXT
);

INSERT INTO customers (first_name, last_name) VALUES
    ("John", "Doe");

INSERT INTO orders (customer_id, product_name) VALUES
    (last_insert_rowid(), "Coke"),
    (last_insert_rowid(), "Sprite");

INSERT INTO customers (first_name, last_name) VALUES
    ("Eric", "Smith");

INSERT INTO orders (customer_id, product_name) VALUES
    (last_insert_rowid(), "Doritos");

.mode column
.headers on
SELECT first_name, last_name, COUNT(*) AS total_orders FROM customers
JOIN orders ON orders.customer_id = customers.id
GROUP BY orders.customer_id;
```

语句执行结果：
```
first_name  last_name   total_orders
----------  ----------  ------------
John        Doe         2           
Eric        Smith       1           
```

## Exercise - 练习
编写一个查询，显示数据库中每个人的名字和可用订单的数量。

```
CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    first_name TEXT,
    last_name TEXT
);

CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    product_name TEXT
);

INSERT INTO customers (first_name, last_name) VALUES
    ("John", "Doe");

INSERT INTO orders (customer_id, product_name) VALUES
    (last_insert_rowid(), "Coke"),
    (last_insert_rowid(), "Sprite");

INSERT INTO customers (first_name, last_name) VALUES
    ("Eric", "Smith");

INSERT INTO orders (customer_id, product_name) VALUES
    (last_insert_rowid(), "Doritos");

-- enter your code here
```

期望的执行结果：
```
John|2
Eric|1
```
