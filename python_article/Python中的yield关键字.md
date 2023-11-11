![](https://p.ipic.vip/cfnkto.png)

在Python中，`yield`是一个重要的关键字，它与生成器（Generator）和懒惰计算（Lazy Evaluation）密切相关。

`yield`允许函数在迭代过程中产生值，而不必一次性将所有值计算出来。这种特性在处理大数据集或无限序列时尤其有用。

## 一、`yield`关键字

### 1.1 `yield`的基本概念

`yield`是一个关键字，用于定义生成器函数。生成器函数可以被暂停和恢复，允许逐个生成值而不需要一次性计算所有值。当生成器函数执行到`yield`语句时，它将生成一个值，并保存其状态，然后等待下一次调用来继续执行。

### 1.2 生成器的工作原理

生成器是一种特殊类型的迭代器，由生成器函数创建。生成器函数包含至少一个`yield`语句，它可以返回一个值，并在下一次迭代时从`yield`语句处继续执行。这允许生成器函数的状态保持不变，而值可以逐个生成。

以下是一个简单的生成器函数示例：

```python
def simple_generator():
    yield 1
    yield 2
    yield 3

gen = simple_generator()
print(next(gen))  # 输出：1
print(next(gen))  # 输出：2
print(next(gen))  # 输出：3
```

示例中，`simple_generator`是一个生成器函数，它包含三个`yield`语句。当我们创建生成器对象`gen`并调用`next()`函数时，生成器函数在每次调用后从`yield`语句处继续执行，并生成相应的值。

## 二、创建生成器

### 2.1 生成器函数

生成器函数是一种包含`yield`语句的函数，用于生成值。生成器函数的执行可以被多次暂停和继续，每次暂停都会生成一个值。

以下是一个生成器函数的示例，用于生成斐波那契数列：

```python
def fibonacci_generator():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

gen = fibonacci_generator()
for _ in range(10):
    print(next(gen))  # 输出前10个斐波那契数
```

### 2.2 生成器表达式

除了生成器函数，Python还提供了生成器表达式，它类似于列表推导式，但是返回一个生成器对象，逐个生成值。生成器表达式的语法更紧凑。

以下是一个生成器表达式的示例，用于生成自然数的平方：

```python
gen = (x**2 for x in range(1, 6))
for value in gen:
    print(value)  # 输出：1 4 9 16 25
```

生成器表达式可以在不创建额外的函数的情况下生成值，适用于简单的迭代需求。

## 三、`yield`的高级用法

### 3.1 生成器的状态保存

生成器函数在每次执行时都会保持其状态。这意味着它可以用于生成无限序列或大数据集，而不必将所有数据存储在内存中。

以下是一个无限递增的生成器示例：

```python
def infinite_increment():
    num = 0
    while True:
        yield num
        num += 1

gen = infinite_increment()
for _ in range(5):
    print(next(gen))  # 输出：0 1 2 3 4
```

### 3.2 生成器的数据过滤

`yield`可以与条件结合使用，用于过滤生成的值。这允许生成器仅生成符合特定条件的值。

以下是一个示例，生成偶数的生成器：

```python
def even_numbers():
    num = 0
    while True:
        if num % 2 == 0:
            yield num
        num += 1

gen = even_numbers()
for _ in range(5):
    print(next(gen))  # 输出：0 2 4 6 8
```

### 3.3 生成器的懒惰计算

生成器的懒惰计算是一种在需要时计算值的方式，而不是一次性计算所有值。这在处理大型数据集或无限序列时非常有用。

以下是一个示例，生成自然数的平方，但只计算前5个：

```python
def lazy_square(limit):
    for x in range(1, limit + 1):
        yield x**2

gen = lazy_square(5)
for value in gen:
    print(value)  # 输出：1 4 9 16 25
```

懒惰计算允许在处理大量数据时节省内存和计算资源。

## 总结

yield的高级用法包括生成器的状态保存，允许无限递增或递减的生成器。还可以与条件结合使用，用于过滤生成的值，仅生成符合特定条件的值。最重要的是，yield支持懒惰计算，允许在需要时计算值，而不是一次性计算所有值，从而节省内存和计算资源。

在处理大型数据集、无限序列或需要逐个生成值的情况下，yield是一个强大的工具。通过深入理解yield，可以更好地利用生成器和懒惰计算，提高代码的效率和可维护性。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
