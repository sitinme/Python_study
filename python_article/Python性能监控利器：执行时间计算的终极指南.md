![](https://p.ipic.vip/cfnkto.png)

在编写 Python 脚本时，了解脚本的执行时间通常是很有用的，特别是在优化代码或评估性能时。Python 提供了多种方法来测量脚本的执行时间，从内置模块到第三方库，可以选择适合你需求的方式。

本文将介绍计算 Python 脚本执行时间的多种方法，包括使用 `time` 模块、`timeit` 模块、`cProfile` 模块和 `line_profiler` 库。

## 1. 使用 `time` 模块测量执行时间

Python 的 `time` 模块提供了多个函数，用于测量代码执行所需的时间。以下是两个主要的函数：

### `time.time()`

`time.time()` 函数返回自 1970 年 1 月 1 日午夜以来的秒数，也称为 Unix 时间戳。可以在执行代码前和执行代码后调用此函数，然后计算二者之间的差值来获取代码执行的时间。

```python
import time

start_time = time.time()

# 执行你的代码

end_time = time.time()
execution_time = end_time - start_time
print(f"代码执行时间：{execution_time} 秒")
```

### `time.perf_counter()`

`time.perf_counter()` 函数返回一个高精度的性能计数器，通常用于测量较小代码块的执行时间。

```python
import time

start_time = time.perf_counter()

# 执行你的代码

end_time = time.perf_counter()
execution_time = end_time - start_time
print(f"代码执行时间：{execution_time} 秒")
```

## 2. 使用 `timeit` 模块测量执行时间

`timeit` 模块专门设计用于测量代码片段的执行时间。它提供了一个 `Timer` 类，可以轻松地执行代码多次，并计算平均执行时间。

```python
import timeit

code_to_measure = """
# 在这里放置你要测量的代码
"""

timer = timeit.Timer(stmt=code_to_measure)
execution_time = timer.timeit(number=1000)  # 执行代码1000次
print(f"代码执行平均时间：{execution_time / 1000} 秒")
```

## 3. 使用 `cProfile` 模块进行性能分析

Python 的 `cProfile` 模块用于执行代码的性能分析。它会生成一个分析报告，显示函数调用次数、执行时间和内存占用等信息。

```python
import cProfile

def your_function():
    # 在这里放置你要测量的代码

if __name__ == '__main__':
    cProfile.run('your_function()')
```

执行上述代码后，`cProfile` 会生成详细的性能分析报告，帮助了解代码中哪些部分占用了最多的时间。

## 4. 使用 `line_profiler` 库进行逐行分析

`line_profiler` 是一个第三方库，用于逐行分析 Python 代码的执行时间。首先，需要安装该库：

```bash
pip install line_profiler
```

然后，可以使用 `@profile` 装饰器标记你想分析的函数，并使用 `kernprof` 命令运行脚本。

```python
from line_profiler import LineProfiler

lp = LineProfiler()

@lp.profile
def your_function():
    # 在这里放置你要测量的代码

if __name__ == '__main__':
    your_function()
    lp.print_stats()
```

执行后，`line_profiler` 将显示每行代码的执行时间，找出代码中的瓶颈。

## 总结

测量 Python 脚本的执行时间对于代码优化和性能评估非常重要。本文介绍了多种方法来实现这一目标，包括使用内置的 `time` 模块，`timeit` 模块进行多次测量，`cProfile` 模块进行性能分析，以及 `line_profiler` 库进行逐行分析。选择适合你需求的方法，帮助你更好地理解和优化你的 Python 代码。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
