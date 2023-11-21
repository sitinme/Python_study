![](https://p.ipic.vip/cfnkto.png)

设计模式是在软件工程中广泛使用的经验丰富的解决问题的方法。它们是通用的、可重复使用的解决方案，用于解决常见的设计问题。设计模式有助于使代码更易于理解、可维护和可扩展。Python作为一门多范式的编程语言，提供了丰富的设计模式应用场景。

在本文中，我们将详细介绍 Python 中的各种设计模式，包括创建型、结构型和行为型模式。

## 创建型模式

创建型模式关注对象的创建机制，它们包括单例、工厂、抽象工厂、建造者和原型模式。这些模式旨在提供一种灵活的方式来创建对象，同时减少对象创建的复杂性。

### 单例模式

单例模式确保一个类只有一个实例，并提供一个全局访问点。这对于需要在应用程序中共享资源的情况非常有用，例如配置管理、日志记录和数据库连接。

**示例代码：**

```python
class Singleton:
    _instance = None
    
    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(Singleton, cls).__new__(cls)
        return cls._instance

# 使用单例模式
singleton1 = Singleton()
singleton2 = Singleton()
print(singleton1 is singleton2)  # 输出：True
```

单例模式确保只创建一个实例，即使多次创建也返回相同的实例。

### 工厂模式

工厂模式用于创建对象，将对象的创建逻辑封装在一个方法中，从而实现对象的创建和使用的解耦。工厂模式可以根据传入的参数选择创建哪种类型的对象。

**示例代码：**

```python
class Dog:
    def __init__(self, name):
        self.name = name

class Cat:
    def __init__(self, name):
        self.name = name

class AnimalFactory:
    def create_animal(self, animal_type, name):
        if animal_type == "dog":
            return Dog(name)
        elif animal_type == "cat":
            return Cat(name)

# 使用工厂模式
factory = AnimalFactory()
dog = factory.create_animal("dog", "Buddy")
cat = factory.create_animal("cat", "Whiskers")
```

工厂模式将对象创建的逻辑封装在一个工厂类中，客户端可以根据需要创建不同类型的对象。

### 抽象工厂模式

抽象工厂模式提供了一种创建相关对象家族的方式，而无需指定它们的具体类。这允许创建一组相关对象，例如不同操作系统下的窗口和按钮。

**示例代码：**

```python
class Button:
    def display(self):
        pass

class Window:
    def display(self):
        pass

class MacOSButton(Button):
    def display(self):
        print("MacOS Button")

class LinuxButton(Button):
    def display(self):
        print("Linux Button")

class MacOSWindow(Window):
    def display(self):
        print("MacOS Window")

class LinuxWindow(Window):
    def display(self):
        print("Linux Window")

class GUIFactory:
    def create_button(self):
        pass

    def create_window(self):
        pass

class MacOSFactory(GUIFactory):
    def create_button(self):
        return MacOSButton()

    def create_window(self):
        return MacOSWindow()

class LinuxFactory(GUIFactory):
    def create_button(self):
        return LinuxButton()

    def create_window(self):
        return LinuxWindow()

# 使用抽象工厂模式
macos_factory = MacOSFactory()
linux_factory = LinuxFactory()

macos_button = macos_factory.create_button()
linux_window = linux_factory.create_window()

macos_button.display()  # 输出：MacOS Button
linux_window.display()  # 输出：Linux Window
```

抽象工厂模式创建一组相关的对象，例如在不同操作系统下使用不同样式的界面组件。

### 建造者模式

建造者模式将一个复杂对象的构建过程分解为一系列步骤，使客户端能够按步骤构建对象。这对于构建包含许多可选组件的对象非常有用。

**示例代码：**

```python
class Pizza:
    def __init__(self, size, cheese, pepperoni, mushrooms):
        self.size = size
        self.cheese = cheese
        self.pepperoni = pepperoni
        self.mushrooms = mushrooms

class PizzaBuilder:
    def __init__(self, size):
        self.size = size
        self.cheese = False
        self.pepperoni = False
        self.mushrooms = False

    def add_cheese(self):
        self.cheese = True
        return self

    def add_pepperoni(self):
        self.pepperoni = True
        return self

    def add_mushrooms(self):
        self.mushrooms = True
        return self

    def build(self):
        return Pizza(self.size, self.cheese, self.pepperoni, self.mushrooms)

# 使用建造者模式
pizza = PizzaBuilder(12).add_cheese().add_pepperoni().build()
```

建造者模式逐步构建一个对象，设置其属性并最终构建对象。这对于构建参数众多的对象非常有用。

### 原型模式

原型模式通过复制现有对象来创建新对象。这对于创建大型对象或需要定制初始化的对象非常有用。原型模式可以克隆一个现有对象，而无需从头创建一个新对象。

**示例代码：**

```python
import copy

class Prototype:
    def __init__(self):
        self.items = []

    def clone(self):
        return copy.deepcopy(self)

# 使用原型模式
original = Prototype()
original.items.append("item1")

# 克隆原型对象
clone = original.clone()
clone.items.append("item2")

print(original.items)  # 输出：['item1']
print(clone.items)     # 输出：['item1', 'item2']
```

原型模式可以克隆对象，能够在不从头创建对象的情况下生成新对象。

## 结构型模式

结构型模式处理对象之间的关系，包括适配器、桥接、组合、装饰器、外观、享元和代理模式。这些模式有助于定义对象之间的协作方式，同时保持系统的灵活性和可维护性。

### 适配器模式

适配器模式用于将一个接口转换成另一个接口，以使不兼容的类可以一起工作。适配器模式使用不同接口的对象协同工作。

**示例代码：**

```python
class OldSystem:
    def operation(self):
        return "Old System"

class NewSystem:
    def operation(self):
        return "New System"

class Adapter:
    def __init__(self, new_system):
        self.new_system = new_system

    def operation(self):
        return f"Adapter using {self.new_system.operation()}"

# 使用适配器模式
new_system = NewSystem()
adapter = Adapter(new_system)

result = adapter.operation()
print(result)  # 输出：Adapter using New System
```

适配器模式允许新旧系统一起工作，将新系统的接口适配为旧系统可以使用的接口。

### 桥接模式

桥接模式将抽象部分与实现部分分离，它们可以独立变化。这有助于减少类之间的耦合，同时允许它们在运行时独立变化。

**示例代码：**

```python
class DrawingAPI:
    def draw_circle(self, x, y, radius):
        pass

class DrawingAPI1(DrawingAPI):
    def draw_circle(self, x, y, radius):
        print(f"API1.circle at {x}:{y} radius {radius}")

class DrawingAPI2(DrawingAPI):
    def draw_circle(self, x, y, radius):
        print(f"API2.circle at {x}:{y} radius {radius}")

class Shape:
    def __init__(self, drawing_api):
        self.drawing_api = drawing_api

    def draw(self):
        pass

class Circle(Shape):
    def __init__(self, x, y, radius, drawing_api):
        super().__init__(drawing_api)
        self.x = x
        self.y = y
        self.radius = radius

    def draw(self):
        self.drawing_api.draw_circle(self.x, self.y, self.radius)

# 使用桥接模式
api1 = DrawingAPI1()
api2 = DrawingAPI2()

circle1 = Circle(1, 2, 3, api1)
circle1.draw()  # 输出

：API1.circle at 1:2 radius 3

circle2 = Circle(4, 5, 6, api2)
circle2.draw()  # 输出：API2.circle at 4:5 radius 6
```

桥接模式将抽象形状和绘制API分开，使它们可以独立变化。这有助于降低系统的复杂性。

### 组合模式

组合模式用于将对象组织成树状结构，以表示部分-整体关系。这使得客户端可以统一处理单个对象和组合对象，从而简化代码。

**示例代码：**

```python
class Component:
    def operation(self):
        pass

class Leaf(Component):
    def operation(self):
        return "Leaf"

class Composite(Component):
    def __init__(self):
        self.children = []

    def add(self, component):
        self.children.append(component)

    def operation(self):
        results = []
        for child in self.children:
            results.append(child.operation())
        return f"Composite [{', '.join(results)}]"

# 使用组合模式
leaf1 = Leaf()
leaf2 = Leaf()
composite = Composite()
composite.add(leaf1)
composite.add(leaf2)

result = composite.operation()
print(result)  # 输出：Composite [Leaf, Leaf]
```

组合模式允许构建包含子组件的复杂对象，同时使客户端能够一致地处理单个对象和组合对象。

### 装饰器模式

装饰器模式动态地将责任附加到对象上。它是在不修改对象源代码的情况下扩展对象功能的一种方式。

**示例代码：**

```python
class Coffee:
    def cost(self):
        return 5

class MilkDecorator:
    def __init__(self, coffee):
        self._coffee = coffee

    def cost(self):
        return self._coffee.cost() + 2

class SugarDecorator:
    def __init__(self, coffee):
        self._coffee = coffee

    def cost(self):
        return self._coffee.cost() + 1

# 使用装饰器模式
coffee = Coffee()
print(coffee.cost())  # 输出：5

coffee_with_milk = MilkDecorator(coffee)
print(coffee_with_milk.cost())  # 输出：7

coffee_with_milk_and_sugar = SugarDecorator(coffee_with_milk)
print(coffee_with_milk_and_sugar.cost())  # 输出：8
```

装饰器模式在运行时动态地添加新功能或修改对象的行为。

### 外观模式

外观模式提供了一个统一的接口，用于访问子系统中的一组接口。这简化了复杂子系统的使用，为客户端提供了一个简化的接口。

**示例代码：**

```python
class SubsystemA:
    def operation_a(self):
        return "Subsystem A operation"

class SubsystemB:
    def operation_b(self):
        return "Subsystem B operation"

class SubsystemC:
    def operation_c(self):
        return "Subsystem C operation"

class Facade:
    def __init__(self):
        self.subsystem_a = SubsystemA()
        self.subsystem_b = SubsystemB()
        self.subsystem_c = SubsystemC()

    def operation(self):
        result = []
        result.append(self.subsystem_a.operation_a())
        result.append(self.subsystem_b.operation_b())
        result.append(self.subsystem_c.operation_c())
        return "\n".join(result)

# 使用外观模式
facade = Facade()
result = facade.operation()
print(result)
```

外观模式提供了一个高级接口，使客户端能够访问一组子系统接口，而不必了解其复杂性。

### 享元模式

享元模式用于共享大量细粒度对象，以减少内存占用。它将对象的共享部分抽象出来，以减少对象的数量。

**示例代码：**

```python
class Flyweight:
    def operation(self):
        pass

class ConcreteFlyweight(Flyweight):
    def __init__(self, intrinsic_state):
        self._intrinsic_state = intrinsic_state

    def operation(self):
        return f"Concrete Flyweight: {self._intrinsic_state}"

class FlyweightFactory:
    def __init__(self):
        self._flyweights = {}

    def get_flyweight(self, key):
        if key not in self._flyweights:
            self._flyweights[key] = ConcreteFlyweight(key)
        return self._flyweights[key]

# 使用享元模式
factory = FlyweightFactory()
flyweight1 = factory.get_flyweight("A")
flyweight2 = factory.get_flyweight("B")

print(flyweight1.operation())  # 输出：Concrete Flyweight: A
print(flyweight2.operation())  # 输出：Concrete Flyweight: B
```

享元模式允许多个对象共享相同的内部状态，从而降低内存占用。

### 代理模式

代理模式允许创建一个代理对象，用于控制对其他对象的访问。代理对象充当被代理对象的接口，以便在不直接访问被代理对象的情况下执行其他操作。

**示例代码：**

```python
class Subject:
    def operation(self):
        pass

class RealSubject(Subject):
    def operation(self):
        return "Real Subject operation"

class Proxy(Subject):
    def __init__(self):
        self._real_subject = RealSubject()

    def operation(self):
        return f"Proxy operation, {self._real_subject.operation()}"

# 使用代理模式
proxy = Proxy()
result = proxy.operation()
print(result)  # 输出：Proxy operation, Real Subject operation
```

代理模式允许代理对象控制对真实对象的访问，从而提供附加的功能或控制。

## 行为型模式

行为型模式处理对象之间的通信，包括观察者、策略、命令、责任链、状态、访问者、迭代器、备忘录、中介者、解释器和模板方法模式。这些模式有助于定义对象之间的交互和职责分配。

### 观察者模式

观察者模式定义了一种一对多的依赖关系，其中一个对象的状态发生变化时，其所有依赖对象都会得到通知。

**示例代码：**

```python
class Subject:
    def __init__(self):
        self._observers = []

    def attach(self, observer):
        self._observers.append(observer)

    def detach(self, observer):
        self._observers.remove(observer)

    def notify(self):
        for observer in self._observers:
            observer.update()

class ConcreteSubject(Subject):
    def __init__(self, state):
        super().__init__()
        self._state = state

    def get_state(self):
        return self._state

    def set_state(self, state):
        self._state = state
        self.notify()

class Observer:
    def update(self):
        pass

class ConcreteObserver(Observer):
    def __init__(self, subject):
        self._subject = subject
        self._state = subject.get_state()

    def update(self):
        self._state = self._subject.get_state()

# 使用观察者模式
subject = ConcreteSubject("initial state")
observer1 = ConcreteObserver(subject)
observer2 = ConcreteObserver(subject)

subject.attach(observer1)
subject.attach(observer2)

print(observer1._state)  # 输出：initial state
print(observer2._state)  # 输出：initial state

subject.set_state("new state")

print(observer1._state)  # 输出：new state
print(observer2._state)  # 输出：new state
```

观察者模式允许主题对象和观察者对象之间保持松散的耦合，主题对象的状态变化会自动通知观察者对象。

### 策略模式

策略模式定义了一系列算法，封装每个算法，并使它们可以相互替换。这提供了灵活性，允许在运行时选择算法。

**示例代码：**

```python
class Strategy:
    def execute(self, a, b):
        pass

class AddStrategy(Strategy):
    def execute(self, a, b):
        return a + b

class SubtractStrategy(Strategy):
    def execute(self, a, b):
        return a - b

class Calculator:
    def __init__(self, strategy):
        self._strategy = strategy

    def execute(self, a, b):
        return self._strategy.execute(a, b)

# 使用策略模式
add_strategy = AddStrategy()
sub_strategy = SubtractStrategy()

calculator = Calculator(add_strategy)
result = calculator.execute(5, 3)
print(result)  # 输出：8

calculator = Calculator(sub_strategy)
result = calculator.execute(5, 3)
print(result)  # 输出：2
```

策略模式允许定义一组算法，并将它们封装在可互换的策略对象中，以便在运行时选择不同的算法。

### 命令模式

命令模式将请求封装成一个对象，从而可以参数化客户端对象操作，队列请求或记录请求日志。

**示例代码：**

```python
class Receiver:
    def action(self):
        pass

class Light(Receiver):
    def action(self):
        print("Light is on")

class Stereo(Receiver):
    def action(self):
        print("Stereo is on")

class Command:
    def __init__(self, receiver):
        self._receiver = receiver

    def execute(self):
        pass

class LightOnCommand(Command):
    def execute(self):
        self._receiver.action()

class StereoOnCommand(Command):
    def execute(self):
        self._receiver.action()

class RemoteControl:
    def __init__(self):
        self._commands = []

    def add_command(self, command):
        self._commands.append(command)

    def execute_commands(self):
        for command in self._commands:
            command.execute()

# 使用命令模式
light = Light()
stereo = Stereo()

light_on_command = LightOnCommand(light)
stereo_on_command = StereoOnCommand(stereo)

remote = RemoteControl()
remote.add_command(light_on_command)
remote.add_command(stereo_on_command)

remote.execute_commands()
# 输出：
# Light is on
# Stereo is on
```

命令模式将请求和处理请求的对象解耦，允许将命令存储、排队和操作。

### 责任链模式

责任链模式构建一系列对象，每个对象负责处理请求的一部分。请求按顺序通过链传递，直到有一个对象处理它为止。

**示例代码：**

```python
class Handler:
    def set_successor(self, successor):
        self._successor = successor

    def handle_request(self, request):
        pass

class ConcreteHandler1(Handler):
    def handle_request(self, request):
        if request == "A":
            return "Handled by Handler1"
        elif self._successor:
            return self._successor.handle_request(request)
        else:
            return "Request not handled"

class ConcreteHandler2(Handler):
    def handle_request(self, request):
        if request == "B":
            return "Handled by Handler2"
        elif self._successor:
            return self._successor.handle_request(request)
        else:
            return "Request not handled"

# 使用责任链模式
handler1 = ConcreteHandler1()
handler2 = ConcreteHandler2()

handler1.set_successor(handler2)

result1 = handler1.handle_request("A")
print(result1)  # 输出：Handled by Handler1

result2 = handler1.handle_request("B")
print(result2)  # 输出：Handled by Handler2

result3 = handler1.handle_request("C")
print(result3)  # 输出：Request not handled
```

责任链模式允许构建对象链，其中每个对象决定是否处理请求或将其传递给下一个对象。

### 状态模式

状态模式允许对象在其内部状态改变时改变其行为。这将状态转移逻辑封装在不同的状态类中。

**示例代码：**

```python
class State:
    def handle(self):
        pass

class StateA(State):
    def handle(self):
        return "State A"

class StateB(State):
    def handle(self):
        return "State B"

class Context:
    def __init__(self):
        self._state = None

    def set_state(self, state):
        self._state = state

    def request(self):
        return self._state.handle()

# 使用状态模式
context = Context()
state_a = StateA()
state_b = StateB()

context.set_state(state_a)
result1 = context.request()
print(result1)  # 输出：State A



context.set_state(state_b)
result2 = context.request()
print(result2)  # 输出：State B
```

状态模式允许对象在其内部状态改变时改变其行为，从而使其看起来像是更改了类。

### 访问者模式

访问者模式允许在不修改对象结构的情况下为对象结构中的元素添加新操作。它通过将访问操作从元素类中分离出来来实现这一点。

**示例代码：**

```python
class Element:
    def accept(self, visitor):
        pass

class ConcreteElementA(Element):
    def accept(self, visitor):
        visitor.visit_concrete_element_a(self)

class ConcreteElementB(Element):
    def accept(self, visitor):
        visitor.visit_concrete_element_b(self)

class Visitor:
    def visit_concrete_element_a(self, element):
        pass

    def visit_concrete_element_b(self, element):
        pass

class ConcreteVisitor(Visitor):
    def visit_concrete_element_a(self, element):
        return f"Visited {element.__class__.__name__} by {self.__class__.__name__}"

    def visit_concrete_element_b(self, element):
        return f"Visited {element.__class__.__name__} by {self.__class__.__name__}"

# 使用访问者模式
element_a = ConcreteElementA()
element_b = ConcreteElementB()
visitor = ConcreteVisitor()

result1 = element_a.accept(visitor)
print(result1)  # 输出：Visited ConcreteElementA by ConcreteVisitor

result2 = element_b.accept(visitor)
print(result2)  # 输出：Visited ConcreteElementB by ConcreteVisitor
```

访问者模式将元素和访问操作分离，为元素添加新操作而无需修改元素类。

### 迭代器模式

迭代器模式在不暴露集合的内部表示的情况下顺序访问集合的元素。

**示例代码：**

```python
class Iterator:
    def next(self):
        pass

class Aggregate:
    def create_iterator(self):
        pass

class ConcreteIterator(Iterator):
    def __init__(self, collection):
        self._collection = collection
        self._index = 0

    def next(self):
        if self._index < len(self._collection):
            item = self._collection[self._index]
            self._index += 1
            return item
        else:
            raise StopIteration()

class ConcreteAggregate(Aggregate):
    def __init__(self):
        self._collection = []

    def create_iterator(self):
        return ConcreteIterator(self._collection)

    def add_item(self, item):
        self._collection.append(item)

# 使用迭代器模式
aggregate = ConcreteAggregate()
aggregate.add_item("Item 1")
aggregate.add_item("Item 2")
aggregate.add_item("Item 3")

iterator = aggregate.create_iterator()

while True:
    try:
        item = iterator.next()
        print(item)
    except StopIteration:
        break
```

迭代器模式顺序访问集合的元素，而无需暴露其内部表示。

### 备忘录模式

备忘录模式用于捕获一个对象的内部状态，以便以后可以将其恢复到该状态。它将对象状态的保存和恢复分离开来。

**示例代码：**

```python
class Memento:
    def __init__(self, state):
        self._state = state

    def get_state(self):
        return self._state

class Originator:
    def __init__(self):
        self._state = ""

    def set_state(self, state):
        self._state = state

    def create_memento(self):
        return Memento(self._state)

    def restore_memento(self, memento):
        self._state = memento.get_state()

class Caretaker:
    def __init__(self):
        self._mementos = []

    def add_memento(self, memento):
        self._mementos.append(memento)

    def get_memento(self, index):
        return self._mementos[index]

# 使用备忘录模式
originator = Originator()
caretaker = Caretaker()

originator.set_state("State 1")
caretaker.add_memento(originator.create_memento())

originator.set_state("State 2")
caretaker.add_memento(originator.create_memento())

originator.restore_memento(caretaker.get_memento(0))
print(originator._state)  # 输出：State 1

originator.restore_memento(caretaker.get_memento(1))
print(originator._state)  # 输出：State 2
```

备忘录模式保存对象的状态，并在需要时将其恢复到以前的状态。

### 中介者模式

中介者模式用于减少对象之间的直接通信，将对象之间的交互集中到中介者对象中。这有助于减少对象之间的耦合。

**示例代码：**

```python
class Mediator:
    def send(self, message, colleague):
        pass

class Colleague:
    def __init__(self, mediator):
        self._mediator = mediator

    def send(self, message):
        self._mediator.send(message, self)

class ConcreteMediator(Mediator):
    def __init__(self, colleague1, colleague2):
        self._colleague1 = colleague1
        self._colleague2 = colleague2

    def send(self, message, colleague):
        if colleague == self._colleague1:
            self._colleague2.receive(message)
        else:
            self._colleague1.receive(message)

class ConcreteColleague1(Colleague):
    def receive(self, message):
        print(f"Colleague 1 received: {message}")

class ConcreteColleague2(Colleague):
    def receive(self, message):
        print(f"Colleague 2 received: {message}")

# 使用中介者模式
colleague1 = ConcreteColleague1(None)
colleague2 = ConcreteColleague2(None)

mediator = ConcreteMediator(colleague1, colleague2)
colleague1._mediator = mediator
colleague2._mediator = mediator

colleague1.send("Hello from Colleague 1")
colleague2.send("Hi from Colleague 2")
```

中介者模式将对象之间的通信集中到中介者对象中，减少了对象之间的直接耦合。

### 解释器模式

解释器模式用于定义一门语言的语法，以解释语言中的句子。它将语法规则和解释逻辑分开。

**示例代码：**

```python
class Expression:
    def interpret(self):
        pass

class TerminalExpression(Expression):
    def __init__(self, data):
        self._data = data

    def interpret(self):
        if self._data in ["LiteralA", "LiteralB"]:
            return True
        return False

class OrExpression(Expression):
    def __init__(self, expression1, expression2):
        self._expression1 = expression1
        self._expression2 = expression2

    def interpret(self):
        return self._expression1.interpret() or self._expression2.interpret()

class AndExpression(Expression):
    def __init__(self, expression1, expression2):
        self._expression1 = expression1
        self._expression2 = expression2

    def interpret(self):
        return self._expression1.interpret() and self._expression2.interpret()

# 使用解释器模式
expression1 = TerminalExpression("LiteralA")
expression2 = TerminalExpression("LiteralB")
or_expression = OrExpression(expression1, expression2)
and_expression = AndExpression(expression1, expression2)

result1 = or_expression.interpret()
print(result1)  # 输出：True

result2 = and_expression.interpret()
print(result2)  # 输出：True
```

解释器模式定义一门语言的语法，并为语言中的句子创建解释器。

### 模板方法模式

模板方法模式定义了一个算法的骨架，将算法的一些步骤推迟到子类中。这允许子类在不改变算法结构的情况下重新定义算法的某些步骤。

**示例代码：**

```python
class AbstractClass:
    def template_method(self):
        self.operation1()
        self.operation2()

    def operation1(self):
        pass

    def operation2(self):
        pass

class ConcreteClass1(AbstractClass):
    def operation1(self):
        print("ConcreteClass1: Operation 1")

    def operation2(self):
        print("ConcreteClass1: Operation 2")

class ConcreteClass2(AbstractClass):
    def operation1(self):
        print("ConcreteClass2: Operation 1")

    def operation2(self):
        print("ConcreteClass2: Operation 2")

# 使用模板方法模式
concrete1 = ConcreteClass1()
concrete1.template_method()
# 输出：
# ConcreteClass1: Operation 1
# ConcreteClass1: Operation 2

concrete2 = ConcreteClass2()
concrete2.template_method()
# 输出：
# ConcreteClass2: Operation 1
# ConcreteClass2: Operation 2
```

模板方法模式定义了一个算法的骨架，允许子类提供实现特定步骤的方法。

## 结论

Python的设计模式是一种有关如何解决特定问题或设计灵活可维护代码的指导原则。设计模式是开发者们多年经验的总结，可以在面对各种软件设计挑战时提供有力的解决方案。

创建型设计模式处理对象的创建，包括单例、工厂、抽象工厂、建造者和原型模式。这些模式可以灵活地管理对象的生命周期和创建过程。

结构型设计模式有助于组织和管理对象之间的关系，包括适配器、装饰器、代理、组合、桥接、享元和外观模式。它们构建更灵活和可维护的系统。

行为型设计模式处理对象之间的通信和协作，包括观察者、策略、命令、责任链、状态、访问者、迭代器、备忘录、中介者、解释器和模板方法模式。这些模式有助于定义对象之间的交互和协作方式。

设计模式可以提高代码的可读性、可维护性和可扩展性。选择适当的设计模式可以使开发过程更高效，减少错误，并降低系统复杂性。然而，要根据具体问题和需求来选择和实现设计模式，而不是机械地应用它们。在实际开发中，理解设计模式的核心概念和原则将成为更出色的软件工程师。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
