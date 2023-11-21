![](https://p.ipic.vip/cfnkto.png)

JavaScript 是一门强大的脚本语言，广泛应用于网页前端开发、构建交互式用户界面以及处理各种客户端端任务。然而，有时可能需要在 Python 环境中执行 JavaScript 代码，无论是为了与网页进行交互，自动化浏览器操作，还是执行需要 JavaScript 的任务。

本文将介绍多种方法，帮助你在 Python 中执行 JavaScript 代码，并提供详尽的示例代码，使你能够轻松掌握这一技能。

## 1. 为什么需要在 Python 中执行 JavaScript

在 Python 中执行 JavaScript 代码的需求有多种情形，其中一些包括：

- **Web 自动化：** 通过执行 JavaScript，可以模拟用户在网页上的交互，例如点击按钮、填写表单等，从而自动化 Web 浏览器操作。
- **Web 数据抓取：** 一些网站使用 JavaScript 动态生成内容，通过在 Python 中执行 JavaScript，可以获取这些动态生成的数据。
- **前端开发：** 可以在 Python 环境中测试前端代码，以确保它与后端服务协同工作无误。
- **Web 应用集成：** 将 Python 后端与 JavaScript 前端进行集成，以构建更复杂的 Web 应用程序。


## 2. 使用 Python 内置库 execjs 执行 JavaScript

[execjs](https://pypi.org/project/PyExecJS/) 是 Python 的内置库，允许执行 JavaScript 代码。这种方法适用于执行简单的 JavaScript 代码，无需浏览器环境。

### 安装 execjs

首先，安装 execjs。

使用 pip 执行以下命令：

```bash
pip install PyExecJS
```

### 执行 JavaScript 代码

以下是一个使用 execjs 执行 JavaScript 代码的示例：

```python
import execjs

# 创建一个 JavaScript 上下文
ctx = execjs.compile("""
function add(x, y) {
    return x + y;
}
""")

# 在上下文中执行 JavaScript 函数
result = ctx.call("add", 3, 4)
print(result)
```

在这个示例中，使用 execjs 创建了一个 JavaScript 上下文，然后在该上下文中执行了 JavaScript 函数。可以在上下文中执行任何 JavaScript 代码。

## 3. 使用 PyExecJS 执行 JavaScript

[PyExecJS](https://pypi.org/project/PyExecJS/) 是另一个用于执行 JavaScript 代码的 Python 库，提供与 execjs 类似的功能。

### 安装 PyExecJS

使用 pip 安装 PyExecJS：

```bash
pip install PyExecJS
```

### 执行 JavaScript 代码

以下是一个使用 PyExecJS 执行 JavaScript 代码的示例：

```python
import PyExecJS

# 创建一个 PyExecJS 上下文
ctx = PyExecJS.compile("""
function multiply(x, y) {
    return x * y;
}
""")

# 在上下文中执行 JavaScript 函数
result = ctx.call("multiply", 3, 4)
print(result)
```

在此示例中，使用 PyExecJS 创建了一个 JavaScript 上下文，然后在该上下文中执行了 JavaScript 函数。这与使用 execjs 类似。

## 4. 使用 Selenium 与 WebDriver 执行 JavaScript

[Selenium](https://www.selenium.dev/) 是一个用于自动化浏览器操作的工具，它可以与不同的浏览器一起使用，包括 Chrome、Firefox、Edge 等。通过 Selenium 和浏览器驱动程序（如 ChromeDriver、GeckoDriver），可以执行 JavaScript 代码，并与页面元素进行交互。

### 安装 Selenium

首先，安装 Selenium。使用 pip 执行以下命令：

```bash
pip install selenium
```

然后，需要下载适用于你所使用的浏览器的 WebDriver。例如，如果使用 Chrome 浏览器，你需要下载 [ChromeDriver](https://sites.google.com/chromium.org/driver/)。

### 执行 JavaScript 代码

以下是一个使用 Selenium 执行 JavaScript 代码的示例：

```python
from selenium import webdriver

# 初始化 Chrome 浏览器驱动
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')

# 打开网页
driver.get('https://example.com')

# 执行 JavaScript 代码
result = driver.execute_script('return 3 + 4;')
print(result)

# 关闭浏览器
driver.quit()
```

在这个示例中，首先初始化了 Chrome 浏览器驱动，然后打开了一个网页。接着，使用 `driver.execute_script` 方法执行了 JavaScript 代码，最后关闭了浏览器。

## 5. 使用 Node.js 执行 JavaScript

[Node.js](https://nodejs.org/) 是一个基于 Chrome V8 引擎的 JavaScript 运行时，允许在服务器端运行 JavaScript 代码。可以使用 Node.js 来执行 JavaScript 脚本，并从 Python 中调用 Node.js 进程。

### 安装 Node.js

首先，安装 Node.js。可以从 [Node.js 官方网站](https://nodejs.org/) 下载并安装 Node.js。

### 创建 JavaScript 文件

创建一个 JavaScript 文件，例如 `my_script.js`，其中包含想要执行的 JavaScript 代码。

下面是一个示例：

```javascript
// my_script.js

function add(x, y) {
    return x + y;
}

add(3, 4);
```

### 执行 JavaScript 代码

下面是一个使用 Python 调用 Node.js 执行 JavaScript 代码的示例：

```python
import subprocess

# 执行 Node.js 进程并运行 JavaScript 文件
result = subprocess.check_output(['node', 'my_script.js'], text=True)
print(result)
```

在这个示例中，使用 Python 的 `subprocess` 模块启动了一个 Node.js 进程，并运行了 `my_script.js` 文件中的 JavaScript 代码。

## 6. 选择合适的方法

选择在 Python 中执行 JavaScript 代码的方法取决于你的需求和使用情况：

- 如果只需执行一些简单的 JavaScript 代码而无需浏览器环境，使用 `execjs` 或 `PyExecJS` 是一种轻量级的方法。
- 如果需要与网页进行交互或自动化浏览器操作，Selenium 与 WebDriver 是不二选择。
- 如果希望在服务器端运行 JavaScript 代码，并从 Python 中调用，Node.js 是最佳选项。

根据项目需求，选择适合的方法。

## 总结

在 Python 中执行 JavaScript 代码可以帮助完成多种任务，包括 Web 自动化、数据抓取、前端开发和 Web 应用集成。

本文介绍了多种方法，包括使用内置库 `execjs` 和 `PyExecJS`、Selenium 与 WebDriver，以及调用 Node.js 进程。根据具体的需求和使用情况，选择适合的方法，可以更高效地执行 JavaScript 代码，从而实现更多功能。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
