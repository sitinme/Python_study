![](https://p.ipic.vip/cfnkto.png)

AutoEDA（自动探索性数据分析）工具库是数据科学中至关重要的一部分。它们能够自动生成数据摘要、探查数据的基本特征、检测异常值和提供可视化，为数据科学家和分析师们提供了解数据的便捷方式。以下是一些常见的AutoEDA工具库及其功能和示例代码。

## 1. Pandas-Profiling

### 概述
Pandas-Profiling是一个基于Pandas的数据探索性分析工具。它提供了数据集的摘要统计信息、变量分布、相关性矩阵和异常值等详尽信息，帮助用户更快地了解数据集。

### 示例代码
```python
import pandas as pd
from pandas_profiling import ProfileReport

data = pd.read_csv("your_dataset.csv")
profile = ProfileReport(data)
profile.to_file("output.html")
```

## 2. SweetViz

### 概述
SweetViz是一个交互式的EDA工具，以可视化的方式展示数据报告。它提供了数据的摘要统计信息、分布图、对比图和相关性图等可视化内容。

### 示例代码
```python
import sweetviz as sv

data = pd.read_csv("your_dataset.csv")
report = sv.analyze(data)
report.show_html("output.html")
```

## 3. Autoviz

### 概述
Autoviz是一个简单易用的EDA库，它能够自动生成数据集的可视化摘要。用户只需一行代码即可生成数据的关键可视化图表。

### 示例代码
```python
from autoviz.AutoViz_Class import AutoViz_Class

AV = AutoViz_Class()
report = AV.AutoViz("your_dataset.csv")
```

## 4. D-Tale

### 概述
D-Tale是一个交互式数据分析工具，提供了数据的详细分析和可视化。它生成数据的概要统计信息、图表和可视化图，并允许用户对数据进行交互式操作。

### 示例代码
```python
import dtale

data = pd.read_csv("your_dataset.csv")
dtale.show(data)
```

## 5. DataPrep

### 概述
DataPrep是一个数据准备工具，它提供了数据探索和预处理的功能。能够自动检测数据类型、缺失值和异常值。

### 示例代码
```python
from dataprep.eda import create_report

report = create_report(df)
report.show_browser()
```


## 6. Exploratory

### 概述
Exploratory是一个交互式的数据分析平台，提供了多种可视化方法和数据探索功能。用户可以生成图表、热力图、并且自动探索数据之间的相关性。

### 示例代码
```python
# Exploratory是基于网页的平台，需要使用其提供的界面进行数据分析。
# 用户可导入数据并在平台上进行交互式数据分析。
```

## 7. Lux

### 概述
Lux是一个基于Pandas的自动可视化工具，能够根据数据集自动推荐可视化图表。它简化了可视化流程，为数据提供更多探索机会。

### 示例代码
```python
import lux

df = pd.read_csv("your_dataset.csv")
df.set_executor_type("Pandas") # Lux需要将数据集设置为Pandas执行器类型
df.set_context(["column_name"]) # 用户可根据需要设置上下文
df
```

## 8. DataPrep

### 概述
DataPrep是一个用于数据探索和预处理的库。它提供了EDA报告、数据类型检测、缺失值分析和数据预处理功能。

### 示例代码
```python
from dataprep.eda import create_report

report = create_report(df)
report.show_browser()
```

## 9. PandasGUI

### 概述
PandasGUI是一个用于数据分析和探索的桌面应用程序，提供了交互式的GUI界面，用户可视化地探索数据和进行分析。

### 示例代码
```python
from pandasgui import show

show(df) # 将DataFrame传递给PandasGUI
```

## 总结

AutoEDA工具库为数据探索和分析提供了多种工具和方法，每个工具都有其独特的优势。选择适合自己项目需求和个人偏好的工具，能够帮助提高数据分析的效率和质量。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
