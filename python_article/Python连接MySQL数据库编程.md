![](https://p.ipic.vip/cfnkto.png)

数据库编程是在应用程序中与数据库交互和管理数据的关键部分。MySQL是一种流行的关系型数据库管理系统（RDBMS），在Python中进行MySQL数据库编程相对容易。

本文介绍如何使用Python进行MySQL数据库编程，包括连接数据库、执行SQL查询、插入、更新和删除数据等操作。

# 目录

1. 安装MySQL驱动
2. 连接MySQL数据库
3. 创建数据库
4. 创建数据表
5. 插入数据
6. 查询数据
7. 更新数据
8. 删除数据
9. 执行事务
10. 关闭数据库连接
11. 示例：一个完整的MySQL数据库编程示例
12. 安全性注意事项
13. 总结

## 1. 安装MySQL驱动

在开始之前，需要安装Python的MySQL数据库驱动程序。最常用的驱动程序之一是`mysql-connector-python`

使用pip进行安装：

```bash
pip install mysql-connector-python
```

## 2. 连接MySQL数据库

在进行任何数据库操作之前，首先需要建立与MySQL数据库的连接。通常，需要提供数据库的主机名、用户名、密码和数据库名称。

以下是连接到MySQL数据库的示例：

```python
import mysql.connector

# 创建数据库连接
db = mysql.connector.connect(
    host="localhost",  # MySQL服务器地址
    user="username",   # 用户名
    password="password",  # 密码
    database="mydatabase"  # 数据库名称
)

# 创建游标对象，用于执行SQL查询
cursor = db.cursor()
```

## 3. 创建数据库

创建一个新的数据库，可以执行以下操作：

```python
# 创建一个名为"mydatabase"的新数据库
cursor.execute("CREATE DATABASE mydatabase")
```

## 4. 创建数据表

在数据库中，数据以表格形式组织。在创建表格之前，需要定义表格的结构，包括列名、数据类型和约束。

以下是一个示例：

```python
# 创建一个名为"customers"的数据表
cursor.execute("CREATE TABLE customers (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), address VARCHAR(255))")
```

## 5. 插入数据

插入数据是将数据添加到数据表中的过程。可以使用SQL的`INSERT INTO`语句来执行插入操作。

以下是一个示例：

```python
# 插入一条记录到"customers"表中
sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"
values = ("John Smith", "123 Main St")
cursor.execute(sql, values)

# 提交更改到数据库
db.commit()

print(f"插入了 {cursor.rowcount} 条记录")
```

## 6. 查询数据

查询数据是从数据库中检索数据的过程。使用SQL的`SELECT`语句来执行查询操作。

以下是一个示例：

```python
# 查询所有记录
cursor.execute("SELECT * FROM customers")

# 获取查询结果
results = cursor.fetchall()

for row in results:
    print(row)
```

## 7. 更新数据

更新数据是修改现有数据的过程。使用SQL的`UPDATE`语句来执行更新操作。

以下是一个示例：

```python
# 更新"customers"表中id为1的记录
sql = "UPDATE customers SET address = %s WHERE id = %s"
values = ("456 Elm St", 1)
cursor.execute(sql, values)

# 提交更改到数据库
db.commit()

print(f"更新了 {cursor.rowcount} 条记录")
```

## 8. 删除数据

删除数据是从数据库中删除数据的过程。使用SQL的`DELETE`语句来执行删除操作。

以下是一个示例：

```python
# 删除"customers"表中id为1的记录
sql = "DELETE FROM customers WHERE id = %s"
values = (1,)
cursor.execute(sql, values)

# 提交更改到数据库
db.commit()

print(f"删除了 {cursor.rowcount} 条记录")
```

## 9. 执行事务

事务是一组SQL操作，要么全部成功，要么全部失败。在某些情况下，需要使用事务来确保数据库的完整性。

以下是一个示例：

```python
try:
    db.start_transaction()
    # 执行一系列SQL操作
    cursor.execute("INSERT INTO customers (name, address) VALUES (%s, %s)", ("Alice", "789 Oak St"))
    cursor.execute("UPDATE customers SET address = %s WHERE id = %s", ("789 Elm St", 2))
    db.commit()  # 提交事务
except:
    db.rollback()  # 事务回滚，撤销之前的操作
```

## 10. 关闭数据库连接

在完成数据库操作后，不要忘记关闭数据库连接，以释放资源。

```python
cursor.close()  # 关闭游标
db.close()  # 关闭数据库连接
```

## 11. 示例：一个完整的MySQL数据库编程示例

以下是一个完整的MySQL数据库编程示例，包括连接数据库、创建表格、插入数据、查询数据、更新数据和删除数据：

```python
import mysql.connector

# 创建数据库连接
db = mysql.connector.connect(
    host="localhost",
    user="username",
    password="password",
    database="mydatabase"
)

# 创建游标对象
cursor = db.cursor()

# 创建一个名为"customers"的数据表
cursor.execute("CREATE TABLE customers (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), address VARCHAR(255))")

# 插入记录
sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"
values = [("John Smith", "123 Main St"), ("Alice Johnson", "456 Elm St")]
cursor.executemany(sql, values)
db.commit()

# 查询记录
cursor.execute("SELECT * FROM customers")
results = cursor.fetchall()
for row in results:
    print(row)

# 更新记录
sql = "UPDATE customers SET address = %s WHERE name = %s"
values = ("789 Oak St", "Alice Johnson")
cursor.execute(sql, values)
db.commit()

# 删除记录
sql = "DELETE FROM customers WHERE name = %s"
values = ("John Smith",)
cursor.execute(sql, values)
db.commit()

# 关闭游标和数据库连接
cursor.close()
db.close()
```

## 12.安全性注意事项

在进行数据库编程时，请务必注意安全性。避免直接将用户提供的数据插入SQL语句，以防止SQL注入攻击。可以使用参数化查询或ORM（对象关系映射）来增强安全性。

## 总结

MySQL数据库编程是Python应用程序的关键组成部分。本文介绍了如何连接数据库、创建数据表、插入、查询、更新和删除数据，以及执行事务。通过这些操作，您可以有效地管理数据，并确保数据的完整性和安全性。希望本文对您在Python中进行MySQL数据库编程有所帮助。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
