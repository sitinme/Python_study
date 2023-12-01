![](https://p.ipic.vip/cfnkto.png)

Python 中的 PymuPDF 是一个强大的库，可以让你轻松地处理 PDF 文件。本文将深入探讨 PymuPDF 的用法，包括打开、读取、修改和创建 PDF 文件，以及文本提取和页面操作。

## 1. 安装 PymuPDF

首先，确保安装了 PymuPDF 库。

可以使用 `pip` 安装：

```bash
pip install pymupdf
```

## 2. 打开和读取 PDF 文件

使用 PymuPDF 可以打开和读取现有的 PDF 文件。

```python
import fitz

# 打开 PDF 文件
pdf_document = fitz.open("example.pdf")

# 获取总页数
total_pages = pdf_document.page_count
print(f"总页数: {total_pages}")

# 读取文本
page = pdf_document.load_page(0)  # 读取第一页
text = page.get_text("text")
print(f"第一页文本:\n{text}")
```

## 3. 提取文本和元数据

可以提取 PDF 文件中的文本和元数据。

```python
# 提取整个文档的文本
full_text = ""
for page_num in range(total_pages):
    page = pdf_document.load_page(page_num)
    full_text += page.get_text("text")

print(f"整个文档文本:\n{full_text}")

# 提取元数据
metadata = pdf_document.metadata
print(f"元数据:\n{metadata}")
```

## 4. 修改现有 PDF

PymuPDF 允许修改现有的 PDF 文件，如添加文本、高亮或删除内容。

```python
# 添加文本到现有 PDF 文件
page = pdf_document[0]
page.insert_text((100, 100), "Hello, PymuPDF!")

# 保存修改
pdf_document.save("modified_example.pdf")
```

## 5. 创建新的 PDF 文件

使用 PymuPDF 也可以创建新的 PDF 文件。

```python
new_document = fitz.open()
new_page = new_document.new_page()

# 添加文本到新页面
new_page.insert_text((100, 100), "New PDF Document")

# 保存新的 PDF 文件
new_document.save("new_document.pdf")
```

## 6. 页面操作和图像提取

PymuPDF 也支持页面操作，比如裁剪页面、旋转页面，以及提取页面中的图像。

```python
# 裁剪页面
page = pdf_document[0]
page.select(clip=[0, 0, 300, 300])

# 旋转页面
page = pdf_document[1]
page.set_rotation(90)

# 提取页面中的图像
images = page.get_images(full=True)
print(f"页面中的图像:\n{images}")
```

## 总结

PymuPDF 提供了丰富的功能，能够轻松地处理 PDF 文件。无论是提取文本、操作页面、修改现有 PDF 还是创建新的 PDF 文件，这个库都能胜任。掌握 PymuPDF 的使用，能够为 PDF 文件操作提供强大的工具和方法。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
