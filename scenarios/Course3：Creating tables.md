# **Course3：Creating tables - 创建表**
>表是所有数据库的基础。 表可以包含数据行 - 每个数据行都有一组在创建表时定义的预定义列。

创建表时，我们需要指定表将支持的列，以及每列可以容纳的数据类型。

SQLite有以下几种数据类型：
* INTEGER – 整数
* REAL – 浮点数
* TEXT - 用数据库编码方式编码的可读文本（通常是UTF-8）
* BLOB - “Binary Large Object”可以包含一系列字节。适用于存储图像等。

其他数据库（如MySQL和PostgreSQL）有更多的数据类型，但SQLite是一个非常简单的数据库，它不关注性能或规模，这就是它为什么没有很多不同的数据类型。

使用下面的语句来创建表：
```
CREATE TABLE database_name.table_name (
    column1 <data type> PRIMARY KEY,
    column2 <data type>,
    column3 <data type>
);
```

表的主键是一种特殊类型的唯一索引，它定义表的主键。每个主键只能有一行，在主键上选择非常有效，因为它也是一个索引。与唯一索引不同，主键不能为NULL。主键也可用于外键，约束，共享等内容，如果可能，定义一个键始终很重要。

这是一个示例：
```
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    full_name TEXT,
    age INTEGER
);
```

学生的id是主键，因为我们的表中不能有两个以上具有相同ID号的人。full_name需要是文本记录，而年龄可以是整数。

## Exercise - 练习
创建一个名为students的表，其中包含first_name和last_name（两个都是文本列）和一个age（应定义为整数）。

```
-- enter code here

INSERT INTO students (first_name, last_name, age) VALUES ("John", "Doe", 23);
SELECT * FROM students;
```

期望的执行结果：
```
John|Doe|23
```

