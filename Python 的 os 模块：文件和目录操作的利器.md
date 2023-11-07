![](https://p.ipic.vip/cfnkto.png)

Python 的标准库提供了许多有用的模块，其中 `os` 模块是一个功能强大的工具，用于进行文件和目录操作，以及管理操作系统相关的功能。无论是在编写脚本还是开发应用程序，`os` 模块都是不可或缺的。

本文将深入介绍 `os` 模块，包括其主要功能和示例代码，更好地理解如何利用它来管理文件和目录。

## 一、什么是 `os` 模块？

`os` 模块是 Python 标准库中的一个核心模块，提供了与操作系统交互的函数和方法。

通过 `os` 模块，可以执行以下操作：

- 文件和目录的创建、删除、重命名等操作。
- 获取文件和目录的属性信息，如大小、权限等。
- 运行系统命令和子进程。
- 管理环境变量和路径。
- 处理文件路径，包括路径拼接、拆分和规范化。
- 更多与操作系统相关的功能。

`os` 模块编写可移植的代码，因为它可以适应不同操作系统（如 Windows、Linux 和 macOS）的差异。

## 二、文件和目录操作

### 1. 创建目录

使用 `os.mkdir()` 函数可以创建一个新的目录。如果目录已经存在，会引发 `FileExistsError` 异常。

```python
import os

# 创建一个新目录
os.mkdir("my_directory")
```

### 2. 删除目录

使用 `os.rmdir()` 函数可以删除目录。如果目录非空，会引发 `OSError` 异常。

```python
import os

# 删除目录
os.rmdir("my_directory")
```

### 3. 遍历目录

`os` 模块提供了许多方法来遍历目录中的文件和子目录。例如，`os.listdir()` 返回指定目录中的所有文件和子目录的列表。

```python
import os

# 遍历目录并打印文件和子目录
for item in os.listdir("my_directory"):
    print(item)
```

### 4. 文件操作

`os` 模块还可以进行文件操作，如创建文件、删除文件、重命名文件等。

以下是一些常见的文件操作示例：

```python
import os

# 创建文件
with open("my_file.txt", "w") as file:
    file.write("Hello, World!")

# 删除文件
os.remove("my_file.txt")

# 重命名文件
os.rename("old_file.txt", "new_file.txt")
```

## 三、路径操作

`os` 模块提供了一组函数来处理文件和目录路径。这对于编写可移植的代码特别有用，因为不同操作系统使用不同的路径分隔符。

以下是一些示例：

### 1. 拼接路径

`os.path.join()` 函数用于拼接目录和文件名，根据当前操作系统的规则自动添加正确的路径分隔符。

```python
import os

path = os.path.join("my_directory", "file.txt")
```

### 2. 获取绝对路径

`os.path.abspath()` 函数用于获取指定路径的绝对路径。

```python
import os

absolute_path = os.path.abspath("my_directory/file.txt")
```

### 3. 拆分路径

`os.path.split()` 函数将路径拆分为目录部分和文件名部分。

```python
import os

dirname, filename = os.path.split("/path/to/my_file.txt")
```

## 四、系统命令和子进程

`os` 模块可以执行系统命令和创建子进程。这对于自动化系统任务非常有用。

### 1. 执行系统命令

`os.system()` 函数可用于执行系统命令。

```python
import os

# 执行系统命令
os.system("ls -l")
```

### 2. 创建子进程

`os` 模块还提供了创建子进程的函数，如 `os.fork()`、`os.spawn*()` 等。允许在 Python 中运行其他程序。

## 五、示例应用：批量重命名文件

一个实际示例，使用 `os` 模块批量重命名文件。

```python
import os

# 获取目标目录中的所有文件
directory = "my_directory"
files

 = os.listdir(directory)

# 批量重命名文件
for i, filename in enumerate(files):
    new_name = f"file_{i+1}.txt"
    os.rename(os.path.join(directory, filename), os.path.join(directory, new_name))
```

此示例会将目录中的所有文件重命名为 "file_1.txt"、"file_2.txt" 等。

## 总结

Python 的 `os` 模块提供了强大的工具，用于进行文件和目录操作，以及与操作系统交互。不仅可以简化文件操作，还可以使代码在不同操作系统上具有更好的可移植性。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
