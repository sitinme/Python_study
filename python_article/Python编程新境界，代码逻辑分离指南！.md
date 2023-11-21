![](https://p.ipic.vip/cfnkto.png)

在 Python 编程中，适当的代码逻辑分离可以帮助降低复杂度、提高可读性，减少大量的 if-else 结构。本文将深入探讨如何使用不同方法来改进代码结构，降低对 if-else 结构的依赖。

## 1. 使用字典替代if-else

通过字典映射，将不同的操作与对应的函数关联起来，减少大量的if-else结构。

```python
def action1():
    return "Action 1"

def action2():
    return "Action 2"

def action3():
    return "Action 3"

options = {
    '1': action1,
    '2': action2,
    '3': action3
}

choice = input("Enter choice (1, 2, 3): ")

if choice in options:
    result = options[choice]()
    print(result)
else:
    print("Invalid choice")
```

## 2. 使用策略模式

通过创建不同的策略类，将不同的行为封装在类内部，提高可维护性和灵活性。

```python
class Action1:
    def execute(self):
        return "Action 1"

class Action2:
    def execute(self):
        return "Action 2"

class Action3:
    def execute(self):
        return "Action 3"

class Context:
    def __init__(self, strategy):
        self.strategy = strategy

    def execute_action(self):
        return self.strategy.execute()

# 在需要执行的地方选择特定的策略
choice = input("Enter choice (1, 2, 3): ")

if choice == '1':
    context = Context(Action1())
elif choice == '2':
    context = Context(Action2())
elif choice == '3':
    context = Context(Action3())
else:
    print("Invalid choice")

if choice in ('1', '2', '3'):
    result = context.execute_action()
    print(result)
```

## 3. 使用多态

利用 Python 的多态特性，将不同类对象统一调用相同的方法，从而消除冗长的 if-else 结构。

```python
class BaseAction:
    def execute(self):
        pass

class Action1(BaseAction):
    def execute(self):
        return "Action 1"

class Action2(BaseAction):
    def execute(self):
        return "Action 2"

class Action3(BaseAction):
    def execute(self):
        return "Action 3"

# 统一调用执行方法
def perform_action(action):
    return action.execute()

choice = input("Enter choice (1, 2, 3): ")

if choice == '1':
    result = perform_action(Action1())
elif choice == '2':
    result = perform_action(Action2())
elif choice == '3':
    result = perform_action(Action3())
else:
    result = "Invalid choice"

print(result)
```

## 4. 使用装饰器

装饰器能够为函数添加额外的功能，使代码结构更为清晰，避免深层嵌套的 if-else 结构。

```python
def choice_validator(func):
    def inner(*args, **kwargs):
        choice = args[0]
        if choice in ('1', '2', '3'):
            return func(*args, **kwargs)
        else:
            return "Invalid choice"
    return inner

@choice_validator
def perform_action(choice):
    actions = {
        '1': "Action 1",
        '2': "Action 2",
        '3': "Action 3"
    }
    return actions[choice]

choice = input("Enter choice (1, 2, 3): ")
result = perform_action(choice)
print(result)
```

## 总结

通过这些方法，可以减少 if-else 结构，提高代码的模块化、可读性和可维护性。选择合适的方法将使代码更清晰、更易于理解，并提高代码的可重用性。适当的代码逻辑分离对于编写清晰、高效的代码是非常重要的。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
