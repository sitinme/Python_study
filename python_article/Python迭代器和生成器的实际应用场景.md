![](https://p.ipic.vip/cfnkto.png)

在Python中，迭代器（Iterators）和生成器（Generators）是两个关键的概念，为我们提供了强大的工具，用于处理各种数据序列。

迭代器和生成器不仅使我们能够更有效地操作数据，还可以大大减少内存占用，尤其在处理大型数据集时表现突出。

## 迭代器（Iterators）

### 什么是迭代器？

迭代器是一种特殊的对象，可以在数据序列上进行迭代。它可以让你逐个访问序列中的元素，而无需将整个序列加载到内存中。Python中的大多数数据结构都可以用作可迭代对象，例如列表、元组、字符串等。

### 迭代器协议

迭代器对象必须遵守以下两个方法：

- `__iter__()`: 返回迭代器自身。
- `__next__()`: 返回序列中的下一个元素。如果没有元素可供迭代，引发`StopIteration`异常。

示例代码，演示如何创建一个自定义的迭代器：

```python
class MyIterator:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.end:
            self.current += 1
            return self.current - 1
        raise StopIteration

# 使用自定义迭代器
my_iterator = MyIterator(0, 3)
for item in my_iterator:
    print(item)  # 输出0, 1, 2
```

### 迭代器与`for`循环

Python中的`for`循环用于迭代可迭代对象中的元素。当我们使用`for`循环时，会自动调用可迭代对象的`__iter__()`方法，并使用`__next__()`方法来遍历元素，直到引发`StopIteration`异常。

```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)  # 输出1, 2, 3, 4, 5
```

### 可迭代对象

可迭代对象是实现了`__iter__()`方法的对象，可以被用作迭代器的基础。Python标准库中有许多内置的可迭代对象，例如`range()`、`enumerate()`、`zip()`等。

## 生成器（Generators）

### 什么是生成器？

生成器是一种特殊类型的迭代器，允许你按需生成值，而不是一次性生成所有值。

这种按需生成的方式非常有用，尤其是在处理大量数据时，以减少内存占用和提高性能。

### 生成器函数

生成器函数是包含`yield`语句的函数，而不是`return`。当函数包含`yield`语句时，它变成了一个生成器函数。每次调用生成器的`__next__()`方法时，函数会从上次`yield`的位置继续执行，直到遇到下一个`yield`或函数结束。

让我们看一个示例，演示如何创建一个生成器函数：

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1

# 使用生成器函数
for i in countdown(5):
    print(i)  # 输出5, 4, 3, 2, 1
```

### 生成器表达式

生成器表达式类似于列表推导式，但它返回一个生成器对象，而不是一次性生成所有元素。在处理大量数据时非常有用。

```python
# 生成器表达式示例
even_numbers = (x for x in range(10) if x % 2 == 0)
for num in even_numbers:
    print(num)  # 输出0, 2, 4, 6, 8
```

### 生成器的惰性求值

生成器以惰性方式生成数据，只有在需要时才计算和返回数据。这意味着生成器不会一次性生成所有值，从而减少内存占用。

### 生成器的无限序列

由于生成器的惰性求值，可以创建无限序列，而不必担心内存问题。例如，生成无限的斐波那契数列：

```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

# 生成无限的斐波那契数列
fib = fibonacci()
for _ in range(10):
    print(next(fib))  # 输出0, 1, 1, 2, 3, 5, 8, 13, 21, 34
```

## Python的迭代器与生成器 的区别和联系

Python的迭代器（Iterators）和生成器（Generators）都是用于处理数据序列的概念，但在工作方式、用途和实现上有一些重要的区别和联系。

### 区别：

**1. 工作方式：**
   - 迭代器：迭代器是一个对象，实现了`__iter__()`和`__next__()`方法。通过调用`__iter__()`方法，可以获得迭代器自身，然后通过反复调用`__next__()`方法来逐个访问序列中的元素。
   - 生成器：生成器是一种特殊的迭代器，通过函数定义中包含`yield`语句来创建的。生成器函数在每次调用`yield`时会暂停并保留当前的状态，下次调用时会从上次暂停的位置继续执行。

**2. 内存占用：**
   - 迭代器：迭代器需要在内存中保存整个序列，如果序列很大，可能会占用大量内存。
   - 生成器：生成器以惰性求值的方式生成数据，只在需要时计算和返回值，因此内存占用较低，特别适用于处理大型数据集。

**3. 实现方式：**
   - 迭代器：可以自定义迭代器类，实现`__iter__()`和`__next__()`方法来定义迭代行为。此外，Python提供了很多内置的可迭代对象和迭代器，如列表、元组、字符串等。
   - 生成器：生成器可以通过生成器函数（包含`yield`语句）或生成器表达式（类似于列表推导式）来创建。生成器函数是一种更灵活的方式，可以动态生成值。

### 联系：

**1. 都用于处理数据序列：** 迭代器和生成器都用于处理数据序列，允许逐个访问元素而不必一次性加载整个序列。

**2. 都可以用于`for`循环：** 可以将迭代器和生成器用于`for`循环，这是常见用途。`for`循环会自动调用迭代器的`__next__()`方法来遍历序列中的元素。

**3. 都可以实现惰性求值：** 迭代器和生成器都支持惰性求值，只在需要时计算和返回值，这有助于节省内存。

**4. 都可以创建无限序列：** 可以使用生成器来创建无限序列，而迭代器也可以用于处理无限序列的数据。

### 示例：

示例代码，展示迭代器和生成器之间的区别和联系：

```python
# 迭代器示例
class MyIterator:
    def __init__(self, start, end):
        self.current = start
        self.end = end

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.end:
            self.current += 1
            return self.current - 1
        raise StopIteration

# 生成器示例
def countdown(n):
    while n > 0:
        yield n
        n -= 1

# 使用迭代器
my_iterator = MyIterator(0, 3)
for item in my_iterator:
    print(item)  # 输出0, 1, 2

# 使用生成器
for i in countdown(5):
    print(i)  # 输出5, 4, 3, 2, 1
```

在这个示例中，展示了如何使用自定义迭代器和生成器函数来处理数据序列。尽管在实现方式上不同，但都能够逐个访问元素并支持惰性求值。

## 总结

迭代器是Python中最基本的迭代工具，允许我们逐个访问数据序列的元素，而不需要一次性加载整个序列到内存中。

生成器则将迭代提升到了一个全新的层次，它们以一种更加灵活和高效的方式生成数据，只在需要时计算，极大地提高了性能。

深入学习迭代器和生成器的工作原理、用途和示例，帮助你全面了解这两个重要概念，并在实际编程中合理地选择它们以应对各种数据处理任务。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
