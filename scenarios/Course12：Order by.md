# **Course12：Order by - Order by语句**
当我们需要从最重要的行查看到最不重要的行时，对查询结果排序非常有用。例如，要回答“谁是得分最高的人”这个问题，可以通过对结果排序并逐行阅读结果来回答。

让我们获取一个年级列表，并生成一个按字母顺序从A到Z排列的名称列表：
```
CREATE TABLE grades (name TEXT, subject TEXT, grade INTEGER);

INSERT INTO grades (name, subject, grade) VALUES
    ("John", "CompSci", 97), ("Eric", "CompSci", 88), ("Carol", "Arts", 99),
    ("John", "History", 93), ("Andrew", "History", 82), ("Eric", "History", 87),
    ("Steve", "Physics", 91), ("John", "Physics", 84), ("Barney", "Physics", 97);

SELECT DISTINCT name
FROM grades
ORDER by name;
```

语句执行结果：

```
Andrew
Barney
Carol
Eric
John
Steve
```

现在，让我们得到一个分数（成绩）列表，并将所有分数从高到低排序。注意，顺序现在是相反的，这意味着顺序是递减的。使用DEST命令可以记录降序排列。
```
CREATE TABLE grades (name TEXT, subject TEXT, grade INTEGER);

INSERT INTO grades (name, subject, grade) VALUES
    ("John", "CompSci", 97), ("Eric", "CompSci", 88), ("Carol", "Arts", 99),
    ("John", "History", 93), ("Andrew", "History", 82), ("Eric", "History", 87),
    ("Steve", "Physics", 91), ("John", "Physics", 84), ("Barney", "Physics", 97);

SELECT name, subject, grade
FROM grades
ORDER by grade DESC;
```

语句执行结果：

```
Carol|Arts|99
John|CompSci|97
Barney|Physics|97
John|History|93
Steve|Physics|91
Eric|CompSci|88
Eric|History|87
John|Physics|84
Andrew|History|82
```

## Exercise - 练习
从成绩列表中获取按字母顺序排列的科目列表。

```
CREATE TABLE grades (name TEXT, subject TEXT, grade INTEGER);

INSERT INTO grades (name, subject, grade) VALUES
    ("John", "CompSci", 97), ("Eric", "CompSci", 88), ("Carol", "Arts", 99),
    ("John", "History", 93), ("Andrew", "History", 82), ("Eric", "History", 87),
    ("Steve", "Physics", 91), ("John", "Physics", 84), ("Barney", "Physics", 97);

-- enter code here
```

期望的执行结果：
```
Arts
CompSci
History
Physics
```
