![](https://p.ipic.vip/cfnkto.png)

Python作为一门强大的编程语言，提供了丰富而灵活的输入输出（I/O）功能，使得与用户交互和数据处理变得轻而易举。

## 标准输入与标准输出

Python的输入输出从最基础的标准输入（stdin）和标准输出（stdout）开始。

`print()`函数将文本输出到屏幕上

`input()`函数从用户获取输入。

```python
# 使用print()函数输出文本
print("Hello, Python!")

# 使用input()函数获取用户输入
name = input("请输入您的名字：")
print(f"欢迎您，{name}!")
```

在这里，向用户问好并获取其名字，然后将其回显到屏幕上。

## 文件输入与输出

在Python中，文件操作非常常见。可以使用`open()`函数来打开文件，并通过它来读取或写入文件内容。为了确保文件在使用完毕后被正确关闭，通常使用`with`语句块。

```python
# 打开文件以读取内容
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# 打开文件以写入内容
with open("output.txt", "w") as file:
    file.write("这是写入的文本。")
```

这里，打开了一个文件以供读取，并将其内容显示在屏幕上，然后创建了一个新文件并向其中写入文本。

## 文件操作技巧

除了基本的文件读写外，还有一些技巧可以让文件操作更加灵活。例如，可以构建文件路径，检查文件是否存在，以及创建和删除目录。

```python
import os

# 构建文件路径
file_path = os.path.join("data", "example.txt")

# 检查文件是否存在
if os.path.exists(file_path):
    print("文件存在。")

# 创建目录
os.makedirs("my_directory")

# 删除目录
os.rmdir("my_directory")
```

这里，使用`os`模块执行了文件路径构建、文件存在检查、目录创建和目录删除操作。

## 实际应用

文件操作在实际应用中非常重要。例如，可以使用Python来处理文本文件，如日志文件或配置文件。

下面是一个简单的例子，演示如何读取和写入文本文件。

```python
# 读取配置文件
config = {}
with open("config.txt", "r") as file:
    for line in file:
        key, value = line.strip().split("=")
        config[key] = value

# 修改配置并保存
config["username"] = "new_user"
with open("config.txt", "w") as file:
    for key, value in config.items():
        file.write(f"{key}={value}\n")
```

在这个示例中，读取了一个配置文件并修改了其中的值，然后将修改后的配置保存回文件。

## 最佳实践和注意事项

在Python的文件操作中，一些最佳实践可以确保代码更加健壮和可维护。这包括处理字符编码、处理大文件和异常处理等。

```python
try:
    with open("file.txt", "r", encoding="utf-8") as file:
        content = file.read()
except FileNotFoundError:
    print("文件不存在。")
except UnicodeDecodeError:
    print("无法解码文件。")
else:
    print("文件读取成功。")
```

使用异常处理来处理文件不存在和字符编码问题。

## 总结
在实际应用中，Python的I/O功能变得更加强大。可以处理文本文件、CSV、JSON等各种数据格式，同时还可以进行异常处理、字符编码处理以及大文件操作。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)

