![](https://p.ipic.vip/cfnkto.png)

PyPDF2是一个Python库，用于处理PDF文件，包括合并、分割、旋转和提取文本等操作。它是一个功能强大且灵活的工具，可用于自动化处理PDF文件，适用于各种应用，从文档管理到数据分析。

本文将深入介绍PyPDF2库，掌握如何利用它来处理PDF文件。

## 安装PyPDF2

在开始之前，需要安装PyPDF2库。使用pip进行安装：

```bash
pip install PyPDF2
```

## 基本PDF操作

### 1. 合并PDF文件

使用PyPDF2合并多个PDF文件为一个文件。

以下是一个示例代码：

```python
import PyPDF2

pdf1 = open("file1.pdf", "rb")
pdf2 = open("file2.pdf", "rb")
output = open("merged.pdf", "wb")

pdf_reader1 = PyPDF2.PdfFileReader(pdf1)
pdf_reader2 = PyPDF2.PdfFileReader(pdf2)
pdf_writer = PyPDF2.PdfFileWriter()

for page_num in range(pdf_reader1.numPages):
    page = pdf_reader1.getPage(page_num)
    pdf_writer.addPage(page)

for page_num in range(pdf_reader2.numPages):
    page = pdf_reader2.getPage(page_num)
    pdf_writer.addPage(page)

pdf_writer.write(output)

pdf1.close()
pdf2.close()
output.close()
```

### 2. 分割PDF文件

分割一个PDF文件为多个文件。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("source.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)

for page_num in range(pdf_reader.numPages):
    pdf_writer = PyPDF2.PdfFileWriter()
    pdf_writer.addPage(pdf_reader.getPage(page_num))
    output = open(f"page_{page_num + 1}.pdf", "wb")
    pdf_writer.write(output)
    output.close()

pdf.close()
```

### 3. 旋转PDF页面

旋转PDF页面。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("file.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)
pdf_writer = PyPDF2.PdfFileWriter()

for page_num in range(pdf_reader.numPages):
    page = pdf_reader.getPage(page_num)
    page.rotateClockwise(90)  # 旋转90度
    pdf_writer.addPage(page)

output = open("rotated.pdf", "wb")
pdf_writer.write(output)

pdf.close()
output.close()
```

### 4. 提取PDF文本

提取PDF中的文本。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("file.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)

text = ""
for page_num in range(pdf_reader.numPages):
    page = pdf_reader.getPage(page_num)
    text += page.extractText()

print(text)
```

## 高级PDF操作

### 1. 添加水印

在PDF页面上添加水印。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("file.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)
pdf_writer = PyPDF2.PdfFileWriter()

watermark = PyPDF2.PdfFileReader(open("watermark.pdf", "rb"))

for page_num in range(pdf_reader.numPages):
    page = pdf_reader.getPage(page_num)
    page.mergePage(watermark.getPage(0))
    pdf_writer.addPage(page)

output = open("watermarked.pdf", "wb")
pdf_writer.write(output)

pdf.close()
output.close()
```

### 2. 加密PDF文件

使用PyPDF2来加密PDF文件。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("file.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)
pdf_writer = PyPDF2.PdfFileWriter()

for page_num in range(pdf_reader.numPages):
    page = pdf_reader.getPage(page_num)
    pdf_writer.addPage(page)

pdf_writer.encrypt("password", "owner_password")
output = open("encrypted.pdf", "wb")
pdf_writer.write(output)

pdf.close()
output.close()
```

### 3. 提取图像

使用PyPDF2提取PDF中的图像。

以下是一个示例代码：

```python
import PyPDF2

pdf = open("file.pdf", "rb")
pdf_reader = PyPDF2.PdfFileReader(pdf)

for page_num in range(pdf_reader.numPages):
    page = pdf_reader.getPage(page_num)
    xObject = page['/Resources']['/XObject'].get_object()
    for obj in xObject:
        if xObject[obj]['/Subtype'] == '/Image':
            img = xObject[obj]
            data = img.get_data()
            with open(f"image_{page_num + 1}.jpg", "wb") as f:
                f.write(data)

pdf.close()
```

## 总结

PyPDF2是一个功能丰富的Python库，用于处理PDF文件。无论是需要合并、分割、旋转、提取文本，还是进行更高级的操作如添加水印、加密、提取图像，PyPDF2都能满足需求。

通过本文的介绍和示例代码，可以更好地掌握PyPDF2，将其应用于各种PDF文件处理任务中，提高工作效率，简化操作。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
