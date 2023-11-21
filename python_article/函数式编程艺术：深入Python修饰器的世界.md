![](https://p.ipic.vip/cfnkto.png)

Python的修饰器（Decorators）是一项强大的函数式编程工具，用于增强函数的功能或修改其行为。修饰器允许在不修改原始函数代码的情况下，动态地添加功能。

本文将详细介绍Python修饰器的概念，提供详细的示例，并介绍如何使用它们来优化和扩展代码。

## 什么是修饰器？

修饰器是Python中的一种高阶函数，它接受一个函数作为输入，并返回一个新的函数。这个新函数通常会包装原始函数，可以在调用原始函数之前或之后执行额外的操作。

修饰器的主要特点包括：

- 修饰器是函数。
- 修饰器接受一个函数作为参数。
- 修饰器返回一个新的函数，通常是原始函数的包装器。
- 修饰器允许您在不修改原始函数代码的情况下，添加额外的功能。

修饰器是Python中的一种元编程技术，可以将通用功能提取到可重用的装饰器函数中，从而实现更干净和可维护的代码。

## 基本修饰器示例

让我们从一个基本的修饰器示例开始，以更好地理解它们的工作原理。

假设有一个简单的函数，用于打印一条欢迎消息：

```python
def welcome():
    return "Welcome to our website!"
```

现在，想要创建一个修饰器，可以在欢迎消息前后添加一些额外的文本。

下面是一个简单的修饰器函数：

```python
def decorate_welcome(func):
    def wrapper():
        return "**********\n" + func() + "\n**********"
    return wrapper
```

在这个示例中，`decorate_welcome`是一个接受函数作为参数的修饰器函数。返回一个新的函数`wrapper`，该函数在原始`welcome`函数的输出前后添加了装饰文本。

可以使用`@`符号将修饰器应用于我们的`welcome`函数：

```python
@decorate_welcome
def welcome():
    return "Welcome to our website!"
```

当调用`welcome()`时，实际上调用了`wrapper()`，它包装了原始的`welcome`函数。

这将在欢迎消息前后添加装饰文本：

```python
result = welcome()
print(result)
```

输出：

```
**********
Welcome to our website!
**********
```

这是一个简单的修饰器示例，但它展示了修饰器的基本概念：它们包装原始函数，在调用前后执行额外的操作。

## 修饰器的应用场景

修饰器是Python中非常强大且灵活的工具，可以应用于多种场景，包括：

### 1. 认证和授权

修饰器可用于验证用户身份或授权用户对特定资源的访问。例如，可以创建一个身份验证修饰器，以确保用户已登录并具有适当的权限。

### 2. 缓存

修饰器可用于缓存函数的结果，以提高性能。通过将函数的参数和结果存储在缓存中，可以避免多次计算相同的结果。

### 3. 记录和日志

修饰器可以用于记录函数的调用和执行时间，从而帮助调试和性能分析。

### 4. 输入验证

修饰器可用于验证函数的输入参数，确保它们满足预期的条件。

### 5. 事务管理

在数据库操作中，修饰器可用于管理事务，确保一组相关操作要么全部成功，要么全部失败。

### 6. 性能优化

修饰器可以用于优化函数的性能，如并行处理、延迟加载等。

### 7. 错误处理

修饰器可以用于捕获函数中的异常，并执行适当的错误处理操作。

### 8. 类方法修饰

除了函数修饰器，Python还支持修饰类方法。这些修饰器可用于修改类方法的行为，如限制访问、添加验证等。



## 常用修饰器

Python有一些内置的修饰器，可用于常见任务。以下是其中一些：

### @staticmethod

这个修饰器用于声明一个静态方法。静态方法与类的实例无关，可以通过类本身调用。

```python
class MyClass:
    @staticmethod
    def static_method():
        print("This is a static method")

# 调用静态方法
MyClass.static_method()
```

### @classmethod

这个修饰器用于声明一个类方法。类方法的第一个参数通常是`cls`，用于引用类本身。

```python
class MyClass:
    class_variable = 0
    
    def __init__(self, value):
        self.instance_variable = value
    
    @classmethod
    def class_method(cls):
        cls.class_variable += 1

# 调用类方法
obj1 = MyClass(1)
obj2 = MyClass(2)
MyClass.class_method()
print(MyClass.class_variable)  # 输出：1
```

### @property

这个修饰器用于将方法转化为属性，使其可以像访问属性一样调用。

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def diameter(self):
        return 2 * self._radius

# 访问属性
circle = Circle(5)
print(circle.diameter)  # 输出：10
```

### @staticmethod vs @classmethod vs @property

上面介绍的三个内置修饰器在使用时有一些区别：
- `@staticmethod`用于定义静态方法，不需要引用实例或类，直接调用。
- `@classmethod`用于定义类方法，需要引用类本身，通常用于修改类级别的属性。
- `@property`用于定义属性，允许方法像属性一样被访问。

## 自定义修饰器

除了内置修饰器，还可以创建自定义修饰器。自定义修饰器是普通函数，接受一个函数作为参数并返回一个新函数。

下面是一个示例，演示如何创建一个自定义修饰器来测量函数的执行时间：

```python
import time

def measure_time(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"{func.__name__} executed in {end_time - start_time:.4f} seconds")
        return result
    return wrapper

@measure_time
def time_consuming_function():
    # 模拟耗时操作
    time.sleep(2)

time_consuming_function()
```

这个自定义修饰器`measure_time`在函数执行前记录开始时间，函数执行后记录结束时间，并输出执行时间。通过将`@measure_time`应用于`time_consuming_function`，可以轻松地测量它的执行时间。

## 堆叠多个修饰器

堆叠多个修饰器，以便在一个函数上应用多个功能。修饰器的顺序很重要，它们按从上到下的顺序执行。

下面是一个堆叠多个修饰器的示例：

```python
def decorator1(func):
    def wrapper(*args, **kwargs):
        print("Decorator 1: Before function execution")
        result = func(*args, **kwargs)
        print("Decorator 1: After function execution")
        return result
    return wrapper

def decorator2(func):
    def wrapper(*args, **kwargs):
        print("Decorator 2: Before function execution")
        result = func(*args, **kwargs)
        print("Decorator 2: After function execution")
        return result
    return wrapper

@decorator1
@decorator2
def my_function():
    print("Function is executed")

my_function()
```

输出：
```
Decorator 1: Before function execution
Decorator 2: Before function execution
Function is executed
Decorator 2: After function execution
Decorator 1: After function execution
```

在这个示例中，`my_function`上堆叠了两个修饰器，它们按照装饰器的顺序执行。这使得修饰器的组合非常灵活，可以应用多个功能，同时保持代码的清晰性。

## 常见修饰器的应用

让我们看一些常见修饰器的应用场景。

### 1. 缓存修饰器

缓存修饰器可用于缓存函数的结果，以提高性能。通过将函数参数和结果存储在一个字典中，以避免多次计算相同的结果。

下面是一个简单的缓存修饰器示例：

```python
def cache(func):
    cached_results = {}
    def wrapper(*args):
        if args in cached_results:
            print(f"Cache hit for {func.__name__}({args})")
            return cached_results[args]
        result = func(*args)
        cached_results[args] = result
        print(f"Cache miss for {func.__name__}({args}), result cached")
        return result
    return wrapper

@cache
def fibonacci(n):
    if n < 2:
        return n
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

fibonacci(5)
```

在这个示例中，使用`cache`修饰器来缓存`fibonacci`函数的结果，以避免多次计算相同的斐波那契数。修饰器在内部使用`cached_results`字典来存储结果，实现了缓存功能。

### 2. 认证和授权修饰器

认证和授权修饰器可用于验证用户的身份和授权用户对某些资源的访问。这在Web应用程序中特别有用。

下面是一个简单的认证修饰器示例：

```python
def authenticate(username, password):
    authorized_users = {"user1": "password1", "user2": "password2"}
    if username in authorized_users and authorized_users[username] == password:
        return True
    else:
        return False

def requires_authentication(func):
    def wrapper(*args, **kwargs):
        username = input("Enter your username: ")
        password = input("Enter your password: ")
        if authenticate(username, password):
            return func(*args, **kwargs)
        else:
            return "Authentication failed. Access denied."
    return wrapper

@requires_authentication
def sensitive_info():
    return "This is sensitive information."

result = sensitive_info()
print(result)
```

在这个示例中，`requires_authentication`修饰器需要用户输入用户名和密码，然后验证用户的身份。只有通过身份验证的用户才能访问`@requires_authentication`修饰的函数。

### 3. 日志修饰器

日志修饰器用于记录函数的调用和执行时间。这对于跟踪程序的执行流程和性能分析非常有用。

下面是一个简单的日志修饰器示例：

```python
import time

def log_execution_time(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        execution_time = end_time - start_time
        print(f"{func.__name__} executed in {execution_time:.4f} seconds")
        return result
    return wrapper

@log_execution_time
def slow_function():
    time.sleep(2)

slow_function()
```

这个示例中，`log_execution_time`修饰器记录了`slow_function`的执行时间，并在执行后打印出来。

## 总结

Python的修饰器是一项强大的功能，可以显著提高代码的可维护性、可读性和性能。本文深入学习修饰器的工作原理，以及如何创建和使用它们。我们学习了不同类型的修饰器，包括函数修饰器、类修饰器和属性修饰器，每种类型都有其独特的用途和应用场景。

通过大量的示例代码和案例，展示了修饰器如何用于日常编程中，从简化日志记录和身份验证到性能优化和代码重用。这些示例可以更好地理解如何自定义修饰器以满足其特定需求，同时保持代码的简洁和可读性。

修饰器不仅是Python编程的一种强大工具，还是提高代码质量和效率的关键方法。在不断学习和实践的过程中，读者将能够更好地编写高质量、可维护和高性能的Python代码。所以，不论是新手还是有经验的Python开发者，都可以受益于深入了解和利用Python修饰器的知识。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)

