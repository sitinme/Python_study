![](https://p.ipic.vip/cfnkto.png)

时间序列数据是许多领域的核心，从金融市场到气象学，都需要对时间序列数据进行分析和可视化。

Python提供了丰富的库和工具，用于处理和绘制时间序列数据。

以下8种不同的绘图类型，在分析时间序列数据比较常用。

## 1. 折线图

折线图是最常见的时间序列数据可视化类型之一。它显示了数据随时间的变化趋势，通常以连续的折线表示。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'日期': pd.date_range(start='2023-01-01', periods=30, freq='D'),
        '数值': [10, 15, 13, 12, 18, 20, 22, 25, 28, 30, 35, 40, 38, 36, 34, 32, 30, 28, 26, 24, 22, 20, 18, 16, 14, 12, 10, 8, 6, 4]}

df = pd.DataFrame(data)
plt.plot(df['日期'], df['数值'])
plt.xlabel('日期')
plt.ylabel('数值')
plt.title('折线图')
plt.show()
```

## 2. 散点图

散点图用于表示数据点的分布和关系，适合展示时间序列数据中的离散观测。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'日期': pd.date_range(start='2023-01-01', periods=30, freq='D'),
        '数值': [10, 15, 13, 12, 18, 20, 22, 25, 28, 30, 35, 40, 38, 36, 34, 32, 30, 28, 26, 24, 22, 20, 18, 16, 14, 12, 10, 8, 6, 4]}

df = pd.DataFrame(data)
plt.scatter(df['日期'], df['数值'])
plt.xlabel('日期')
plt.ylabel('数值')
plt.title('散点图')
plt.show()
```

## 3. 柱状图

柱状图适用于展示时间序列数据的分组或分类，通常用于比较不同时间点或不同组之间的数据。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'日期': pd.date_range(start='2023-01-01', periods=5, freq='D'),
        '数值1': [10, 15, 13, 12, 18],
        '数值2': [5, 8, 7, 6, 10]}

df = pd.DataFrame(data)
df.set_index('日期', inplace=True)
df.plot(kind='bar')
plt.xlabel('日期')
plt.ylabel('数值')
plt.title('柱状图')
plt.show()
```

## 4. 面积图

面积图是折线图的一种变体，用于显示时间序列数据的趋势和数据点之间的关系。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'日期': pd.date_range(start='2023-01-01', periods=30, freq='D'),
        '数值1': [10, 15, 13, 12, 18, 20, 22, 25, 28, 30, 35, 40, 38, 36, 34, 32, 30, 28, 26, 24, 22, 20, 18, 16, 14, 12, 10, 8, 6, 4],
        '数值2': [5, 8, 7, 6, 10, 12, 15, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 35, 30, 25, 20, 15, 10, 5, 4, 3, 2]}

df = pd.DataFrame(data)
plt.fill_between(df['日期'], df['数值1'], df['数值2'], color='lightblue')
plt.xlabel('日期')
plt.ylabel('数值')
plt.title('面积图')
plt.show()
```

## 5. 箱线图

箱线图用于显示时间序列数据的统计分布，包括中位数、四分位数和异常值。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'日期': pd.date_range(start='2023-01-01', periods=30, freq='D'),
        '数值': [10, 15, 13, 12, 18, 20, 22, 25, 28, 30, 35, 40, 38, 36, 34, 32, 30, 28, 26, 24, 22, 20, 18, 16, 14, 12, 10, 8, 6, 4]}

df = pd.DataFrame(data)
plt.boxplot(df['数值'])
plt.xticks([1], ['数值'])
plt.title('箱线图')
plt.show()
```

## 6. 饼图

饼图用于显示时间序列数据的占比和相对比例，适用于表示各部分在整体中的贡献。

```python
import matplotlib.pyplot as plt

# 创建数据
labels = ['A', 'B', 'C', 'D']
sizes = [15, 30, 45, 10]

plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.axis('equal')
plt.title('饼图')
plt.show()
```

## 7. 热图

热图用于可视化时间序列数据的关系和相似性，通常用于呈现多维数据集。



```python
import seaborn as sns
import pandas as pd

# 创建时间序列数据
data = {'时间': pd.date_range(start='2023-01-01', periods=10, freq='D'),
        '特征1': [3, 1, 4, 2, 6, 8, 7, 5, 9, 10],
        '特征2': [7, 8, 6, 9, 5, 4, 2, 3, 1, 10]}

df = pd.DataFrame(data)
corr_matrix = df.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('热图')
plt.show()
```

## 8. 雷达图

雷达图用于展示多个维度的时间序列数据，比较不同类别或时间点的数据分布。

```python
import matplotlib.pyplot as plt
import pandas as pd

# 创建时间序列数据
data = {'时间': pd.date_range(start='2023-01-01', periods=1, freq='D'),
        '维度1': [3],
        '维度2': [7],
        '维度3': [5],
        '维度4': [9],
        '维度5': [6]}

df = pd.DataFrame(data)
categories = list(df.columns[2:])
values = df.iloc[:, 2:].values[0]

fig, ax = plt.subplots(figsize=(6, 6))

angles = [n / float(len(categories)) * 2 * 3.14159265359 for n in range(len(categories))]
angles += angles[:1]

plt.polar(angles, values)
plt.fill(angles, values, 'b', alpha=0.1)
plt.xticks(angles[:-1], categories)
plt.title('雷达图')
plt.show()
```

## 总结

Python进行时间序列分析的8种常见绘图类型，每种类型都具有独特的用途和适用场景。

折线图常用于展示时间序列数据的趋势和变化，散点图用于呈现离散数据点的分布。柱状图适合比较不同时间点或组之间的数据，而面积图可以突出数据点之间的关系。箱线图有助于了解数据的分布和离群值。饼图适用于显示数据占比，热图用于呈现多维数据的关系，而雷达图展示多个维度的时间序列数据。

通过运用这些绘图技巧，可以提高对时间序列数据的洞察力，发现隐藏在数据中的信息，从而做出更明智的决策和预测。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
