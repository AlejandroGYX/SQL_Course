# **Course9：Aggregate functions - 聚合函数**
SQL定义了聚合函数，它们可以使用聚合操作来汇总整个列。 两个最基本的聚合函数是SUM和COUNT，它们可以对列的总值求和或分别计算存在的非空条目的数量。另一个非常有用的功能是平均数函数AVG，它简单地获取SUM并将其与COUNT分开。

以下是关于学生名单及其成绩的总体功能示例：
```
CREATE TABLE grades (name TEXT, grade INTEGER);

INSERT INTO grades (name, grade) VALUES
    ("John", 97), ("Eric", 88), ("Jessica", 98), ("Mike", 82), ("Jeff", NULL);

SELECT "total students", COUNT(name) FROM grades;
SELECT "total grades", COUNT(grade) FROM grades;
SELECT "sum of grades", SUM(grade) FROM grades;
SELECT "grade average", AVG(grade) FROM grades;
SELECT "lowest grade", MIN(grade) FROM grades;
SELECT "highest grade", MAX(grade) FROM grades;
SELECT "names", GROUP_CONCAT(name) FROM grades;
```

语句执行结果：

```
total students|5
total grades|4
sum of grades|365
grade average|91.25
lowest grade|82
highest grade|98
names|John,Eric,Jessica,Mike,Jeff
```

我们可以使用诸如SUM，COUNT，AVG，MIN，MAX等数学函数来完成对数字的聚合。

聚合字符串通常使用GROUP_CONCAT这样的函数来完成，该函数只连接字段。聚合字符串并不简单，而且通常对于分析目的也不是很有用。


## Aggregate functions in Group By statements - Group By语句中的聚合函数
在对行进行分组时，必须对不属于正在分组的字段的所有字段使用聚合函数。这是因为在group by result中引用列是不明确的。必须使用聚合函数来引用group by语句中的列。

我们可以用一个例子来说明这一点。假设我们有以下数据库：
```
CREATE TABLE grades (name TEXT, class INTEGER, grade INTEGER);

INSERT INTO grades (name, class, grade) VALUES
    ("John", 1, 97), ("Eric", 1, 88), ("Jessica", 1, 98), ("Mike", 1, 82), ("Jeff", 1, NULL),
    ("Ben", 2, 93), ("Andrew", 2, 82), ("Jason", 2, 87), ("Carol", 2, 99), ("Fred", 2, 79);
```

一旦我们按课号对结果进行分组，我们就会按结果分组创建两种类型的字段：
* Group by 字段: class
* Aggregate 字段: name, grade

我们可以简单地选择group by字段，但是必须使用聚合函数汇总聚合字段(不属于group by子句)。

让我们使用GROUP BY语句计算每个类的等级平均值和名称列表：
```
CREATE TABLE grades (name TEXT, class INTEGER, grade INTEGER);

INSERT INTO grades (name, class, grade) VALUES
    ("John", 1, 97), ("Eric", 1, 88), ("Jessica", 1, 98), ("Mike", 1, 82), ("Jeff", 1, NULL),
    ("Ben", 2, 93), ("Andrew", 2, 82), ("Jason", 2, 87), ("Carol", 2, 99), ("Fred", 2, 79);

.mode column
.headers on
SELECT class, GROUP_CONCAT(name), AVG(grade)
FROM grades
GROUP BY class;
```

语句执行结果：

```
class       GROUP_CONCAT(name)           AVG(grade)
----------  ---------------------------  ----------
1           John,Eric,Jessica,Mike,Jeff  91.25     
2           Ben,Andrew,Jason,Carol,Fred  88.0      
```

## Exercise - 练习
找出每门课的最高分.

```
CREATE TABLE grades (name TEXT, class INTEGER, grade INTEGER);

INSERT INTO grades (name, class, grade) VALUES
    ("John", 1, 97), ("Eric", 1, 88), ("Jessica", 1, 98), ("Mike", 1, 82), ("Jeff", 1, NULL),
    ("Ben", 2, 93), ("Andrew", 2, 82), ("Jason", 2, 87), ("Carol", 2, 99), ("Fred", 2, 79);

-- enter code here
```

期望的执行结果：
```
1|98
2|99
```
