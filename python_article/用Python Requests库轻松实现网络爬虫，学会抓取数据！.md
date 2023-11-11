![](https://p.ipic.vip/cfnkto.png)

Python是一门强大的编程语言，广泛用于网络数据采集和爬虫应用。在这个信息时代，互联网上蕴含着海量的数据，而`Requests`库作为Python爬虫中的重要工具，为我们提供了与Web服务器通信的便捷途径。

这篇文章将介绍`Requests`库，包括其基本用法、高级功能以及示例代码。

## 一、认识Requests

### 1.1 什么是Requests？

`Requests`是一个Python库，用于发起HTTP请求。它是在Python社区中广泛使用的库之一，因其简单的API和强大的功能而备受欢迎。

通过`Requests`，可以轻松地与Web服务器进行通信，发送HTTP请求并处理响应。

### 1.2 安装Requests

使用pip来安装`Requests`库：

```bash
pip install requests
```

### 1.3 导入Requests

导入`requests`模块：

```python
import requests
```

## 二、基本用法

### 2.1 发送GET请求

发送GET请求是获取网页内容的最基本方式。

示例代码：

```python
import requests

# 发送GET请求
response = requests.get("https://www.example.com")

# 获取响应内容
content = response.text

# 打印响应内容
print(content)
```

在这个示例中，使用`get`方法向"https://www.example.com"发送了一个GET请求，并通过`response.text`获取了响应内容。

### 2.2 发送POST请求

向Web服务器提交数据，使用POST请求。

示例代码：

```python
import requests

# 准备要提交的数据
data = {'key1': 'value1', 'key2': 'value2'}

# 发送POST请求
response = requests.post("https://www.example.com/post", data=data)

# 获取响应内容
content = response.text

# 打印响应内容
print(content)
```

### 2.3 设置请求头

有些网站要求设置特定的请求头才能访问，可以使用`headers`参数来设置请求头。

示例代码：

```python
import requests

# 设置请求头
headers = {'User-Agent': 'My Custom User Agent'}

# 发送带有自定义请求头的GET请求
response = requests.get("https://www.example.com", headers=headers)

# 获取响应内容
content = response.text

# 打印响应内容
print(content)
```

### 2.4 处理响应

`Requests`库的响应对象提供了各种方法来处理响应内容、状态码等信息。

示例代码：

```python
import requests

# 发送GET请求
response = requests.get("https://www.example.com")

# 获取响应内容
content = response.text

# 获取响应状态码
status_code = response.status_code

# 判断请求是否成功
if response.status_code == 200:
    print("请求成功")
else:
    print("请求失败")

# 获取响应头信息
headers = response.headers

# 获取响应的URL
url = response.url

# 获取响应的编码
encoding = response.encoding

# 获取响应的字节内容
content_bytes = response.content
```

## 三、高级功能

### 3.1 处理JSON数据

`Requests`库可以方便地处理JSON格式的数据。如果服务器返回的响应是JSON格式，可以使用`json()`方法来解析它。

```python
import requests

# 发送GET请求，获取JSON数据
response = requests.get("https://jsonplaceholder.typicode.com/posts/1")

# 解析JSON响应
data = response.json()

# 打印JSON数据
print(data)
```

### 3.2 处理响应头

使用响应对象的`headers`属性来访问响应头信息。

示例代码：

```python
import requests

# 发送GET请求
response = requests.get("https://www.example.com")

# 获取响应头信息
headers = response.headers

# 打印响应头
for key, value in headers.items():
    print(f"{key}: {value}")
```

### 3.3 处理异常

在实际应用中，网络请求可能会出现各种异常情况。`Requests`库允许捕获这些异常并进行适当的处理。

```python
import requests

try:
    # 发送GET请求
    response = requests.get("https://www.example.com")

    # 如果请求成功
    if response.status_code == 200:
        print("请求成功")
    else:
        print(f"请求失败，状态码：{response.status_code}")
except requests.exceptions.RequestException as e:
    print(f"请求异常：{e}")
```

## 四、完整代码示例

以下是一个完整的示例，演示了如何使用`Requests`库发送HTTP请求、处理响应和异常：

```python
import requests

try:
    # 设置请求头
    headers = {'User-Agent': 'My Custom User Agent'}

    # 发送GET请求
    response = requests.get("https://www.example.com", headers=headers)

    # 如果请求成功
    if response.status_code == 200:
        print("请求成功")

        # 获取响应内容
        content = response.text

        # 打印响应内容
        print(content)
    else:
        print(f"请求失败，状态码：{response.status_code}")

except requests.exceptions.RequestException as e:
    print(f"请求异常：{e}")
```

这个示例展示了如何发送带有自定义请求头的GET请求，并处理请求成功、失败和异常情况。

## 总结

`Requests`库是Python爬虫中不可或缺的工具之一。它简化了与Web服务器的通信，提供了丰富的功能，可以轻松地发送HTTP请求、处理响应以及处理异常情况。无论是要爬取网页内容、调用API接口还是进行其他网络数据收集工作，`Requests`都能满足需求。

在实际应用中，可以结合其他Python库和工具，构建强大的网络爬虫应用，从而实现各种有趣的数据挖掘和分析任务。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
