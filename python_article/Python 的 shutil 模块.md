![](https://p.ipic.vip/cfnkto.png)

`shutil` 是 Python 标准库中的一个模块，提供了许多用于文件操作和目录操作的功能。无论是需要复制、移动、重命名、删除文件，还是进行目录操作，`shutil` 都是一个强大的工具。

本文将会学习到 `shutil` 模块，包括其主要功能和示例代码，以帮助你更好地理解如何使用它来处理文件和目录。

## 1. 什么是 `shutil` 模块？

`shutil` 模块是 Python 标准库中的一个核心模块，提供了用于文件和目录操作的功能，包括复制、移动、重命名、删除文件和目录等。

`shutil` 模块是基于高级文件操作库 `os` 模块构建的，提供了更高级别的文件操作接口，使文件和目录的处理更加方便。

通过 `shutil` 模块，可以执行以下操作：

- 复制文件和目录。
- 移动文件和目录。
- 重命名文件和目录。
- 删除文件和目录。
- 创建和删除目录。
- 执行文件操作的递归操作。
- 更多与文件和目录操作相关的功能。

`shutil` 模块是 Python 编程中的一个不可或缺的工具，可以更轻松地管理文件和目录。

## 2. 文件和目录操作

### 2.1. 复制文件

`shutil.copy(src, dst)` 函数用于复制文件。将源文件复制到目标位置。

示例代码：

```python
import shutil

# 复制文件
shutil.copy("source_file.txt", "destination_file.txt")
```

### 2.2. 复制目录

`shutil.copytree(src, dst)` 函数用于复制目录及其内容。递归地复制整个目录结构。

示例代码：

```python
import shutil

# 复制目录
shutil.copytree("source_directory", "destination_directory")
```

### 2.3. 移动文件或目录

`shutil.move(src, dst)` 函数用于移动文件或目录。可以用于重命名文件或将文件或目录从一个位置移动到另一个位置。

示例代码：

```python
import shutil

# 移动文件
shutil.move("source_file.txt", "destination_file.txt")

# 移动目录
shutil.move("source_directory", "destination_directory")
```

### 2.4. 重命名文件或目录

`shutil.move(src, dst)` 函数也可以用于重命名文件或目录。通过将新路径传递给 `dst` 参数，可以实现重命名操作。

示例代码：

```python
import shutil

# 重命名文件
shutil.move("old_file.txt", "new_file.txt")

# 重命名目录
shutil.move("old_directory", "new_directory")
```

### 2.5. 删除文件

`shutil.remove(file)` 函数用于删除文件。

示例代码：

```python
import shutil

# 删除文件
shutil.remove("file_to_delete.txt")
```

### 2.6. 删除目录

`shutil.rmtree(directory)` 函数用于递归地删除目录及其内容。

示例代码：

```python
import shutil

# 删除目录及其内容
shutil.rmtree("directory_to_delete")
```

### 2.7. 创建目录

`shutil.mkdir(directory)` 函数用于创建目录。

示例代码：

```python
import shutil

# 创建目录
shutil.mkdir("new_directory")
```

### 2.8. 删除目录中的文件

`shutil.rmtree(directory)` 函数会删除目录及其内容。如果只想删除目录中的文件但保留目录结构，可以使用以下方法：

```python
import shutil

# 删除目录中的文件，保留目录结构
for root, dirs, files in os.walk("directory_to_clean"):
    for file in files:
        file_path = os.path.join(root, file)
        os.remove(file_path)
```

## 3. 文件操作的递归操作

`shutil` 模块提供了许多递归操作的函数，可以在文件操作中非常有用。这些函数可以递归地处理文件和目录，从而简化复杂的操作。

### 3.1. 递归复制

在 Python 中，使用 `shutil.copytree(src, dst)` 函数可以递归复制整个目录结构，包括子目录和文件。这个函数非常有用，可以将一个目录及其所有内容复制到另一个位置，保留了整个目录结构。

使用 `shutil.copytree` 来递归复制目录：

```python
import shutil

# 源目录和目标目录
source_directory = "source_directory"
destination_directory = "destination_directory"

# 使用 copytree 复制源目录到目标目录
shutil.copytree(source_directory, destination_directory)

print(f"Directory '{source_directory}' has been recursively copied to '{destination_directory}'.")
```

在上面的示例中，`source_directory` 中的所有内容（包括子目录和文件）都会被递归复制到 `destination_directory`。可以在文件操作中保持目录结构的完整性。

### 3.2. 递归移动

`shutil.move(src, dst)` 函数可以用于递归地移动文件和目录，包括它们的子目录和内容。可以在不同目录之间移动文件和目录，并且可以用于重命名文件或目录。

使用 `shutil.move` 函数来递归地移动文件和目录：

```python
import shutil

# 源目录或文件和目标目录或文件
source = "source_path"
destination = "destination_path"

# 使用 move 函数递归移动源到目标
shutil.move(source, destination)

print(f"'{source}' has been recursively moved to '{destination}'.")
```

`source` 可以是文件或目录，它及其内容将被递归地移动到 `destination`。如果 `destination` 是目录，那么 `source` 将成为 `destination` 目录的子目录。如果 `destination` 是文件路径，那么 `source` 将被移动并重命名为 `destination`。

### 3.3. 递归删除

`shutil.rmtree(directory)` 函数用于递归删除目录及其内容，包括子目录和文件。可以轻松地清理整个目录树。

使用 `shutil.rmtree` 函数来递归删除目录：

```python
import shutil

# 要删除的目录
directory_to_delete = "directory_to_delete"

# 使用 rmtree 函数递归删除目录及其内容
shutil.rmtree(directory_to_delete)

print(f"Directory '{directory_to_delete}' has been recursively deleted.")
```

在上面的示例中，`shutil.rmtree` 函数会删除 `directory_to_delete` 目录以及其中的所有子目录和文件。这是一个非常有用的功能，特别需要清理或卸载不再需要的目录时。

## 4. 示例应用：备份文件

让我们看一个实际示例，使用 `shutil` 模块创建一个简单的文件备份脚本。

```python
import shutil
import os
import time

# 源目录和目标目录
source_directory = "source_data"
backup_directory = "backup_data"

# 创建目标目录（如果不存在）
if not os.path.exists(backup_directory):
    os.makedirs(backup_directory)

# 获取当前日期作为备份文件夹名称
backup_folder = time.strftime("%Y-%m-%d")

# 创建以当前日期为名称的备份子目录
backup_path = os.path.join(backup_directory, backup_folder)
os.makedirs(backup_path)

# 复制源目录中的内容到备份目录
shutil.copytree(source_directory, os.path.join(backup_path, source_directory))
```

此示例会创建一个备份文件夹，其中包含了源目录中的内容，以当前日期作为子目录名称。

## 5. 结语

`shutil` 模块是 Python 编程中的一个强大工具，用于进行文件和目录操作。不仅可以进行基本的文件复制、移动、重命名和删除，还可以递归地处理目录结构。通过深入了解 `shutil` 模块的功能，您可以更好地掌握如何使用它来处理文件和目录，从而提高代码的效率和可维护性。希望本文的示例和解释对您有所帮助，帮助您更好地利用 `shutil` 模块来处理文件和目录。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
