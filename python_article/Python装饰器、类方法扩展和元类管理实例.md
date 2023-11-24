![](https://p.ipic.vip/cfnkto.png)

## 1. Python装饰器

### 装饰器简介

装饰器是一种函数，用于修改其他函数的行为。它们允许在调用函数之前或之后执行某些代码，而无需修改函数本身。

### 装饰器的基本用法

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

### 装饰器的高级用法

#### 装饰器链
```python
def decorator_one(func):
    def wrapper():
        print("Decorator One - Before")
        func()
        print("Decorator One - After")
    return wrapper

def decorator_two(func):
    def wrapper():
        print("Decorator Two - Before")
        func()
        print("Decorator Two - After")
    return wrapper

@decorator_one
@decorator_two
def say_hello():
    print("Hello!")

say_hello()
```

#### 带参数的装饰器
```python
def parametrized_decorator(param):
    def real_decorator(func):
        def wrapper(*args, **kwargs):
            print(f"Decorator parameter: {param}")
            func(*args, **kwargs)
        return wrapper
    return real_decorator

@parametrized_decorator("Custom Param")
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")
```


## 2. 类方法扩展

### 类方法简介

类方法是属于类而不是实例的方法，通过`@classmethod`装饰器声明。它们允许对类本身执行操作，而不是对实例执行操作。

### 扩展类方法的常用方式

```python
class MyClass:
    @classmethod
    def my_class_method(cls):
        print("This is a class method.")

def extend_class_method(func):
    def wrapper():
        print("Do something before executing the method.")
        func()
        print("Do something after executing the method.")
    return wrapper

# Applying decorator to a class method
MyClass.my_class_method = extend_class_method(MyClass.my_class_method)
```
### 扩展类方法的常用方式

#### 对类方法应用装饰器
```python
class MyClass:
    @classmethod
    def my_class_method(cls):
        print("This is a class method.")

def extend_class_method(func):
    def wrapper():
        print("Do something before executing the method.")
        func()
        print("Do something after executing the method.")
    return wrapper

# Applying decorator to a class method
MyClass.my_class_method = extend_class_method(MyClass.my_class_method)
MyClass.my_class_method()
```

## 3. 元类管理实例

### 元类简介

元类是类的类，用于控制类的创建。它允许在定义类时定制类的行为。

### 元类用于管理类的行为

```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        # Modify or enhance class behavior before it's created
        return super().__new__(cls, name, bases, dct)

class MyClass(metaclass=Meta):
    def my_method(self):
        print("This is a method inside MyClass.")
```

## 总结

本文介绍了Python装饰器、类方法扩展和元类的基本概念。装饰器可用于在函数执行前后添加功能。类方法扩展允许对类方法的行为进行定制。元类提供了对类的创建过程进行定制的能力。深入理解这些概念可以更好地理解Python中的高级编程技术。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
