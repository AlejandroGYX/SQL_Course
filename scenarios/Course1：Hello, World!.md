# **Course1：Hello, World!**
>*注意：本教程使用SQLite引擎对数据进行操作。它（SQLite引擎）与其他SQL引擎相类似，例如：MySQL和PostgreSQL.*

SQL是一种非常古老的声明性编程语言，它定义了从查询应该返回什么数据以及如何返回。 在每个教程中，我们将从一个空数据库开始，并为我们的练习构建必要的表和数据。

对于第一个教程，我们将简明地讨论启动第一个SQL查询所需的所有指令。

## Creating a table - 创建一个表
>我们使用CREATE TABLE语句语法来创建一个表格。我们将在下一个关于如何使用CREATE TABLE语句语法的教程中详细介绍。

目前，在我们的示例中，我们将使用一个非常基本的CREATE TABLE语句，该语句创建一个名为helloworld的表，在表中有一列名为phrase。列phrase包含TEXT类型的数据，这基本上意味着您可以在其中存储文本，而不是数字、布尔值等。

下面是语句：
```
  CREATE TABLE helloworld (phrase TEXT);
  .tables
```

语句执行结果：

![SQL](https://github.com/AlejandroGYX/SQL_Course/edit/master/scenarios/Course1/C1-1.PNG)

在我们执行完语句之后，表创建完毕。我们使用.tables SQLite语句来显示表的列表。

## Inserting data into a table - 将数据插入表中
>在我们创建表之后，我们可以开始使用INSERT INTO语句将数据插入到我们刚刚创建的表中。 我们将在下一个教程中详细介绍如何使用INSERT INTO语句。

数据逐行插入表中。我们可以使用INSERT INTO语句插入一行，如果我们想要使用UPDATE语句，则更新该行。但同样，我们将在过后更新行的长度。

现在，让我们使用INSERT INTO语句，向表中添加两行，然后计算我们添加的行数：
```
CREATE TABLE helloworld (phrase TEXT);
INSERT INTO helloworld VALUES ("Hello, World!");
INSERT INTO helloworld VALUES ("Goodbye, World!");
SELECT COUNT(*) FROM helloworld;
```
语句执行结果：

![SQL](./photos/Course1/C1-2.PNG)

## Selecting from a table - 从表中选择
>使用SELECT语句从一个或多个表中选择数据。

从表格中选择数据是迄今为止最重要的学习技能，因为它使我们能够根据我们想要回答的问题从数据中产生深入了解。 例如 - “有多少学生平均分高于80”是我们可以使用SELECT语句来回答的问题。

以下是SELECT语句的基本语法：
```
SELECT * FROM helloworld WHERE phrase = "Hello, World!";
```

这个语句将从表helloworld中获取所有列（因此为*），并仅将结果过滤到短语列等于Hello，World！的行。

## Exercise - 练习
选择数据库中其短语列等于“Goodbye，World！”的所有行。

参考代码：
```
CREATE TABLE helloworld (phrase TEXT);
INSERT INTO helloworld VALUES ("Hello, World!");
INSERT INTO helloworld VALUES ("Goodbye, World!");

SELECT * FROM helloworld WHERE phrase = "Goodbye, World!";
```

语句执行结果：

![SQL](./photos/Course1/C1-3.PNG)
