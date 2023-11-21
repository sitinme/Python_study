![](https://p.ipic.vip/cfnkto.png)

在Python中，格式化字符串输出是一项非常常见的任务，用于将变量、表达式和文本组合成一个可读性强的字符串。Python提供了多种方式来实现字符串格式化，每种方式都有其独特的优势和用法。本篇文章将详细介绍Python中格式化字符串输出的几种方式，包括：

1. **百分号格式化**：这是Python中最古老的字符串格式化方式之一，它使用百分号（%）作为占位符，允许你插入变量或表达式。这种方式已经存在很长时间，但在Python 3.x 中不再被推荐使用。

2. **`str.format()`方法**：这是一种更现代的字符串格式化方式，它使用大括号 `{}` 作为占位符，并支持更多的格式化选项，如对齐、精度和类型转换。

3. **f-字符串**：这是Python 3.6及更高版本引入的一种新的字符串格式化方式，它使用前缀 `f`，允许在大括号 `{}` 内插入变量或表达式，非常直观和简洁。

4. **字符串模板（`string.Template`）**：字符串模板使用 `$` 作为占位符，通过 `substitute()` 方法来替换占位符，适用于一些特定的场景。

5. **`join()`方法**：`join()`方法是一种将多个字符串连接成一个字符串的方式，通常用于将列表中的字符串元素合并。

## 1. 百分号格式化

百分号格式化是Python中最古老的字符串格式化方式之一。它使用百分号（%）作为占位符，通过格式说明符来插入变量或表达式。

以下是一些示例：

```python
name = "Alice"
age = 30
print("My name is %s and I am %d years old." % (name, age))
```

百分号格式化的格式说明符指定了要插入的变量类型和格式。以下是一些常用的格式说明符：

- `%s`：字符串
- `%d`：整数
- `%f`：浮点数

### 示例代码

```python
# 使用百分号格式化
quantity = 3
price = 9.99
total = quantity * price
print("You ordered %d items for a total of $%.2f." % (quantity, total))
```

虽然百分号格式化在一些旧代码中仍然很常见，但在处理复杂的格式化需求时可能显得不够灵活。

## 2. 使用`str.format()`方法

`str.format()`方法是一种更现代和强大的字符串格式化方式。它使用大括号 `{}` 作为占位符，并允许在大括号内添加格式说明符。

以下是示例：

```python
name = "Bob"
age = 25
print("My name is {} and I am {} years old.".format(name, age))
```

`str.format()`方法支持更多的格式化选项，如对齐、精度和类型转换。

### 示例代码

```python
# 使用str.format()
name = "John"
greeting = "Hello, {}!"
formatted_greeting = greeting.format(name)
print(formatted_greeting)

# 格式说明符
radius = 5
area = 3.14159 * radius ** 2
print("The area of a circle with radius {} is {:.2f} square units.".format(radius, area))
```

`str.format()`方法提供了更多控制格式化输出的选项，使其更灵活。

## 3. 使用f-字符串

f-字符串是Python 3.6及更高版本引入的一种新的字符串格式化方式。它非常直观和简洁。

示例如下：

```python
name = "Charlie"
age = 35
print(f"My name is {name} and I am {age} years old.")
```

f-字符串在字符串前加上 `f` 前缀，然后使用大括号 `{}` 插入变量或表达式。这种方式使代码更易读和维护。

### 示例代码

```python
# 使用f-字符串
radius = 5
area = 3.14159 * radius ** 2
print(f"The area of a circle with radius {radius} is {area:.2f} square units.")
```

f-字符串是一种非常方便的方式，尤其在需要在字符串中嵌入变量时。

## 4. 使用字符串模板（`string.Template`）

Python的`string.Template`类提供了另一种格式化字符串的方式，使用 `$` 作为占位符。

以下是示例：

```python
from string import Template

name = "David"
age = 40
template = Template("My name is $name and I am $age years old.")
message = template.substitute(name=name, age=age)
print(message)
```

字符串模板使用 `$` 符号作为占位符，然后使用 `substitute()` 方法来替换占位符。

### 示例代码

```python
# 使用字符串模板
product = "book"
price = 19.99
template = Template("The price of the $product is $$price.")
message = template.substitute(product=product, price=price)
print(message)
```

字符串模板在一些特殊情况下非常有用，例如需要在模板中转义某些字符。

## 5. 使用`join()`方法连接字符串

`join()`方法允许你将多个字符串连接成一个字符串。

示例如下：

```python
words = ["Hello", "World", "Python"]
sentence = " ".join(words)
print(sentence)
```

`join()`方法通常用于将列表中的字符串元素合并为一个字符串，可以指定连接字符串的分隔符。

### 示例代码

```python
# 使用join()方法
words = ["Python", "is", "fun"]
sentence = " ".join(words)
print(sentence)

# 指定分隔符
numbers = ["1", "2", "3", "4", "5"]
csv = ",".join(numbers)
print(csv)
```

`join()`方法非常适用于构建包含多个项目的字符串，例如CSV数据。

## 选择合适的方式

选择哪种字符串格式化方式取决于需求。百分号格式化在一些旧代码中仍然很常见，但`str.format()`和f-字符串在现代Python中更受欢迎。字符串模板和`join()`方法则在特定情况下非常有用。根据任务的复杂性、可读性和维护性，选择合适的方式。

总之，Python提供了丰富的字符串格式化选项，可以根据具体情况选择最适合你的方式，使字符串输出更加清晰和优雅。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
