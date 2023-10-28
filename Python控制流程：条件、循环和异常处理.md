![](https://p.ipic.vip/cfnkto.png)

Python是一门强大的编程语言，具备丰富的控制流程工具，使得开发者能够更灵活地控制程序的执行流程。

掌握Python的控制流程对于编写高效、功能强大的程序至关重要。

## 1.条件语句：控制程序分支

条件语句是编程中的基本构建块之一，允许根据条件的真假执行不同的代码块。Python提供了`if`语句，能够轻松实现分支逻辑。

```python
age = 20

if age >= 18:
    print("您已经成年了，可以投票！")
else:
    print("对不起，您还不能投票。")
```

在这个例子中，使用了`if`语句检查`age`变量的值是否大于或等于18。如果条件成立，就会执行第一个代码块；否则，执行第二个代码块。

但条件不仅仅局限于一个分支，还可以使用`elif`来添加更多条件分支：

```python
score = 85

if score >= 90:
    print("优秀")
elif score >= 70:
    print("良好")
else:
    print("待提高")
```

这个例子演示了如何根据不同的分数范围给出不同的评价。

## 2. 循环结构：重复执行代码

在编程中，循环结构是处理重复性任务的利器。Python提供了两种主要类型的循环：`for`循环和`while`循环。

**2.1 for循环：** 

这种循环通常用于遍历集合中的元素，如列表、元组或字符串。

```python
fruits = ["苹果", "香蕉", "橙子"]

for fruit in fruits:
    print(fruit)
```

这段代码遍历了水果列表，并逐个打印出每种水果的名称。

**2.2 while循环：** 

这种循环用于在满足特定条件时重复执行代码块。

```python
count = 0

while count < 5:
    print(f"计数：{count}")
    count += 1
```

这个例子展示了如何使用`while`循环来计数。

## 3. 异常处理：应对错误情况

在编写程序时，不可避免地会遇到错误和异常情况。为了确保程序的稳定性，Python提供了异常处理机制。

**3.1 try和except：** 

使用`try`和`except`块可以捕获并处理异常。

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("除零错误发生了！")
```

在这个示例中，尝试计算10除以0，这会引发`ZeroDivisionError`异常，使用`except`捕获了这个异常并打印了一条错误消息。

**3.2 finally和自定义异常：** 

使用`finally`块可以确保不管是否发生异常都会执行的代码。还可以创建自定义异常类，以更好地管理异常情况。

```python
class CustomError(Exception):
    def __init__(self, message):
        self.message = message

try:
    raise CustomError("这是自定义异常的示例。")
except CustomError as e:
    print(f"捕获到自定义异常：{e}")
finally:
    print("无论如何都会执行的代码块。")
```

这个示例中，创建了一个名为`CustomError`的自定义异常类，并在`try`块中引发了这个异常。然后，`except`块捕获了异常并打印了消息，而`finally`块中的代码无论如何都会执行。

## 4. 实际应用示例

现在让我们看一些实际应用示例，以便更好地理解控制流程如何在实际编程中发挥作用。

**4.1 条件语句的应用：** 

假设正在编写一个简单的登录系统。根据用户输入的用户名和密码，可以使用条件语句验证用户是否成功登录。

```python
username = input("请输入用户名：")
password = input("请输入密码：")

if username == "admin" and password == "12345":
    print("登录成功！")
else:
    print("登录失败，请重试。")
```

在这个示例中，使用条件语句来检查用户名和密码是否匹配。

**4.2 循环结构的应用：** 

假设需要编写一个程序，计算给定数字列表中的所有偶数的平均值。

```python
numbers = [2, 4, 6, 8, 10]
total = 0
count = 0

for num in numbers:
    if num % 2 == 0:
        total += num
        count += 1

if count > 0:
    average = total / count
    print(f"偶数的平均值是：{average}")
else:
    print("没有偶数可供计算。")
```

在这个示例中，使用`for`循环遍历数字列表，并使用条件语句检查每个数字是否为偶数，然后计算它们的平均值。

**4.3 异常处理的应用：** 

假设正在编写一个文件处理程序，需要打开文件并读取其中的内容。在这个过程中，文件可能不存在，或者出现其他问题。

```python
try:
    with open("example.txt", "r") as file:
        content = file.read()
        print(content)
except FileNotFoundError:
    print("文件未找到。")
except Exception as e:
    print(f"发生错误：{e}")
```

在这个示例中，使用`try`和`except`块来处理文件操作可能出现的异常情况。如果文件不存在，捕获`FileNotFoundError`异常；如果发生其他异常，也会捕获并打印错误消息。


## 总结

条件语句能够根据条件的真假来选择不同的执行路径，这对于根据不同情况采取不同措施的程序至关重要。

循环结构允许我们重复执行代码块，处理集合中的元素或在满足条件时执行特定任务。for循环和while循环都是强大的工具，用于处理重复性任务和迭代数据。

异常处理是编写健壮程序的关键。通过使用try和except块，可以捕获并处理可能出现的错误情况，确保程序不会因异常而崩溃。同时，finally块可以用于执行无论是否发生异常都必须完成的代码。


--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)

