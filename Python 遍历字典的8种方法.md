![](https://p.ipic.vip/cfnkto.png)

遍历字典是Python中常见的操作，可以很方便的访问字典中的键和值，以执行各种任务。

本文将介绍Python中遍历字典的8种方法，包括for循环、字典方法和推导式等。

## 方法一：for循环遍历字典

使用for循环是最常见的遍历字典的方法。可以分别遍历字典的键、值或键值对。

以下是一些示例：

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 遍历字典的键
for name in student_grades:
    print(name)

# 遍历字典的值
for grade in student_grades.values():
    print(grade)

# 遍历字典的键值对
for name, grade in student_grades.items():
    print(f"{name}: {grade}")
```

通过使用for循环，可以轻松访问字典中的元素。这对于执行各种操作，如查找、过滤或转换字典中的数据非常有用。

## 方法二：字典方法items()遍历

使用`items()`方法可以一次性获取字典中的键值对，然后在for循环中遍历它们。这是一种方便的方法，尤其适用于需要同时访问键和值的情况。

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 使用items()方法遍历字典
for name, grade in student_grades.items():
    print(f"{name}: {grade}")
```

`items()`方法返回一个包含键值对的元组，可以在for循环中解包这些元组以获取键和值。

## 方法三：字典方法keys()和values()遍历

使用`keys()`方法可以获取字典中的键，使用`values()`方法可以获取字典中的值。可以分别遍历键和值，如下所示：

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 使用keys()方法遍历字典的键
for name in student_grades.keys():
    print(name)

# 使用values()方法遍历字典的值
for grade in student_grades.values():
    print(grade)
```

这两种方法可以在for循环中单独访问键或值，根据需要执行不同的操作。

## 方法四：字典推导式

字典推导式是一种紧凑的方式来创建新的字典或从现有字典生成新的字典。可以在字典推导式中遍历原字典的键和值，并根据条件创建新的键值对。

以下是一个示例：

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 使用字典推导式创建新字典，只包含成绩大于90的学生
top_students = {name: grade for name, grade in student_grades.items() if grade > 90}
print(top_students)
```

在上面的示例中，使用字典推导式创建了一个新的字典`top_students`，其中包含成绩大于90的学生。

## 方法五：使用enumerate()函数

`enumerate()`函数可用于同时遍历字典的键和值，并提供索引。这对于需要记录元素的位置或索引的情况非常有用。

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 使用enumerate()函数遍历字典的键和值
for index, (name, grade) in enumerate(student_grades.items()):
    print(f"学生#{index+1}: {name} - 成绩: {grade}")
```

在上面的示例中，我们使用`enumerate()`函数获取了每个键值对的索引，并将其一起打印出来。

## 方法六：使用iteritems()（Python 2.x）

在Python 2.x中，有一个名为`iteritems()`的方法，它返回一个迭代器，允许在for循环中以更高效的方式遍历字典的键值对。但需要注意的是，这个方法在Python 3.x中已被废弃，不再可用。

```python
# 创建一个示例字典（仅适用于Python 2.x）
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 使用iteritems()方法遍历字典
for name, grade in student_grades.iteritems():
    print(f"{name}: {grade}")
```

在Python 3.x中，不再使用`iteritems()`方法，而应使用`items()`方法。

## 方法七：使用迭代器

如果内存限制较低或需要处理非常大的字典，可以使用迭代器来遍历字典。`iter()`函数用于创建字典的迭代器，然后使用`next()`函数来逐个获取键值对。

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 创建字典的迭代器
iterator = iter(student_grades)

# 遍历字典并逐个获取键值对
while True:
    try:
        name = next(iterator)
        grade = student_grades[name]
        print(f"{name}: {grade}")
    except StopIteration:
        break
```

使用迭代器可以有效地处理大型字典，因为它不会一次性加载所有键值对到内存中。

## 方法八：使用回调函数

回调函数是一种自定义遍历字典的方法。可以定义一个回调函数，然后在遍历字典时调用它，以执行自定义操作。

```python
# 创建一个示例字典
student_grades = {"Alice": 95, "Bob": 88, "Charlie": 92, "David": 78}

# 定义一个回调函数
def custom_callback(name, grade):
    print(f"{name}: {grade}")

# 遍历字典并调用回调函数
for name, grade in student_grades.items():
    custom_callback(name, grade)
```

使用回调函数可以实现更高度的自定义，例如将键值对写入文件、将数据插入数据库等。

## 总结

遍历字典是Python中常见的操作，有多种方法可供选择，取决于需求和代码的简洁性。不同的方法适用于不同的情况，选择合适的遍历方法可以使代码更加清晰和高效。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
