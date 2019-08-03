# **Course6：Deleting rows - 删除行**
删除行与更新行非常相似，只有对该行执行的更新类型才是删除。

下面是删除行操作的语句：
```
DELETE FROM table_name WHERE column1 = value1 AND column2 = value2 ...
```

符合DELETE查询标准的所有行都将被删除。


## Exercise - 练习
添加DELETE语句，从customers表中删除Eric。

```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);

INSERT INTO customers (first_name, last_name, age)
VALUES ("John", "Doe", 23), ("Eric", "Smith", 26);

SELECT * FROM customers;

-- enter code here

SELECT * FROM customers;
```
