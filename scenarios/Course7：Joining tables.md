# **Course7：Joining tables - 添加表格**
>连接表的能力是数据库最重要的特性之一。它允许用户创建一组新的数据，这些数据是通过并排连接两个表而收集的，将第一个表的列与第二个表的列“stitching(拼接)”。

当您想要查询一个表时，我们需要连接表，然后将信息添加到另一个表中每一行的SELECT语句的结果中。

有效地连接两个表会从具有两个表的查询中创建“笛卡尔积”结果，从而在结果输出中生成M * N行（假设第一个表包含M行而第二个表包含N行）。 但是，当连接两个表时，使用连接条件，该条件限制返回到两个表之间的关系条件的行数。

我们来看一个例子。假设我们有一个包含客户和客户订单的数据库。订单表是指客户表中的客户ID，用于跟踪每个客户的订单。我们希望看到客户完成的所有订单以及客户名称。

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

.mode column
.headers on
SELECT product_name, first_name, last_name
FROM orders
JOIN customers ON orders.customer_id = customers.id;
```

语句执行结果：

```
product_name  first_name  last_name 
------------  ----------  ----------
Coke          John        Doe       
Sprite        John        Doe       
```

## Exercise - 练习
编写SELECT查询，选择产品名称和购买产品的客户的名字，仅当客户名称为John时显示查询结果。

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
    (last_insert_rowid(), "Doritos"),
    (last_insert_rowid(), "Water");

-- enter code here
```

期望的执行结果：
```
Coke|John
Sprite|John
```
