![](https://p.ipic.vip/cfnkto.png)

在Python中，类属性和实例属性是面向对象编程的核心概念之一。它们允许存储和管理对象的数据，并影响对象的行为。

本篇文章中，会学习到类属性和实例属性的概念、区别以及如何在Python中使用它们，同时提供大量的示例代码来更好地理解它们的作用和用法。

## 一、理解类属性和实例属性

### 1.1 什么是类属性？

类属性是与类相关联的属性。它们属于类本身，而不是类的任何特定实例。这意味着无论创建多少个类的实例，它们都会共享相同的类属性。类属性通常位于类的顶部，定义在类的任何方法之外。

类属性的一个常见用途是存储与类相关的常量或共享的状态信息。例如，可以在类属性中存储数据库连接信息、默认配置或类的共享状态。

### 1.2 什么是实例属性？

实例属性是与类的每个实例相关联的属性。每个类的实例都可以拥有自己的一组实例属性。实例属性通常在类的构造方法（通常是`__init__`方法）内定义，并使用`self`关键字来访问。

实例属性的一个重要特点是每个实例都有自己独立的一组实例属性。这意味着一个实例的属性值可以与另一个实例不同，它们互不影响。

### 1.3 区别总结

让我们总结一下类属性和实例属性的主要区别：

- 类属性属于类本身，而实例属性属于类的每个实例。
- 所有类的实例共享相同的类属性，而每个实例都有自己独立的实例属性。
- 类属性通常用于存储与类相关的常量或共享状态，而实例属性通常用于存储每个实例特有的数据。


## 二、示例代码

### 2.1 类属性的示例

```python
class Dog:
    # 类属性
    species = "Canis familiaris"

    def __init__(self, name, age):
        self.name = name  # 实例属性
        self.age = age    # 实例属性

# 创建两个实例
buddy = Dog("Buddy", 9)
miles = Dog("Miles", 4)

# 访问实例属性
print(f"{buddy.name} is {buddy.age} years old.")
print(f"{miles.name} is {miles.age} years old.")

# 访问类属性
print(f"{buddy.name} is a {buddy.species}.")
print(f"{miles.name} is also a {miles.species}.")
```

在上面的示例中，`species`是一个类属性，它属于`Dog`类本身，因此所有`Dog`类的实例共享相同的`species`值。而`name`和`age`是实例属性，每个`Dog`实例都有自己独立的`name`和`age`属性。

### 2.2 实例属性的示例

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make      # 实例属性
        self.model = model    # 实例属性
        self.year = year      # 实例属性

    def display_info(self):
        return f"{self.year} {self.make} {self.model}"

# 创建两个Car实例
car1 = Car("Toyota", "Camry", 2022)
car2 = Car("Honda", "Civic", 2021)

# 访问实例属性和调用方法
print(car1.display_info())  # 输出：2022 Toyota Camry
print(car2.display_info())  # 输出：2021 Honda Civic
```

在上面的示例中，`make`、`model`和`year`都是`Car`类的实例属性，每个`Car`实例都有自己独立的属性值。

## 三、类属性 vs 实例属性的用途

### 3.1 类属性的常见用途

- 存储常量和配置信息：可以使用类属性来存储与类相关的常量值或默认配置信息。例如，存储数学常数、API密钥或默认设置。
- 共享状态信息：如果需要在所有类的实例之间共享某种状态信息，类属性是一个合适的选择。例如，可以使用类属性来记录创建的实例数量。

### 3.2 实例属性的常见用途

- 存储对象的状态：实例属性通常用于存储对象的状态信息。例如，如果创建一个代表用户的类，那么每个用户对象可以有自己的用户名、电子邮件地址等属性。
- 存储对象特定的数据：每个实例可以拥有自己独立的数据。例如，如果创建一个代表图书的类，每本书可以有自己的标题、作者和出版日期。

## 四、动态修改类属性和实例属性

在Python中，可以动态地修改类属性和实例属性。意思是可以在对象的生命周期中根据需要更改属性的值。

### 4.1 修改类属性

```python
class MyClass:
    class_attr = 42  # 类属性

# 修改类属性的值
MyClass.class_attr = 100

# 创建类的实例
obj = MyClass()

# 访问类属性
print(obj.class_attr)  # 输出：100
```

在上面的示例中，首先定义了一个类属性`class_attr`，然后在创建类的实例后，通过类名访问类属性并修改了它的值。

### 4.2 修改实例属性

```python
class Person:
    def __init__(self, name):
        self.name = name  # 实例属性

# 创建一个实例
person = Person("Alice")

# 修改实例属性的值
person.name = "Bob"

# 访问实例属性
print(person.name)  # 输出：Bob
```

在上面的示例中，首先创建了一个实例属性`name`，然后通过实例来修改了它的值。

## 总结

在Python中，类属性和实例属性是管理对象数据的重要工具。

不同的作用范围和用途：

- 类属性属于类本身，而实例属性属于类的每个实例。
- 类属性通常用于存储与类相关的常量或共享状态信息。
- 实例属性用于存储每个实例特有的数据和状态信息。

理解和正确使用类属性和实例属性对于面向对象编程非常重要。根据需求，选择使用类属性、实例属性或两者结合来实现对象的设计和行为。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
