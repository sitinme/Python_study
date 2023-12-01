![](https://p.ipic.vip/cfnkto.png)

文件操作是任何编程语言中都至关重要的一部分，Python 提供了简单而强大的文件操作功能，使得读取、写入和处理文件变得非常便捷。本文将详细介绍 Python 中文件操作的基本用法，包括文件的打开、读写、关闭等操作，以及不同模式下的文件处理方式。同时，提供了丰富的示例代码来说明这些操作的实际应用。

## 文件的打开与关闭

在 Python 中，使用 `open()` 函数来打开文件。`open()` 函数接受文件名和打开模式作为参数，并返回一个文件对象，可用于读取或写入文件。打开文件后，务必在完成操作后关闭文件以释放资源，使用 `close()` 方法来实现。

### 示例代码:

```python
# 打开文件
file = open('example.txt', 'r')  # 以只读模式打开文件
# 进行文件操作...
# 关闭文件
file.close()
```

## 文件的读取操作

Python 提供了多种方法来读取文件内容，包括读取整个文件、逐行读取和按需读取。

### 1. 读取整个文件内容

使用 `read()` 方法可以一次性读取整个文件的内容。这对于文件较小的情况较为方便，但对于大文件可能会消耗大量内存。

```python
file = open('example.txt', 'r')
content = file.read()
print(content)
file.close()
```

### 2. 逐行读取文件

使用 `readline()` 方法可以逐行读取文件内容。这对于大文件而言更为高效，不会一次性将整个文件内容加载到内存中。

```python
file = open('example.txt', 'r')
line = file.readline()
while line:
    print(line)
    line = file.readline()
file.close()
```

### 3. 按需读取文件

使用 `read(size)` 方法可以按需指定读取文件的字节数。这对于大文件的部分读取非常有用。

```python
file = open('example.txt', 'r')
chunk = file.read(20)  # 读取前 20 个字符
print(chunk)
file.close()
```

## 文件的写入操作

除了读取，Python 也提供了写入文件的功能，允许创建、编辑和更新文件内容。

### 1. 写入文件

使用 `write()` 方法可以向文件中写入内容，如果文件不存在则会被创建。需要注意的是，以写入模式打开文件会清空文件内容，如果想要追加内容可以使用追加模式 `'a'`。

```python
file = open('new_file.txt', 'w')
file.write('Hello, this is a new file!')
file.close()
```

### 2. 追加内容到文件

使用追加模式 `'a'` 打开文件，可以在文件末尾追加新内容，而不会清空原有内容。

```python
file = open('new_file.txt', 'a')
file.write('\nAppending new content to the file.')
file.close()
```

## 不同打开模式的用途

在 `open()` 函数中，可以指定不同的模式来打开文件，每种模式都有特定的用途。

- `'r'`：只读模式，用于读取文件内容，文件必须存在。
- `'w'`：写入模式，用于写入内容到文件，会清空文件内容，如果文件不存在则创建文件。
- `'a'`：追加模式，用于在文件末尾追加内容，如果文件不存在则创建文件。
- `'r+'`：读写模式，可以读取和写入文件，文件必须存在。
- `'b'`：二进制模式，用于处理二进制文件，例如图片或视频文件。

```python
# 以读写模式打开文件
file = open('example.txt', 'r+')
# 进行读取和写入操作...
file.close()
```

## 上下文管理器（Context Manager）

Python 中的 `with` 语句提供了上下文管理器，用于自动管理资源的分配和释放，更安全、更简洁地处理文件操作。

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
# 文件会在 with 代码块结束后自动关闭，无需手动调用 file.close()
```

## 异常处理

在文件操作中，可能会出现各种异常，例如文件不存在、权限问题等。使用异常处理能够更好地应对这些问题。

```python
try:
    file = open('nonexistent_file.txt', 'r')
    content = file.read()
    file.close()
except FileNotFoundError:
    print("File not found.")
except PermissionError:
    print("Permission denied to open the file.")
finally:
    file.close()
```

## 总结

Python 中的文件操作是编程中不可或缺的一部分。通过 `open()` 函数，可以以不同模式打开文件，进行读取和写入操作。对于读取，`read()` 方法能读取整个文件或者逐行读取，而 `readline()` 方法则逐行处理大文件更有效。写入文件可使用 `write()` 方法，以及追加模式 `'a'`。各种打开模式包括只读、写入、追加、读写以及处理二进制文件。上下文管理器 `with` 语句可简化文件操作，自动管理资源释放。异常处理在文件操作中也很重要，能应对文件不存在、权限问题等异常情况。

掌握文件操作的基本用法对于处理数据、配置文件等至关重要。 Python 提供了灵活而强大的文件处理功能，对于编写各种应用程序和处理数据十分重要。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
