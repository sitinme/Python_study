![](https://p.ipic.vip/cfnkto.png)

Microsoft Word是最常用的文档处理工具之一，但有时需要以编程方式生成或修改Word文档。Python中有一个`python-docx`的库，它允许创建、修改和操作Word文档。

本文将详细介绍`python-docx`库的用法，包括如何创建文档、添加文本、格式化文本、插入表格和图片等。

## 1. 安装python-docx

首先，需要安装`python-docx`库。

使用pip来安装它：

```bash
pip install python-docx
```

## 2. 创建一个Word文档

使用`python-docx`创建一个新的Word文档非常简单。首先，导入库并创建一个`Document`对象：

```python
from docx import Document

doc = Document()
```

现在，你已经创建了一个空白的Word文档。

## 3. 添加标题和段落

使用`add_heading`方法添加标题和`add_paragraph`方法添加段落：

```python
# 添加标题
doc.add_heading('Python文档示例', 0)

# 添加段落
doc.add_paragraph('这是一个使用python-docx创建的Word文档示例。')
```

## 4. 格式化文本

`python-docx`还允许对文本进行格式化，比如设置字体、颜色、大小和样式。

下面是一个示例：

```python
from docx.shared import Pt
from docx.oxml.ns import qn

# 创建一个段落
p = doc.add_paragraph()

# 添加文本
p.add_run('这是加粗的文本。').bold = True
p.add_run('这是斜体的文本。').italic = True

# 设置字体大小和颜色
run = p.add_run('这是红色的文本。')
run.font.size = Pt(14)
run.font.color.rgb = qn('FF0000')

# 添加下划线
run = p.add_run('这是带下划线的文本。')
run.underline = True
```

## 5. 插入表格

使用`add_table`方法来插入表格：

```python
from docx.oxml.ns import qn
from docx.shared import Inches

# 创建一个表格
table = doc.add_table(rows=3, cols=3)

# 设置表格样式
table.style = 'Table Grid'

# 填充表格数据
for row in table.rows:
    for cell in row.cells:
        cell.text = '单元格内容'

# 合并单元格
table.cell(0, 0).merge(table.cell(1, 1))
```

## 6. 插入图片

要插入图片，使用`add_picture`方法。确保图片文件存在于相应的路径：

```python
from docx.shared import Inches

# 插入图片
doc.add_picture('example.png', width=Inches(4), height=Inches(3))
```

## 7. 保存文档

当完成文档的创建和编辑后，使用`save`方法将文档保存到磁盘：

```python
doc.save('example.docx')
```

## 8. 完整示例

以下是一个完整的示例，演示了如何创建一个Word文档并添加标题、段落、格式化文本、表格和图片：

```python
from docx import Document
from docx.shared import Pt
from docx.oxml.ns import qn
from docx.shared import Inches

# 创建一个空白文档
doc = Document()

# 添加标题
doc.add_heading('Python文档示例', 0)

# 添加段落
doc.add_paragraph('这是一个使用python-docx创建的Word文档示例。')

# 创建一个段落
p = doc.add_paragraph()

# 添加文本
p.add_run('这是加粗的文本。').bold = True
p.add_run('这是斜体的文本。').italic = True

# 设置字体大小和颜色
run = p.add_run('这是红色的文本。')
run.font.size = Pt(14)
run.font.color.rgb = qn('FF0000')

# 添加下划线
run = p.add_run('这是带下划线的文本。')
run.underline = True

# 创建一个表格
table = doc.add_table(rows=3, cols=3)

# 设置表格样式
table.style = 'Table Grid'

# 填充表格数据
for row in table.rows:
    for cell in row.cells:
        cell.text = '单元格内容'

# 合并单元格
table.cell(0, 0).merge(table.cell(1, 1))

# 插入图片
doc.add_picture('example.png', width=Inches(4), height=Inches(3))

# 保存文档
doc.save('example.docx')
```

这个示例创建了一个简单的Word文档，其中包含标题、段落、格式化文本、表格和图片。可以根据自己的需求修改和扩展这个示例，以生成各种类型的Word文档。

## 总结

在本文中，分享了Python中的文档处理工具 - python-docx库。从安装和基础使用开始，逐步介绍了如何创建、编辑和格式化Word文档，包括文本、段落、表格、样式等方面。还讨论了如何插入图片、超链接和页眉页脚，以及如何进行邮件合并等高级功能。

Python docx库是一个功能丰富而强大的工具，可用于自动化文档生成，报告创建，甚至办公文档的批量处理。通过本文的学习，可以轻松掌握使用python-docx库的技能，将其应用于各种实际场景中，提高工作效率。

无论是需要自动创建报告、生成文档，或者进行文档处理，python-docx都可以成为得力助手。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
