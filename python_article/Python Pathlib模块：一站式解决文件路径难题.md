![](https://p.ipic.vip/cfnkto.png)

Python的`pathlib`模块是Python 3.4及以后版本引入的一个强大的文件和目录路径操作工具，提供了一种更直观和面向对象的方式来操作文件系统路径。`pathlib`模块使得路径操作更加简单和可读，尤其是在处理文件和目录时，它是一个非常有用的工具。

在本文中，将详细介绍`pathlib`模块，包括如何创建路径、检查文件和目录的存在、遍历目录、执行文件操作等。此外，还将提供丰富的示例代码来演示如何使用`pathlib`模块来处理文件和目录。

## 1. 引入`pathlib`模块

要使用`pathlib`模块，首先需要引入它。在Python中，可以使用以下方式引入`pathlib`模块：

```python
from pathlib import Path
```

一旦引入了`Path`类，您就可以开始使用`pathlib`来操作文件和目录路径了。

## 2. 创建路径对象

`pathlib`模块引入了`Path`类，它用于表示文件系统路径。要创建一个路径对象，只需将路径作为字符串传递给`Path`类的构造函数。

```python
from pathlib import Path

# 创建路径对象
file_path = Path("/path/to/your/file.txt")
directory_path = Path("/path/to/your/directory")
```

## 3. 检查路径的存在

`pathlib`模块提供了方法来检查文件和目录的存在。

以下是一些常用的方法：

### 3.1 检查文件是否存在

```python
from pathlib import Path

file_path = Path("/path/to/your/file.txt")

if file_path.is_file():
    print(f"{file_path} 存在")
else:
    print(f"{file_path} 不存在")
```

### 3.2 检查目录是否存在

```python
from pathlib import Path

directory_path = Path("/path/to/your/directory")

if directory_path.is_dir():
    print(f"{directory_path} 存在")
else:
    print(f"{directory_path} 不存在")
```

### 3.3 检查路径是否存在

`exists()`方法来检查路径是否存在，不论是文件还是目录。

```python
from pathlib import Path

path = Path("/path/to/your/file_or_directory")

if path.exists():
    print(f"{path} 存在")
else:
    print(f"{path} 不存在")
```

## 4. 文件和目录操作

`pathlib`模块还提供了许多方法来执行文件和目录操作，包括创建、复制、移动、重命名、删除等。

以下是一些常用的文件和目录操作示例：

### 4.1 创建目录

```python
from pathlib import Path

new_directory = Path("/path/to/your/new_directory")
new_directory.mkdir()  # 创建目录
```

### 4.2 创建文件

```python
from pathlib import Path

new_file = Path("/path/to/your/new_file.txt")
new_file.touch()  # 创建文件
```

### 4.3 复制文件

```python
from pathlib import Path

source_file = Path("/path/to/your/source_file.txt")
destination = Path("/path/to/your/destination_directory")

source_file.copy(destination / source_file.name)  # 复制文件到目标目录
```

### 4.4 移动文件

```python
from pathlib import Path

source_file = Path("/path/to/your/source_file.txt")
destination = Path("/path/to/your/destination_directory")

source_file.rename(destination / source_file.name)  # 移动文件到目标目录
```

### 4.5 删除文件或目录

```python
from pathlib import Path

file_or_directory = Path("/path/to/your/file_or_directory")

if file_or_directory.is_file():
    file_or_directory.unlink()  # 删除文件
else:
    file_or_directory.rmdir()  # 删除目录
```

## 5. 遍历目录

`pathlib`模块允许您遍历目录中的文件和子目录。以下是如何使用`iterdir()`方法遍历目录的示例：

```python
from pathlib import Path

directory_path = Path("/path/to/your/directory")

for item in directory_path.iterdir():
    if item.is_file():
        print(f"文件: {item.name}")
    elif item.is_dir():
        print(f"目录: {item.name}")
```

## 6. 获取文件信息

`pathlib`模块还提供了一些方法来获取文件的信息，如文件大小、修改时间等。以下是一些示例：

### 6.1 获取文件大小

```python
from pathlib import Path

file_path = Path("/path/to/your/file.txt")
file_size = file_path.stat().st_size  # 获取文件大小（字节数）
print(f"{file_path} 的大小是 {file_size} 字节")
```

### 6.2 获取文件修改时间

```python
from pathlib import Path
from datetime import datetime

file_path = Path("/path/to/your/file.txt")
modification_time = file_path.stat().st_mtime  # 获取修改时间戳
modification_time = datetime.fromtimestamp(modification_time)  # 转换为日期时间对象
print(f"{file_path} 的修改时间是 {modification_time}")
```
## 总结

`pathlib`模块提供了丰富的方法来处理文件和目录路径，使文件系统操作更加简单和可读。

通过使用`pathlib`，可以更方便地执行各种文件和目录操作，而不需要手动构建和解析路径字符串。这使得代码更易维护和可移植，尤其是在不同操作系统上。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
