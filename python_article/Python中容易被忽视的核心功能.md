![](https://p.ipic.vip/cfnkto.png)

Python是一门富有魅力的编程语言，拥有丰富的功能和库，以及强大的社区支持。然而，有一些核心功能经常被忽视，而它们实际上可以极大地提高代码的质量、可读性和性能。

## 1. 解析命令行参数的argparse库

很多Python开发者在编写命令行工具时仍然使用`sys.argv`或自己编写的参数解析代码，但Python标准库中有一个强大的工具可以更轻松地处理命令行参数，那就是`argparse`库。它允许定义命令行选项、参数和子命令，自动生成帮助信息，还支持类型检查和默认值设置。

下面是一个简单的示例：

```python
import argparse

parser = argparse.ArgumentParser(description="一个简单的命令行工具")
parser.add_argument("--input", help="输入文件路径")
parser.add_argument("--output", help="输出文件路径")
args = parser.parse_args()

if args.input and args.output:
    print(f"从 {args.input} 复制到 {args.output}")
```

## 2. 上下文管理器与with语句

上下文管理器是一个被忽视但非常有用的功能，可以确保资源在使用后被正确释放。Python中的`with`语句可以创建一个上下文管理器，比如处理文件、数据库连接或网络套接字时非常有用。

示例：

```python
with open("example.txt", "r") as file:
    data = file.read()
# 在离开with块后，文件会被自动关闭
```

## 3. 列表推导式和生成器表达式

列表推导式和生成器表达式允许以一种简洁的方式创建列表或生成器。它们可以取代传统的循环，使代码更加紧凑和可读。

示例：

```python
# 列表推导式
squares = [x**2 for x in range(10)]

# 生成器表达式
even_squares = (x**2 for x in range(10) if x % 2 == 0)
```

## 4. 字典的setdefault()方法

`setdefault()`方法是字典的一个被忽视的功能，它允许在字典中设置默认值，如果键不存在，则创建该键并设置默认值。这在处理字典时非常有用，避免了繁琐的if-else语句。

示例：

```python
data = {}
data.setdefault("count", 0)
data["count"] += 1
```

## 5. 函数的默认参数值

很多人知道Python函数可以有默认参数值，但不是每个人都了解如何正确使用它们。默认参数值可以简化函数调用，同时允许在需要时提供自定义值。

示例：

```python
def greet(name="World"):
    print(f"Hello, {name}!")

greet()  # 输出 "Hello, World!"
greet("Alice")  # 输出 "Hello, Alice!"
```

## 6. 使用collections库的namedtuple

`namedtuple`是Python的一个被忽视但非常有用的数据结构。它可以为元组的字段分配名称，使代码更具可读性。

示例：

```python
from collections import namedtuple

Person = namedtuple("Person", ["name", "age", "country"])
alice = Person("Alice", 30, "USA")
print(alice.name)  # 输出 "Alice"
```

## 7. 集合操作符

Python的集合操作符（`|`、`&`、`-`等）允许你执行集合的并集、交集和差集操作，而不需要显式编写循环。这可以大大简化代码，同时提高性能。

示例：

```python
a = {1, 2, 3}
b = {3, 4, 5}

union = a | b  # 并集 {1, 2, 3, 4, 5}
intersection = a & b  # 交集 {3}
difference = a - b  # 差集 {1, 2}
```

## 8. 使用functools库的lru_cache

`functools`库中的`lru_cache`是一个强大的功能，可以缓存函数的调用结果，以避免重复计算。这对于需要频繁调用的函数非常有用，可以显著提高性能。

示例：

```python
from functools import lru_cache

@lru_cache(maxsize=None)  # 缓存所有调用结果
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

## 9. 使用enumerate()迭代列表

`enumerate()`是一个方便的功能，可以同时访问列表的索引和值。这在需要迭代列表时非常有用。

示例：

```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

## 10. 使用collections库的Counter

`Counter`是`collections`库中的一个功能，用于统计可迭代对象中元素的出现次数。这对于分析数据和计数频率非常有用。

示例：

```python
from collections import Counter

data = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
count = Counter(data)
print(count[3])  # 输出 3
```

以上是Python中一些容易被忽视的核心功能，它们可以大幅改善代码质量、可读性和性能。通过深入了解和应用这些功能，可以成为更高效的Python开发者，并写出更出色的Python代码。希望这些示例和解释能帮助你更好地掌握这些功能，将它们应用到日常编程工作中。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
