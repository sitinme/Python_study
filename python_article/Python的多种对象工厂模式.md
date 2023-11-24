![](https://p.ipic.vip/cfnkto.png)

## 简介

对象工厂模式是一种设计模式，它用于创建对象的实例。在Python中，有几种常见的对象工厂模式，包括工厂方法、抽象工厂和简单工厂。这些模式旨在提供更灵活的方法来实例化对象，使代码更易于维护和扩展。

### 优点：
- 封装对象创建的细节，降低耦合度。
- 提供灵活性，使得对象的创建更易于管理。
- 可以根据需求轻松扩展和修改对象创建的方式。

## 工厂方法模式

工厂方法模式基于继承，使用抽象类定义创建对象的接口，由其子类决定实际创建的对象。

### 理念说明：
工厂方法模式使得基类拥有一个抽象工厂方法，由具体的子类来实现这个方法，根据具体的需求创建对象。

### 代码示例：
```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def make_sound(self):
        pass

class Dog(Animal):
    def make_sound(self):
        return "Woof!"

class Cat(Animal):
    def make_sound(self):
        return "Meow!"

class AnimalFactory(ABC):
    @abstractmethod
    def create_animal(self):
        pass

class DogFactory(AnimalFactory):
    def create_animal(self):
        return Dog()

class CatFactory(AnimalFactory):
    def create_animal(self):
        return Cat()

dog_factory = DogFactory()
cat_factory = CatFactory()

dog = dog_factory.create_animal()
cat = cat_factory.create_animal()

print(dog.make_sound())  # 输出: Woof!
print(cat.make_sound())  # 输出: Meow!
```

## 抽象工厂模式

抽象工厂模式允许创建一组相关对象，而无需指定具体类。

### 理念说明：
抽象工厂模式用于创建一组相关对象，例如家族中不同产品的创建。

### 代码示例：
```python
from abc import ABC, abstractmethod

# 抽象工厂 - 形状工厂
class ShapeFactory(ABC):
    @abstractmethod
    def create_circle(self):
        pass

    @abstractmethod
    def create_square(self):
        pass

# 具体工厂 - 圆形工厂
class CircleFactory(ShapeFactory):
    def create_circle(self):
        return Circle()

    def create_square(self):
        return None

# 具体工厂 - 正方形工厂
class SquareFactory(ShapeFactory):
    def create_circle(self):
        return None

    def create_square(self):
        return Square()

# 抽象产品 - 形状
class Shape(ABC):
    @abstractmethod
    def draw(self):
        pass

# 具体产品 - 圆形
class Circle(Shape):
    def draw(self):
        return "Drawing Circle"

# 具体产品 - 正方形
class Square(Shape):
    def draw(self):
        return "Drawing Square"

# 使用抽象工厂创建对象
def draw_shapes(factory):
    circle = factory.create_circle()
    square = factory.create_square()

    print(circle.draw() if circle else "Circle not supported")
    print(square.draw() if square else "Square not supported")

# 使用不同的工厂创建形状
draw_shapes(CircleFactory())  # 输出: Drawing Circle / Circle not supported
draw_shapes(SquareFactory())  # 输出: Circle not supported / Drawing Square
```
此示例演示了抽象工厂模式，其中有两个工厂类分别创建圆形和正方形。每个工厂类能够创建对应的形状对象，并根据工厂类型返回相应的形状对象。

## 简单工厂模式

简单工厂模式使用一个工厂类创建对象，通过给定条件决定对象类型。

### 理念说明：
简单工厂模式适用于根据条件创建对象，但不属于23种设计模式之一。

### 代码示例：
```python
class Shape:
    def draw(self):
        pass

# 具体产品 - 圆形
class Circle(Shape):
    def draw(self):
        return "Drawing Circle"

# 具体产品 - 正方形
class Square(Shape):
    def draw(self):
        return "Drawing Square"

# 简单工厂
class SimpleShapeFactory:
    def create_shape(self, shape_type):
        if shape_type == "circle":
            return Circle()
        elif shape_type == "square":
            return Square()
        else:
            raise ValueError("Invalid shape type")

# 使用简单工厂创建对象
factory = SimpleShapeFactory()
circle = factory.create_shape("circle")
square = factory.create_shape("square")

print(circle.draw())  # 输出: Drawing Circle
print(square.draw())  # 输出: Drawing Square
```
这个示例演示了简单工厂模式。在这里，SimpleShapeFactory 根据参数类型创建对应的具体产品对象。

## 应用场景

工厂模式适用于以下场景：
- 当对象的创建涉及复杂的逻辑或条件时。
- 当需要隔离对象的创建逻辑时。

## 总结

工厂模式提供了不同的策略来管理对象的创建。通过将实例化的细节封装在不同的类中，代码更易于维护、扩展和修改。选择适当的工厂模式取决于具体的项目需求和设计考虑。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
