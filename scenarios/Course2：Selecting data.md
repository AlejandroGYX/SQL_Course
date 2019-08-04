# **Course2：Selecting data - 选择数据**
>选择数据是SQL（a.k.a结构化查询语言）的基础，可用于查询在任何地方的从小量到大量数据。

这是SELECT语句：
```
SELECT column1, column2, column3...
FROM table1, table2, table3...
WHERE condition1 AND condition2...
```

SELECT语句后面的第一行指定了我们要在查询中选择的列。 如果我们想要选择表的所有字段，我们可以使用星号（*）。 如果查询返回大量数据，则应避免选择所有字段，因为获取的数据越多，查询在时间和网络资源方面所花费的时间就越多。

在FROM子句之后，您需要指定要获取数据的表（或多个表）。 获取多个表是SQL中术语“连接”表的另一种语法。 我们还没有进入这个角色的“joining”表，所以现在我们假设你应该只在SELECT查询中放一个表。

查询的最后一个（也是可选的）部分是WHERE子句，它指示应该从查询返回行的条件。或者换句话说，它使您可以根据特定参数过滤结果。WHERE子句可以通过仅仅查看表中数据的特定子集来分析数据，以获得深入了解。

WHERE语句接收布尔语句，可以使用文本比较运算符，数字比较运算符，IS NULL检查等。

## Exercise - 练习
编写一个SELECT查询，从“students”表中选择所有收到80分以上成绩的学生。只返回学生的姓名。

参考代码：
```
CREATE TABLE students (name text, grade int);
INSERT INTO students VALUES ("Eric", 83);
INSERT INTO students VALUES ("John", 78);
INSERT INTO students VALUES ("Andrew", 91);
INSERT INTO students VALUES ("Jessica", 95);
INSERT INTO students VALUES ("Chris", 79);

```

期望的执行结果：

>**Eric**

>**Andrew**

>**Jessica**

