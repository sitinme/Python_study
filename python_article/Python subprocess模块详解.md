![](https://p.ipic.vip/cfnkto.png)

Python的`subprocess`模块是一个非常强大的工具，用于启动和与外部进程进行交互。它允许执行外部命令、访问系统Shell、管道数据、捕获输出和错误信息，以及更多。

本文详细介绍 `subprocess`模块的各个方面，包括如何执行外部命令、传递参数、处理输入输出、错误处理以及一些高级应用。

## 1. 介绍

`subprocess`模块是Python的标准库中的一部分，它允许与外部进程进行交互。这对于执行系统命令、调用其他可执行文件、处理数据流以及与其他进程通信非常有用。无论是需要执行简单的命令还是需要与复杂的外部程序进行交互，`subprocess`都可以胜任。

在接下来的内容中，我们将学习如何使用`subprocess`模块来执行外部命令、处理输入输出、捕获错误信息，并探讨一些高级用法。我们还会讨论一些安全性方面的注意事项，以确保您的程序不受到潜在的安全漏洞的威胁。

## 2. 执行外部命令

### 2.1 使用`subprocess.run()`

`subprocess.run()`是Python 3.5及更高版本引入的函数，用于运行外部命令并等待其完成。

以下是一个简单的示例，演示如何使用`subprocess.run()`来执行`ls`命令并获取其输出：

```python
import subprocess

result = subprocess.run(["ls", "-l"], stdout=subprocess.PIPE, text=True)
print(result.stdout)
```

在上面的示例中，`subprocess.run()`接受一个包含命令及其参数的列表，通过`stdout=subprocess.PIPE`参数捕获标准输出，并使用`text=True`参数指定输出为文本。最后，我们打印了`result.stdout`以获取`ls -l`命令的输出。

### 2.2 使用`subprocess.Popen()`

`subprocess.Popen()`提供了更多的灵活性，允许与进程进行交互，而不仅仅是等待它完成。

以下是一个使用`subprocess.Popen()`的示例，演示如何执行外部命令并获取其输出：

```python
import subprocess

# 执行命令
process = subprocess.Popen(["ls", "-l"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)

# 读取标准输出和错误
out, err = process.communicate()

print("标准输出:")
print(out)

print("标准错误:")
print(err)
```

在上面的示例中，首先使用`subprocess.Popen()`来启动进程，并指定`stdout=subprocess.PIPE`和`stderr=subprocess.PIPE`以捕获标准输出和标准错误。然后，使用`process.communicate()`方法来等待进程完成并获取其输出。

### 2.3 指定执行路径

使用`cwd`参数来指定执行外部命令的工作目录。例如，要在特定目录中执行命令，可以这样做：

```python
import subprocess

result = subprocess.run(["ls", "-l"], stdout=subprocess.PIPE, text=True, cwd="/path/to/directory")
print(result.stdout)
```

这将在`/path/to/directory`目录中执行`ls -l`命令。

### 2.4 传递参数

如果命令需要接受参数，可以将它们作为列表的一部分传递给`subprocess.run()`或`subprocess.Popen()`。

例如，要将文件名作为参数传递给命令，可以这样做：

```python
import subprocess

filename = "example.txt"
result = subprocess.run(["cat", filename], stdout=subprocess.PIPE, text=True)
print(result.stdout)
```

这将执行`cat example.txt`命令，其中`filename`是文件名。

## 3. 处理输入输出

### 3.1 标准输入

`subprocess`模块还可以将数据传递给外部命令的标准输入。要实现这一点，可以使用`stdin`参数，并将其设置为一个文件对象或一个字节串。

```python
import subprocess

input_data = "Hello, subprocess!"
result = subprocess.run(["grep", "subprocess"], input=input_data, stdout=subprocess.PIPE, text=True)
print(result.stdout)
```

在上面的示例中，使用`input_data`将数据传递给`grep`命令的标准输入，并搜索包含"subprocess"的行。

### 3.2 标准输出

前面的示例中，已经看到如何捕获外部命令的标准输出。通过使用`stdout`参数，可以将标准输出重定向到文件、字节串或文件对象。

```python
import subprocess

output_file = open("output.txt", "w")
result = subprocess.run(["ls", "-l"], stdout=output_file, text=True)
output_file.close()
```

在上面的示例中，我们将`ls -l`命令的标准输出重定向到一个名为`output.txt`的文件。

### 3.3 标准错误

与标准输出类似，`subprocess`还可以捕获标准错误信息。要捕获标准错误，请使用`stderr`参数。

```python
import subprocess

result = subprocess.run(["ls", "/nonexistent"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
print("标准输出:")
print(result.stdout)
print("标准错误:")
print(result.stderr)
```

在上面的示例中，执行`ls /nonexistent`命令，该命令会产生一个错误，并将标准输出和标准错误信息捕获到`result.stdout`和`result.stderr`中。

## 4. 错误处理

执行外部命令时，通常需要处理错误。以下是一些处理错误的常用方法：

### 4.1 检查返回码

`subprocess.run()`和`subprocess.Popen()`返回一个`CompletedProcess`或`Popen`对象，其中包含有关命令执行的信息，包括返回码。返回码为0表示命令成功执行，非零返回码表示发生错误。

```python
import subprocess

result = subprocess.run(["ls", "/nonexistent"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
if result.returncode != 0:
    print("命令执行失败。")
    print("标准错误:")
    print(result.stderr)
```

在上面的示例中，检查`result.returncode`是否为0，如果不是，就表示命令执行失败。

### 4.2 捕获错误输出

有时，错误信息可能不仅仅包含在返回码中，还包含在标准错误输出中。可以捕获标准错误输出并检查其中的信息。

```python
import subprocess

result = subprocess.run(["ls", "/nonexistent"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
if result.returncode != 0:
    print("命令执行失败。")
    print("错误信息:")
    print(result.stderr)
```

在上面的示例中，我们捕获标准错误输出，并在发生错误时打印它。

## 5. 管道和重定向

`subprocess`还可以创建管道，将一个命令的输出连接到另一个命令的输入。这在处理复杂的数据处理任务时非常有用。

例如，要将一个命令的输出传递给另一个命令，可以这样做：

```python
import subprocess

# 创建第一个命令的进程
process1 = subprocess.Popen(["ls", "/path/to/directory"], stdout=subprocess.PIPE, text=True)

# 创建第二个命令的进程，将第一个命令的输出连接到它的输入
process2 = subprocess.Popen(["grep", "search_term"], stdin=process1.stdout, stdout=subprocess.PIPE, text=True)

# 从第二个命令的标准输出中读取结果
result = process2.communicate()[0]
print(result)
```

在上面的示例中，首先创建第一个命令的进程，然后创建第二个命令的进程，并将第一个命令的输出连接到第二个命令的输入。

## 6. 高级应用

### 6.1 同时读写标准输入输出

`subprocess`模块同时读取和写入标准输入和输出。这对于与外部进程进行双向通信非常有用。

以下是一个示例，演示如何使用`subprocess`进行双向通信：

```python
import subprocess

# 创建命令进程
process = subprocess.Popen(["python", "-u"], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True, universal_newlines=True)

# 写入数据到标准输入
process.stdin.write("print('Hello from child process')\n")
process.stdin.flush()

# 读取并打印标准输出
output, errors = process.communicate()
print("标准输出:")
print(output)

# 打印标准错误
print("标准错误:")
print(errors)
```

在上面的示例中，创建了一个子进程，然后向其标准输入写入Python代码，并捕获其标准输出和标准错误。

### 6.2 超时处理

`subprocess`还允许您设置执行命令的超时时间，以防止命令运行时间过长。要实现这一点，您可以使用`timeout`参数。

例如：

```python
import subprocess

try:
    result = subprocess.run(["sleep", "10"], timeout=5, stdout=subprocess.PIPE, text=True)
    print(result.stdout)
except subprocess.TimeoutExpired:
    print("命令执行超时。")
```

在上面的示例中，试图运行`sleep 10`命令，但由于设置了5秒的超时时间，当命令运行时间超过5秒时，将引发`subprocess.TimeoutExpired`异常。

### 6.3 使用Shell命令

默认情况下，`subprocess`不会使用Shell来执行命令。这是出于安全考虑，以防止潜在的Shell注入攻击。但有些情况下，可能需要使用Shell来执行命令，可以将`shell`参数设置为`True`。

```python
import subprocess

# 使用Shell执行命令
result = subprocess.run("ls -l | grep .txt", shell=True, stdout=subprocess.PIPE, text=True)
print(result.stdout)
```

在上面的示例中，我们使用Shell来执行`ls -l | grep .txt`命令。

## 7. 安全性注意事项

在执行外部命令时，请务必小心处理输入，以防止潜在的安全漏洞。避免将不受信任的数据传递给`subprocess`，以免受到命令注入攻击。

确保了解正在执行的命令及其参数，以避免潜在的风险。

## 总结

Python的`subprocess`模块提供了强大的工具，允许与外部进程进行交互。可以使用它执行外部命令、传递参数、处理输入输出和错误信息，以及支持管道和重定向。这为编写需要与外部程序进行通信的Python应用程序提供了关键的功能。

`subprocess`模块是Python中处理外部进程交互的重要工具，但在使用时需要注意安全性问题，特别是在处理不受信任的输入时。熟练掌握这一模块，将有助于编写更强大和安全的Python应用程序，能够与外部程序进行有效通信。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
