![](https://p.ipic.vip/cfnkto.png)

在Python中使用SQLite进行数据库操作时，我们将深入研究SQLite数据库的创建、表格管理、数据插入、查询、更新和删除等关键主题，帮助你全面了解如何使用SQLite进行数据库操作。

## 连接到SQLite数据库

SQLite是一种嵌入式数据库引擎，它允许在应用程序中创建和管理本地数据库文件。

Python提供了`sqlite3`模块，可用于连接到SQLite数据库。

```python
import sqlite3

# 连接到数据库（如果不存在则会创建）
conn = sqlite3.connect('mydatabase.db')
```

上述代码创建了一个名为`mydatabase.db`的SQLite数据库文件（如果该文件不存在），并与该数据库建立连接。可以根据需要更改数据库文件的名称。

## 创建表格

在SQLite数据库中，数据以表格的形式存储。要创建表格，使用SQL语句。

以下是一个示例，创建一个名为"students"的表格：

```python
# 创建一个名为"students"的表格
cursor = conn.cursor()
cursor.execute('''
    CREATE TABLE IF NOT EXISTS students (
        id INTEGER PRIMARY KEY,
        name TEXT NOT NULL,
        age INTEGER
    )
''')
conn.commit()
```

上述代码创建了一个包含id、name和age字段的"students"表格。`cursor.execute()`用于执行SQL语句，`conn.commit()`用于提交更改。

## 插入数据

要向表格中插入数据，使用INSERT INTO语句。

以下是一个插入数据的示例：

```python
# 插入一名学生的信息
cursor.execute("INSERT INTO students (name, age) VALUES (?, ?)", ('Alice', 25))
conn.commit()
```

上述代码将一名名为Alice的学生信息插入到"students"表格中。

## 查询数据

使用SELECT语句，从表格中检索数据。

以下是一个查询数据的示例：

```python
# 查询所有学生的信息
cursor.execute("SELECT * FROM students")
students = cursor.fetchall()

for student in students:
    print(student)
```

上述代码执行SELECT语句并将结果存储在`students`变量中，然后通过循环打印每个学生的信息。

## 更新和删除数据

更新数据，使用UPDATE语句；

删除数据，使用DELETE语句。

以下是更新和删除数据的示例：

```python
# 更新学生信息
cursor.execute("UPDATE students SET age = ? WHERE name = ?", (26, 'Alice'))
conn.commit()

# 删除学生信息
cursor.execute("DELETE FROM students WHERE name = ?", ('Alice',))
conn.commit()
```

上述代码分别将学生Alice的年龄更新为26岁，并从表格中删除了名为Alice的记录。

## 异常处理

在进行数据库操作时，务必使用异常处理来处理可能发生的错误。

例如，如果数据库文件无法创建或打开，或者SQL语句执行失败，都应该处理这些异常情况。

```python
try:
    conn = sqlite3.connect('mydatabase.db')
    # 数据库操作
except sqlite3.Error as e:
    print("SQLite error:", e)
finally:
    conn.close()
```

## 数据库事务

SQLite支持事务，这是一组数据库操作的单元，要么全部成功，要么全部失败。

使用`commit()`提交事务，使用`rollback()`回滚事务。

```python
# 开始一个事务
conn = sqlite3.connect('mydatabase.db')
cursor = conn.cursor()

try:
    # 执行一些数据库操作
    cursor.execute("INSERT INTO students (name, age) VALUES (?, ?)", ('Bob', 30))
    cursor.execute("UPDATE students SET age = ? WHERE name = ?", (31, 'Bob'))
    
    # 提交事务
    conn.commit()
except sqlite3.Error:
    # 发生错误，回滚事务
    conn.rollback()
finally:
    conn.close()
```

## 数据库索引

索引是数据库中用于加速数据检索的重要组成部分。在表格上创建索引以提高查询性能。

```python
# 在"students"表格的"name"字段上创建索引
cursor.execute("CREATE INDEX IF NOT EXISTS idx_name ON students (name)")
conn.commit()
```

## 数据库备份和恢复

定期备份数据库以防止数据丢失是一个好习惯。通过复制数据库文件来创建备份，或者使用SQLite的备份命令。

```python
import shutil

# 创建数据库备份
shutil.copy2('mydatabase.db', 'mydatabase_backup.db')
```

## 安全性考虑

在将用户提供的数据插入到数据库之前，务必进行适当的输入验证和数据清理，以防止SQL注入攻击。

```python
user_input = input("Enter a student name: ")

# 使用参数化查询来避免SQL注入
cursor.execute("INSERT INTO students (name) VALUES (?)", (user_input,))
conn.commit()
```

## 总结

SQLite是一种轻量级的嵌入式数据库引擎，适用于各种应用程序，从小型工具到大型数据驱动应用程序。SQLite是一个强大且灵活的数据库引擎，对于许多应用程序都非常适用。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
