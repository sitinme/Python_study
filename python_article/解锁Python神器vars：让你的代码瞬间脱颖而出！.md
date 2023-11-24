![](https://p.ipic.vip/cfnkto.png)

`vars()`函数是一个内置函数，用于返回对象的__字典__，其中包含对象的__属性__。它适用于模块、类和实例对象，为你提供了访问对象属性的便捷方式。

## 1. `vars()` 函数概述

`vars()`函数有两种使用方式：
- **不带参数**：返回当前作用域的 `__dict__`。
- **带参数**：返回对象的 `__dict__` 属性。

## 2. 使用 `vars()` 函数的示例

### 示例 1: 在模块中使用 `vars()`

```python
# 创建一个模块
# file: my_module.py

var_in_module = "I'm in the module!"

def my_function():
    print("This is a function inside the module.")
```

```python
# 主程序中使用 vars() 查看模块的属性

import my_module

# 查看模块的属性
print(vars(my_module))
# Output: {'__name__': 'my_module', '__doc__': None, 'var_in_module': "I'm in the module!", 'my_function': <function my_function at 0x7fbb42a6b670>, ...}
```

### 示例 2: 在类中使用 `vars()`

```python
class MyClass:
    class_var = "I am a class variable"

    def __init__(self):
        self.instance_var = "I am an instance variable"

obj = MyClass()

# 访问类和实例属性
print(vars(MyClass))
# Output: {'__module__': '__main__', 'class_var': 'I am a class variable', ...}
print(vars(obj))
# Output: {'instance_var': 'I am an instance variable'}
```

### 示例 3: 在实例对象中使用 `vars()`

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def update_age(self, new_age):
        self.age = new_age

person = Person("Alice", 30)

# 获取实例属性
print(vars(person))
# Output: {'name': 'Alice', 'age': 30}
```

### 示例 4: 使用 `vars()` 动态添加对象属性

```python
class Dog:
    def __init__(self, name):
        self.name = name

dog = Dog("Buddy")

# 添加新属性
vars(dog)['breed'] = "Labrador"

print(vars(dog))
# Output: {'name': 'Buddy', 'breed': 'Labrador'}
```

## 3. 使用 `vars()` 函数的注意事项

- 不是所有对象都有 `__dict__` 属性，因此并非所有对象都能使用 `vars()` 函数。
- `vars()` 返回的是对象的 `__dict__` 的引用，因此对返回的字典的更改会影响到原始对象。
- 在某些情况下，对象的 `__dict__` 属性是只读的，尝试更改它可能会导致错误。

`vars()` 函数是Python中强大而多用途的函数之一。它可以帮助你动态地查看和操作对象的属性。通过了解它的用法，你可以更好地利用它来简化代码和探索对象的结构。

## 4. 更深入的应用和用例

### a. 动态查看对象属性

```python
class Car:
    def __init__(self, brand, model, year):
        self.brand = brand
        self.model = model
        self.year = year

my_car = Car("Toyota", "Corolla", 2020)

# 使用 vars() 动态查看对象属性
car_vars = vars(my_car)
print(car_vars)
# Output: {'brand': 'Toyota', 'model': 'Corolla', 'year': 2020}
```

### b. 动态创建对象属性

```python
class Laptop:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

my_laptop = Laptop("Dell", "Inspiron")

# 动态创建新属性
vars(my_laptop)['specs'] = {'RAM': '8GB', 'Storage': '256GB SSD'}

print(vars(my_laptop))
# Output: {'brand': 'Dell', 'model': 'Inspiron', 'specs': {'RAM': '8GB', 'Storage': '256GB SSD'}}
```

## 5. `vars()` 和 `__slots__` 的关系

在某些情况下，对象使用`__slots__`属性而不是`__dict__`来存储实例变量。对于这些对象，`vars()`函数不能直接使用，因为它们不具备`__dict__`属性。

```python
class Book:
    __slots__ = ('title', 'author')

    def __init__(self, title, author):
        self.title = title
        self.author = author

my_book = Book("Python 101", "John Doe")

# 尝试使用 vars() 查看对象属性会引发 AttributeError
# vars(my_book)
# Output: AttributeError: 'Book' object has no attribute '__dict__'
```

## 6. 使用 `vars()` 进行动态调试

`vars()`函数在调试过程中非常有用，它可以帮助你动态地检查对象的属性，特别是在处理复杂的数据结构时。

```python
# 在调试中使用 vars() 检查对象属性
class User:
    def __init__(self, username, email):
        self.username = username
        self.email = email

user = User("johndoe", "johndoe@example.com")

# 在调试中输出对象属性
def some_function():
    # 在函数中动态检查对象属性
    user_vars = vars(user)
    print(user_vars)
    # Output: {'username': 'johndoe', 'email': 'johndoe@example.com'}

some_function()
```

## 总结

`vars()`函数是Python中一个功能强大且多用途的工具，它让你能够动态地查看和操作对象的属性。它适用于模块、类和实例对象，让你更好地理解对象的内部结构。

通过了解和熟练使用`vars()`函数，可以更高效地编写代码，进行调试和探索Python对象。然而，需要注意，并非所有对象都具有`__dict__`属性，而对于`__slots__`来说，`vars()`函数也不能直接使用。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
