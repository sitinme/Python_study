![](https://p.ipic.vip/cfnkto.png)

Beautiful Soup（简称BS4）是一种强大而灵活的HTML和XML解析库，广泛用于Python爬虫和数据采集中。

这篇文章介绍 Beautiful Soup的功能和用法，并提供示例代码，帮助你更好地理解和应用这个优秀的库。

## 一、Beautiful Soup简介

### 1.1 什么是Beautiful Soup？

Beautiful Soup是一个Python库，用于解析HTML和XML文档，并提供了简单而直观的方式来遍历文档树、搜索特定标签和提取数据。它的名字取自路易斯·卡洛斯·蒙特斯·库比斯（Luis Carlos Monteiro Cabral de Melo）的诗歌《Alice》中的一句话：“Beautiful Soup so rich and green, Waiting in a hot tureen!”，寓意着它用来“捞取”美味的数据。

### 1.2 安装Beautiful Soup

使用pip来安装Beautiful Soup库：

```bash
pip install beautifulsoup4
```

同时，为了能够解析HTML和XML文档，还需要安装一个解析器，如lxml或html5lib：

```bash
pip install lxml
# 或
pip install html5lib
```

### 1.3 导入Beautiful Soup

导入Beautiful Soup库：

```python
from bs4 import BeautifulSoup
```

## 二、Beautiful Soup的基本用法

### 2.1 解析HTML文档

Beautiful Soup可以解析HTML或XML文档，并将其转换成文档树的形式，以便于遍历和操作。

示例代码：

```python
from bs4 import BeautifulSoup

# HTML文档示例
html_doc = """
<html>
    <head>
        <title>我的第一个网页</title>
    </head>
    <body>
        <h1>欢迎来到我的网页</h1>
        <p>这是一个段落。</p>
    </body>
</html>
"""

# 创建Beautiful Soup对象
soup = BeautifulSoup(html_doc, 'html.parser')
```

在这个示例中，创建了一个Beautiful Soup对象，并使用`html.parser`解析器解析了HTML文档。

### 2.2 遍历文档树

一旦有了Beautiful Soup对象，就可以遍历文档树，查找特定的标签和数据。

以下是一些基本的遍历方法：

#### 2.2.1 查找标签

使用`find()`方法来查找特定的标签：

```python
# 查找第一个<h1>标签
h1_tag = soup.find('h1')

# 打印标签文本
print(h1_tag.text)
```

#### 2.2.2 遍历子节点

使用`children`属性来遍历一个标签的子节点：

```python
# 遍历<body>标签的子节点
body_tag = soup.find('body')
for child in body_tag.children:
    print(child)
```

#### 2.2.3 遍历所有标签

使用`find_all()`方法来查找所有特定类型的标签：

```python
# 查找所有<p>标签
p_tags = soup.find_all('p')

# 遍历所有<p>标签
for p_tag in p_tags:
    print(p_tag.text)
```

### 2.3 提取数据

找到目标标签，就可以提取其中的数据。

以下是一些提取数据的示例：

#### 2.3.1 获取标签文本

使用`.text`属性获取标签的文本内容：

```python
# 获取<h1>标签的文本内容
h1_text = h1_tag.text
print(h1_text)
```

#### 2.3.2 获取标签属性

如果标签有属性，可以使用字典的方式获取：

```python
# 获取<head>标签的lang属性值
head_tag = soup.find('head')
lang_value = head_tag['lang']
print(lang_value)
```

#### 2.3.3 提取链接

如果要提取链接，可以使用`.get()`方法：

```python
# 获取<a>标签的链接
a_tag = soup.find('a')
link = a_tag.get('href')
print(link)
```

## 三、高级用法

### 3.1 使用CSS选择器

Beautiful Soup支持使用CSS选择器来查找标签，这使得查找更灵活和方便：

```python
# 使用CSS选择器查找所有<p>标签
p_tags = soup.select('p')
```

### 3.2 嵌套查找

在查找方法中嵌套使用，以查找更深层次的标签：

```python
# 查找<body>标签下的所有<p>标签
p_tags = soup.find('body').find_all('p')
```

### 3.3 处理不规范的HTML

Beautiful Soup可以处理不规范的HTML文档，自动修复标签嵌套和缺失的情况：

```python
# 处理不规范的HTML文档
dirty_html = "<p>这是一个段落</p>"
soup = BeautifulSoup(dirty_html, 'html.parser')
print(soup.prettify())
```

## 四、示例代码

以下是一个完整的示例，演示了如何使用Beautiful Soup解析HTML文档、遍历文档树、查找标签和提取数据：

```python
from bs4 import BeautifulSoup

# HTML文档示例
html_doc = """
<html>
    <head>
        <title>我的第一个网页</title>
    </head>
    <body>
        <h1>欢迎来到我的网页</h1>
        <p>这是一个段落。</p>
    </body>
</html>
"""

# 创建Beautiful Soup对象
soup = BeautifulSoup(html_doc, 'html.parser')

# 查找<h1>标签
h1_tag = soup.find('h1')

# 获取<h1>标签的文本内容
h1_text = h1_tag.text

# 查找所有<p>标签
p_tags = soup.find_all('p')

# 提取第一个<p>标签的文本内容
p_text = p_tags[0].text

# 打印结果
print("标题:", h1_text)
print("段落:", p_text)
```

这个示例演示了如何解析HTML文档、查找标签和提取数据，以及如何处理不规范的HTML文档。

## 总结

Beautiful Soup是一个强大的HTML和XML解析库，为Python爬虫和数据采集提供了强大的工具。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
