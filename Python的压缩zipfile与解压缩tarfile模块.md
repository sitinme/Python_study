![](https://p.ipic.vip/cfnkto.png)

Python 提供了两个标准库模块来处理文件的压缩和解压缩操作：`zipfile` 用于处理 ZIP 格式的文件压缩，`tarfile` 用于处理 Tar 格式的文件压缩。

本文将分享 这两个模块的使用方法，包括安装、压缩文件的创建、压缩文件的读取、解压缩和示例代码。

## 安装

Python 的 `zipfile` 和 `tarfile` 模块是标准库的一部分，因此不需要额外安装。可以直接在 Python 程序中导入它们。

```python
import zipfile
import tarfile
```

## 使用 zipfile 模块压缩文件

### 创建压缩文件

使用 `zipfile` 模块可以轻松地创建 ZIP 压缩文件。

以下是一个示例，演示如何创建一个 ZIP 压缩文件并将文件添加到其中：

```python
import zipfile

# 创建一个 ZIP 压缩文件
with zipfile.ZipFile('example.zip', 'w') as zipf:
    # 添加文件到压缩文件
    zipf.write('file.txt', 'file.txt')
```

### 读取压缩文件

要读取 ZIP 压缩文件并获取其中的文件列表，可以使用 `zipfile.ZipFile` 的 `namelist()` 方法：

```python
import zipfile

with zipfile.ZipFile('example.zip', 'r') as zipf:
    file_list = zipf.namelist()
    print("ZIP 压缩文件中的文件列表:", file_list)
```

## 使用 tarfile 模块压缩文件

### 创建压缩文件

使用 `tarfile` 模块可以创建 Tar 压缩文件。

以下是一个示例，演示如何创建一个 Tar 压缩文件并将文件添加到其中：

```python
import tarfile

# 创建一个 Tar 压缩文件
with tarfile.open('example.tar.gz', 'w:gz') as tarf:
    # 添加文件到压缩文件
    tarf.add('file.txt', arcname='file.txt')
```

### 读取压缩文件

要读取 Tar 压缩文件并获取其中的文件列表，可以使用 `tarfile.TarFile` 的 `getnames()` 方法：

```python
import tarfile

with tarfile.open('example.tar.gz', 'r:gz') as tarf:
    file_list = tarf.getnames()
    print("Tar 压缩文件中的文件列表:", file_list)
```

## 解压缩文件

要解压缩 ZIP 或 Tar 压缩文件中的文件，可以使用相应的模块提供的解压缩方法。

以下是一个示例，演示如何解压缩文件：

### 解压缩 ZIP 文件

```python
import zipfile

with zipfile.ZipFile('example.zip', 'r') as zipf:
    zipf.extractall('extracted_files')  # 将文件解压缩到指定目录
```

### 解压缩 Tar 文件

```python
import tarfile

with tarfile.open('example.tar.gz', 'r:gz') as tarf:
    tarf.extractall('extracted_files')  # 将文件解压缩到指定目录
```

## 示例代码

以下是一些示例代码，演示了如何使用 `zipfile` 和 `tarfile` 模块执行常见任务：

```python
import zipfile
import tarfile

# 使用 zipfile 模块创建 ZIP 压缩文件
with zipfile.ZipFile('example.zip', 'w') as zipf:
    zipf.write('file.txt', 'file.txt')

# 使用 zipfile 模块读取 ZIP 压缩文件
with zipfile.ZipFile('example.zip', 'r') as zipf:
    file_list = zipf.namelist()
    print("ZIP 压缩文件中的文件列表:", file_list)

# 使用 tarfile 模块创建 Tar 压缩文件
with tarfile.open('example.tar.gz', 'w:gz') as tarf:
    tarf.add('file.txt', arcname='file.txt')

# 使用 tarfile 模块读取 Tar 压缩文件
with tarfile.open('example.tar.gz', 'r:gz') as tarf:
    file_list = tarf.getnames()
    print("Tar 压缩文件中的文件列表:", file_list)

# 解压 ZIP 文件
with zipfile.ZipFile('example.zip', 'r') as zipf:
    zipf.extractall('extracted_files')

# 解压 Tar 文件
with tarfile.open('example.tar.gz', 'r:gz') as tarf:
    tarf.extractall('extracted_files')
```

## 总结

Python 的 `zipfile` 和 `tarfile` 模块是处理文件的压缩和解压缩操作的重要工具。分别用于 `ZIP` 和 `Tar` 格式的文件，提供了简单而有效的方法来创建、读取和解压缩文件。在本文中，分享了如何创建压缩文件并添加文件到中，以及如何读取压缩文件中的文件列表。同时，还演示了如何解压缩 `ZIP` 和 `Tar` 压缩文件中的文件到指定目录。

这两个模块对于处理文件操作非常有用，可以在许多场景中帮助您有效地管理文件和数据。无论是备份文件、打包文件，还是解压缩已压缩的数据，`zipfile` 和 `tarfile` 模块都提供了简单而灵活的解决方案。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
