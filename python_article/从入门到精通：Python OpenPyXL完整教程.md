![](https://p.ipic.vip/cfnkto.png)

OpenPyXL是一个强大的Python库，用于处理Excel文件，允许读取、编辑和创建Excel工作簿和工作表。无论是需要自动化处理大量数据，还是创建漂亮的报告，OpenPyXL都是一个强大的工具。本文将详细介绍OpenPyXL的各种功能，包括读取、写入、样式设置等，以及大量示例代码来帮助你深入理解。

## 安装OpenPyXL

要开始使用OpenPyXL，首先需要安装它。

使用pip进行安装：

```bash
pip install openpyxl
```

安装完成后，就可以导入OpenPyXL并开始处理Excel文件了。

```python
import openpyxl
```

## 打开和创建工作簿

### 打开现有工作簿

使用OpenPyXL，可以打开现有的Excel工作簿，然后对其进行读取和编辑。

下面是打开工作簿的示例：

```python
import openpyxl

# 打开工作簿
workbook = openpyxl.load_workbook('example.xlsx')

# 获取工作表
sheet = workbook['Sheet1']

# 读取单元格数据
cell_value = sheet['A1'].value
print(cell_value)
```

### 创建新工作簿

可以使用OpenPyXL创建新的Excel工作簿，然后将数据写入其中。

下面是创建新工作簿的示例：

```python
import openpyxl

# 创建新工作簿
workbook = openpyxl.Workbook()

# 获取默认工作表
sheet = workbook.active

# 写入数据到单元格
sheet['A1'] = 'Hello'
sheet['B1'] = 'World'

# 保存工作簿
workbook.save('new_example.xlsx')
```

## 读取和写入数据

### 读取单元格数据

可以使用OpenPyXL读取工作表中的单元格数据。

以下是一些示例：

```python
import openpyxl

workbook = openpyxl.load_workbook('example.xlsx')
sheet = workbook['Sheet1']

# 读取单元格数据
cell_value = sheet['A1'].value
print(cell_value)

# 通过行和列索引读取数据
cell_value = sheet.cell(row=2, column=3).value
print(cell_value)
```

### 写入数据到单元格

要将数据写入工作表，可以简单地为单元格分配一个值。

以下是示例：

```python
import openpyxl

workbook = openpyxl.Workbook()
sheet = workbook.active

# 写入数据到单元格
sheet['A1'] = 'Hello'
sheet.cell(row=2, column=2, value='World')

# 保存工作簿
workbook.save('new_example.xlsx')
```

## 操作工作表

OpenPyXL还可以操作工作表，包括创建、复制、删除等。

以下是一些示例：

### 创建新工作表

可以创建新的工作表，并将其添加到工作簿中：

```python
import openpyxl

workbook = openpyxl.Workbook()

# 创建新的工作表
new_sheet = workbook.create_sheet(title='NewSheet')

# 保存工作簿
workbook.save('new_example.xlsx')
```

### 复制工作表

要复制现有的工作表，可以使用`copy_worksheet`方法：

```python
import openpyxl

workbook = openpyxl.load_workbook('example.xlsx')

# 复制工作表
copied_sheet = workbook.copy_worksheet(workbook['Sheet1'])
copied_sheet.title = 'Copy of Sheet1'

# 保存工作簿
workbook.save('example_with_copy.xlsx')
```

### 删除工作表

要删除工作表，使用`remove`方法：

```python
import openpyxl

workbook = openpyxl.load_workbook('example.xlsx')

# 删除工作表
del workbook['Sheet2']

# 保存工作簿
workbook.save('example_without_sheet2.xlsx')
```

## 设置样式

OpenPyXL还支持样式设置，可以设置字体、背景颜色、边框等。以下是一些示例：

### 设置字体样式

```python
import openpyxl
from openpyxl.styles import Font

workbook = openpyxl.Workbook()
sheet = workbook.active

# 创建字体样式
font = Font(name='Arial', bold=True, size=14)

# 将字体样式应用到单元格
sheet['A1'].font = font

# 保存工作簿
workbook.save('example_with_font.xlsx')
```

### 设置背景颜色

```python
import openpyxl
from openpyxl.styles import PatternFill

workbook = openpyxl.Workbook

()
sheet = workbook.active

# 创建背景颜色样式
fill = PatternFill(start_color='FFFF00', end_color='FFFF00', fill_type='solid')

# 将背景颜色应用到单元格
sheet['B2'].fill = fill

# 保存工作簿
workbook.save('example_with_fill.xlsx')
```

### 设置边框

```python
import openpyxl
from openpyxl.styles import Border, Side

workbook = openpyxl.Workbook()
sheet = workbook.active

# 创建边框样式
border = Border(left=Side(style='thin'), right=Side(style='thin'), top=Side(style='thin'), bottom=Side(style='thin'))

# 将边框应用到单元格
sheet['C3'].border = border

# 保存工作簿
workbook.save('example_with_border.xlsx')
```

## 总结

Python OpenPyXL是一个功能强大的库，用于处理Excel文件，无论是在办公自动化中使用Excel文件，还是需要对大量数据进行分析，OpenPyXL都是一个强有力的工具。在本文中，介绍了OpenPyXL的安装方法，然后分享了如何打开、创建工作簿，读取和写入数据，以及如何操作工作表和设置样式。

通过本文，学会了如何使用OpenPyXL打开已有的Excel文件，读取和编辑其中的数据，也学会了如何创建新的工作簿，将数据写入其中，以及如何操作工作表，包括创建、复制和删除工作表。此外，还了解了如何设置样式，包括字体、背景颜色和边框，以美化Excel文件。

使用Python OpenPyXL，可以轻松地处理各种Excel文件，从而提高办公效率和数据处理能力。无论是日常工作还是数据分析，OpenPyXL都将成为得力助手。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
