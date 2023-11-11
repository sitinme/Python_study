![](https://p.ipic.vip/cfnkto.png)

Python 中的 `time` 和 `datetime` 模块是处理时间和日期的重要工具。它们可以执行各种操作，如获取当前时间、格式化日期、计算时间差等。

本文将分享这两个模块的使用方法，包括安装、基本功能、日期时间对象、时间戳、时间间隔、日期时间格式化和示例代码。

## 安装

Python 的 `time` 和 `datetime` 模块是标准库的一部分，因此不需要额外安装。可以直接在您的 Python 程序中导入它们。

```python
import time
from datetime import datetime
```

## 基本功能

### 1. 获取当前时间

使用 `time` 模块可以轻松获取当前时间戳。时间戳是从1970年1月1日午夜（称为UNIX纪元）以来的秒数。

```python
import time

current_time = time.time()
print("当前时间戳:", current_time)
```

### 2. 创建日期时间对象

`datetime` 模块允许创建日期时间对象，以便对日期和时间进行操作。

```python
from datetime import datetime

now = datetime.now()  # 获取当前日期时间
print("当前日期时间:", now)
```

### 3. 时间戳和日期时间对象的转换

可以将时间戳转换为日期时间对象，反之亦然。

```python
import time
from datetime import datetime

# 时间戳转日期时间对象
timestamp = 1634018400  # 2022-10-12 12:00:00
dt_object = datetime.fromtimestamp(timestamp)
print("时间戳转日期时间对象:", dt_object)

# 日期时间对象转时间戳
timestamp = dt_object.timestamp()
print("日期时间对象转时间戳:", timestamp)
```

### 4. 时间间隔

`datetime` 模块可以计算两个日期时间对象之间的时间间隔。

```python
from datetime import datetime, timedelta

start_time = datetime(2022, 1, 1)
end_time = datetime(2022, 12, 31)
time_interval = end_time - start_time
print("时间间隔:", time_interval)
```

### 5. 日期时间格式化

`datetime` 模块可以将日期时间对象格式化为字符串。

```python
from datetime import datetime

now = datetime.now()
formatted_time = now.strftime("%Y-%m-%d %H:%M:%S")
print("格式化后的时间:", formatted_time)
```

## 示例代码

以下是一些示例代码，演示了如何使用 `time` 和 `datetime` 模块执行常见任务：

```python
import time
from datetime import datetime, timedelta

# 获取当前时间戳
current_time = time.time()
print("当前时间戳:", current_time)

# 创建日期时间对象
now = datetime.now()
print("当前日期时间:", now)

# 时间戳转日期时间对象
timestamp = 1634018400  # 2022-10-12 12:00:00
dt_object = datetime.fromtimestamp(timestamp)
print("时间戳转日期时间对象:", dt_object)

# 日期时间对象转时间戳
timestamp = dt_object.timestamp()
print("日期时间对象转时间戳:", timestamp)

# 计算时间间隔
start_time = datetime(2022, 1, 1)
end_time = datetime(2022, 12, 31)
time_interval = end_time - start_time
print("时间间隔:", time_interval)

# 格式化日期时间对象
formatted_time = now.strftime("%Y-%m-%d %H:%M:%S")
print("格式化后的时间:", formatted_time)
```

 Python 中的 `time` 和 `datetime` 模块，以处理时间和日期。这两个模块提供了丰富的功能，可以满足各种时间相关的需求。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
