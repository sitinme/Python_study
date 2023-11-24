![](https://p.ipic.vip/cfnkto.png)

在 Python 中，`def` 是用于定义函数的关键字。本文将深入介绍 `def` 的用法和特点，详细说明如何定义函数、传递参数、返回值以及更复杂的用法。

## 1. 定义函数

`def` 语句用于定义函数，以下是一个简单的示例:

```python
def greet():
    print("Hello, welcome to Python functions!")
```

## 2. 参数传递

函数可以接收参数，用于在函数内部执行特定的操作。以下是一个带参数的函数示例：

```python
def greet_with_name(name):
    print(f"Hello, {name}! Welcome to Python functions.")
```

## 3. 默认参数

函数可以设定默认参数值，在调用函数时，如果没有传入参数，将使用默认值。

```python
def greet_with_default(name="Guest"):
    print(f"Hello, {name}! Welcome to Python functions.")
```

## 4. 返回值

函数可以返回数值、对象或其他类型的数据。使用 `return` 关键字来指定返回值。

```python
def add(a, b):
    return a + b
```

## 5. 多个返回值

Python 中的函数可以返回多个值，这些值以元组的形式被返回。

```python
def arithmetic_operations(a, b):
    return a + b, a - b, a * b, a / b
```

## 6. 匿名函数

使用 `lambda` 关键字可以创建匿名函数，也被称为 Lambda 函数。

```python
multiply = lambda x, y: x * y
print(multiply(5, 3))  # 输出 15
```

## 7. 函数作为参数

函数可以作为其他函数的参数，这在函数式编程中非常常见。

```python
def square(x):
    return x * x

def process(func, data):
    return [func(x) for x in data]

numbers = [1, 2, 3, 4, 5]
squared_numbers = process(square, numbers)
print(squared_numbers)  # 输出 [1, 4, 9, 16, 25]
```

## 8. 递归

函数可以调用自身，这种方法被称为递归。

下面是一个简单的递归示例。

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n - 1)
```

## 9. 嵌套函数

Python 允许在函数内部定义其他函数，这就是所谓的嵌套函数。

```python
def outer_function():
    print("Outer function")

    def inner_function():
        print("Inner function")

    inner_function()
```

## 10. 函数装饰器

装饰器是一个强大的工具，用于修改函数或方法的行为。它们是由 `@` 符号和一个函数名组成。

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```

## 总结

`def` 是 Python 中定义函数的关键字，它承担着定义、接收参数、返回数值、递归、嵌套函数和装饰器等多种功能。定义函数是编写模块化、可重用代码的基础。通过 `def`，我们能够创建简单的函数、带参数的函数甚至带有默认参数值的函数。函数还可以返回数值或元组，允许多个返回值。匿名函数或 Lambda 函数以及递归函数也是 `def` 的一部分。嵌套函数让我们在一个函数内部定义另一个函数，提供了更好的封装性。另外，函数装饰器为函数的行为增添了灵活性，允许在函数的前后执行额外操作。

掌握 `def` 语句的多种用法能够让程序更加模块化、可读性更强，提高代码的可维护性。函数的复杂性和多功能性使得 Python 成为一个非常强大和灵活的编程语言，为程序员提供了丰富的工具和方法。深入了解并熟练使用 `def` 的各种特性将为开发者带来更多的灵活性和效率，帮助解决多样化的编程需求。 `def` 不仅仅是一个定义函数的关键字，更是开启 Python 强大编程特性的大门。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
