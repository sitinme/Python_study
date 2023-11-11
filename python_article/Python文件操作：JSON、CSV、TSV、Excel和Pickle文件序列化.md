![](https://p.ipic.vip/cfnkto.png)

文件操作是Python编程的重要部分，它涉及处理各种文件格式，包括JSON、CSV、TSV、Excel和Pickle。

## 一、JSON文件操作

### 1.1 什是JSON？

JSON（JavaScript Object Notation）是一种轻量级数据交换格式，常用于数据存储和交换。它采用文本格式，易于阅读和编写，同时也易于解析和生成。JSON数据由键-值对组成，类似于Python中的字典。

### 1.2 读取JSON文件

Python提供了内置的`json`模块，用于读取和写入JSON文件。

读取JSON文件的示例：

```python
import json

# 读取JSON文件
with open('data.json', 'r') as file:
    data = json.load(file)

# 使用数据
print(data)
```

### 1.3 写入JSON文件

要将数据写入JSON文件，可以使用`json.dump()`方法。

将数据写入JSON文件的示例：

```python
import json

data = {'name': 'John', 'age': 30, 'city': 'New York'}

# 写入JSON文件
with open('data.json', 'w') as file:
    json.dump(data, file)
```

## 二、CSV和TSV文件操作

### 2.1 什么是CSV和TSV？

CSV（逗号分隔值）和TSV（制表符分隔值）是常用的纯文本文件格式，用于存储表格数据。

CSV文件使用逗号作为字段分隔符，而TSV文件使用制表符。这两种格式在数据导出和导入中很常见。

### 2.2 读取CSV和TSV文件

Python的`csv`模块允许读取和写入CSV和TSV文件。

读取CSV文件的示例：

```python
import csv

# 读取CSV文件
with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

### 2.3 写入CSV和 TSV文件

要将数据写入CSV文件，可以使用`csv.writer`。

将数据写入CSV文件的示例：

```python
import csv

data = [['Name', 'Age'], ['Alice', 25], ['Bob', 30], ['Charlie', 35]]

# 写入CSV文件
with open('data.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

## 三、Excel文件操作

### 3.1 什么是Excel文件？

Excel是一种流行的电子表格应用程序，用于处理和分析数据。

在Python中，可以使用第三方库`openpyxl`来读取和写入Excel文件。

### 3.2 读取Excel文件

使用`openpyxl`库读取Excel文件的示例：

```python
import openpyxl

# 读取Excel文件
workbook = openpyxl.load_workbook('data.xlsx')
sheet = workbook.active

for row in sheet.iter_rows():
    for cell in row:
        print(cell.value)
```

### 3.3 写入Excel文件

要将数据写入Excel文件，同样可以使用`openpyxl`库。

将数据写入Excel文件的示例：

```python
import openpyxl

data = [['Name', 'Age'], ['Alice', 25], ['Bob', 30], ['Charlie', 35]]

# 写入Excel文件
workbook = openpyxl.Workbook()
sheet = workbook.active

for row in data:
    sheet.append(row)

workbook.save('data.xlsx')
```

## 四、Pickle文件序列化

### 4.1 什么是Pickle？

Pickle是Python的标准模块，用于将Python对象序列化为二进制数据。允许将对象保存到文件中，以便稍后恢复。Pickle对于保存复杂的数据结构非常有用。

### 4.2 序列化对象

使用Pickle将对象序列化为文件的示例：

```python
import pickle

data = {'name': 'John', 'age': 30, 'city': 'New York'}

# 序列化对象并保存到文件
with open('data.pkl', 'wb') as file:
    pickle.dump(data, file)
```

### 4.3 反序列化对象

要从Pickle文件中加载对象，可以使用`pickle.load()`方法。

反序列化对象的示例：

```python
import pickle

# 从文件加载对象
with open('data.pkl', 'rb') as file:
    loaded_data = pickle.load(file)

# 使用加载的数据
print(loaded_data)
```

## 总结

文件操作是Python编程中的重要部分，涉及处理各种文件格式，包括JSON、CSV、TSV、Excel和Pickle。

文章内容包括如何读取和写入这些文件格式，以及如何进行文件序列化和反序列化。这些技能对于处理数据、配置文件、日志等任务非常重要，因此在Python编程中是不可或缺的。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
