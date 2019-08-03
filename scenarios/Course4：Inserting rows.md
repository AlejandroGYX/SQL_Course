# **Course4：Inserting rows - 插入行**
创建表后，可以使用INSERT命令使用数据填充表。

下面的是语句：
```
INSERT INTO table_name (column1, column2)
VALUES (value11, value12), (value21, value22), (value31, value32), ...
```

INSERT INTO语句之后的第一个子句指定将成为insert语句一部分的列。要插入的每一行都将指定由第一个子句定义的列集，并且顺序相同。第一个子句中未指定的其他任何列将接收默认值。 如果表中定义了NOT NULL列并且INSERT INTO语句错过了该列，则INSERT命令将无法运行。

在INSERT上，如果未明确给出INTEGER PRIMARY KEY列的值，则它将自动填充未使用的整数，通常是列中当前使用的下一个数字。 无论是否使用AUTOINCREMENT关键字，都是如此。

如果省略了指定列列表的列的子句，则假设所有列都将在INSERT语句中提供：
```
INSERT INTO table_name VALUES (value1, value2, value3, value4...);
```

如果缺少其中一个值，则INSERT语句将无效 ，除非查询可以确定哪些字段可以设置为其默认值。通常，我们从来不推荐这种插入方法，因为数据库结构会改变查询的含义，这可能非常危险。

请注意，使用一个查询批量插入值要高效得多得多，而不是因为与数据库的通信而导致每行的几个新INSERT语句。 如果您需要考虑性能，请记住这一点。

以下是一些INSERT查询的实例：
```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);
INSERT INTO customers (first_name, last_name, age) VALUES ("John", "Doe", 23);
SELECT * FROM customers;
```

语句执行结果：

![SQL](./photos/Course4/C4-1.PNG)

现在让我们看看如果我们省略列的列表会发生什么：
```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);
INSERT INTO customers VALUES ("John", "Doe", 23);
SELECT * FROM customers;
```

语句执行结果：

![SQL](./photos/Course4/C4-1.PNG)

让我们删除年龄 - 这将导致查询失败：

```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);
INSERT INTO customers VALUES ("John", "Doe");
SELECT * FROM customers;
```

语句执行结果：

![SQL](./photos/Course4/C4-2.PNG)

让我们添加更多的人：
```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);

INSERT INTO customers (first_name, last_name, age)
VALUES ("John", "Doe", 23), ("Eric", "Smith", 26);

SELECT * FROM customers;
```

语句执行结果：

![SQL](./photos/Course4/C4-3.PNG)

## Replacing and ignoring - 替换和忽略
SQLite支持三种其他类型的语法来插入数据：INSERT OR REPLACE，REPLACE INTO和INSERT OR IGNORE。

REPLACE语句表示如果要插入已存在的行（即表中已存在的主键），则INSERT语句不会失败，实际上会删除旧行，并插入新行。 如果该行不存在则REPLACE将失败，而INSERT OR REPLACE将始终有效，并将插入新行或替换现有行。

INSERT或IGNORE类似于INSERT OR REPLACE，但实际上完全忽略了数据库中已存在的特定行的INSERT命令。 这在插入大量数据时很有用，其中一些数据（或其主键）可能已经存在。


## Exercise - 练习
将“John Snow”插入数据库。John今年33岁。

```
CREATE TABLE customers (first_name NOT NULL, last_name NOT NULL, age);

SELECT * FROM customers;
```
