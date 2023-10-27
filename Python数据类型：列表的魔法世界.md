![](https://p.ipic.vip/cfnkto.png)

列表是一种多用途的数据结构，用于存储和操作有序数据集合。

这篇文章会学习到Python列表，包括定义、基本操作、常见方法、列表推导式、多维列表以及实际应用场景。

## 1. 列表的定义

- 列表是有序的数据集合，可以包含不同类型的元素，如整数、字符串、列表等。
- 使用方括号 `[]` 定义列表，元素之间用逗号分隔。

```python
fruits = ["apple", "banana", "cherry"]
numbers = [1, 2, 3, 4, 5]
```

## 2. 基本操作

- 访问列表元素：使用索引来获取列表中的元素，索引从0开始。

```python
first_fruit = fruits[0]  # "apple"
```

- 列表切片：使用切片操作获取子列表。

```python
some_numbers = numbers[1:4]  # [2, 3, 4]
```

## 3. 常见列表方法

- `append()` 方法：在列表末尾添加元素。

```python
fruits.append("orange")
```

- `remove()` 方法：删除指定元素。

```python
fruits.remove("banana")
```

- `len()` 函数：获取列表长度。

```python
num_of_fruits = len(fruits)  # 3
```

## 4. 列表推导式

- 列表推导式是一种简洁创建列表的方式。

```python
squares = [x ** 2 for x in range(1, 6)]  # [1, 4, 9, 16, 25]
```

## 5. 多维列表

- 列表可以包含其他列表，创建多维列表。

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```

## 6. 实际应用场景

- 数据处理：列表用于存储和处理数据，如数据排序、过滤和转换等。

```python
# 数据排序
scores = [90, 75, 88, 92, 78]
sorted_scores = sorted(scores)
```

- 循环结构：列表在循环中发挥重要作用，如 `for` 循环遍历元素。

```python
for fruit in fruits:
    print(fruit)
```

- 实际应用：列表在各种应用中广泛使用，如清单、日历、任务管理等。

## 总结
Python列表是处理有序数据集合的强大工具，具备丰富的操作和方法。本文介绍了列表的定义、基本操作、常见方法、列表推导式、多维列表和实际应用场景，能帮助你更好地应用列表数据类型。


--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)


