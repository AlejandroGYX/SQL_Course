# **Course11：Distinct queries – Distinct查询**
Distinct查询使我们能够计算表或一组行中惟一值的数量。

为此，我们可以使用DISTINCT指令。如果两行或更多行的所有列完全匹配，则DISTINCT查询将返回重复数据删除的条目集。

当我们想要获得人员列表时，这是一个有用的例子。

让我们来看一些示例：
```
CREATE TABLE grades (name TEXT, subject TEXT, grade INTEGER);

INSERT INTO grades (name, subject, grade) VALUES
    ("John", "CompSci", 97), ("Eric", "CompSci", 88), ("Carol", "Arts", 99),
    ("John", "History", 93), ("Andrew", "History", 82), ("Eric", "History", 87),
    ("Steve", "Physics", 91), ("John", "Physics", 84), ("Barney", "Physics", 97);

SELECT "all names", COUNT(name) FROM grades;
SELECT "unique names", COUNT(DISTINCT name) FROM grades;
SELECT DISTINCT name FROM grades;
```

语句执行结果：

![SQL](./photos/Course11/C11-1.PNG)

DISTINCT查询与GROUP BY子句非常相似，并且在子句中选择了所有列。 这有效地使所有相同的行组合在一起。 GROUP BY查询和DISTINCT查询之间的区别在于，您无法计算使用DISTINCT查询为每一行标识的相同事件的数量。 但是，它在大多数情况下比GROUP BY查询更有效。


## Exercise - 练习
从grades表中获取所有不同科目的列表。

```
CREATE TABLE grades (name TEXT, subject TEXT, grade INTEGER);

INSERT INTO grades (name, subject, grade) VALUES
    ("John", "CompSci", 97), ("Eric", "CompSci", 88), ("Carol", "Arts", 99),
    ("John", "History", 93), ("Andrew", "History", 82), ("Eric", "History", 87),
    ("Steve", "Physics", 91), ("John", "Physics", 84), ("Barney", "Physics", 97);

-- enter code here

```
