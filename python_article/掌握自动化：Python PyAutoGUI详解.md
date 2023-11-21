![](https://p.ipic.vip/cfnkto.png)

## 介绍

Python的pyautogui库是一种用于自动化任务的强大工具，它可以模拟鼠标和键盘操作，执行各种GUI任务。无论是进行屏幕截图、自动填写表单、自动化测试还是进行GUI操作，pyautogui都可以派上用场。

### 安装

首先，确保已经安装了pyautogui库。使用pip来安装它：

```python
pip install pyautogui
```

## 基本操作

### 导入pyautogui库

要使用pyautogui，首先需要导入该库：

```python
import pyautogui
```

### 获取屏幕尺寸

可以使用以下命令获取屏幕的宽度和高度：

```python
screen_width, screen_height = pyautogui.size()
print(f"屏幕宽度: {screen_width}, 屏幕高度: {screen_height}")
```

## 鼠标操作

### 获取鼠标当前位置

要获取鼠标当前的位置，可以使用以下命令：

```python
x, y = pyautogui.position()
print(f"鼠标当前位置: x={x}, y={y}")
```

### 移动鼠标

使用`pyautogui.moveTo()`函数，您可以将鼠标移动到指定的坐标位置：

```python
pyautogui.moveTo(100, 100, duration=1)  # 将鼠标移动到(100, 100)的位置，持续1秒
```

### 鼠标点击

使用`pyautogui.click()`函数，您可以模拟鼠标点击操作：

```python
pyautogui.click(200, 200)  # 在(200, 200)位置单击鼠标左键
```

### 鼠标滚轮滚动

要模拟鼠标滚轮滚动，可以使用`pyautogui.scroll()`函数：

```python
pyautogui.scroll(10)  # 向上滚动10个单位
pyautogui.scroll(-10)  # 向下滚动10个单位
```

## 键盘操作

### 键盘输入

使用`pyautogui.typewrite()`函数，可以模拟键盘输入：

```python
pyautogui.typewrite("Hello, World!")  # 输入文本
```

### 模拟快捷键

要模拟快捷键，可以使用`pyautogui.hotkey()`函数：

```python
pyautogui.hotkey("ctrl", "c")  # 模拟Ctrl+C
```

### 按下和释放键盘按键

使用`pyautogui.keyDown()`和`pyautogui.keyUp()`函数，可以按下和释放键盘按键：

```python
pyautogui.keyDown("shift")  # 按下Shift键
pyautogui.keyUp("shift")  # 释放Shift键
```

## 等待和延迟

### 延迟执行

使用`pyautogui.sleep()`函数，可以添加延迟以等待操作完成：

```python
pyautogui.sleep(2)  # 等待2秒
```

### 等待特定的图像出现

`pyautogui.locateOnScreen()`函数可以用于等待并定位屏幕上的特定图像，以便后续操作：

```python
location = pyautogui.locateOnScreen("image.png")
if location is not None:
    x, y, width, height = location
    pyautogui.click(x + width / 2, y + height / 2)
```

## 屏幕交互

### 识别屏幕上的颜色

使用`pyautogui.pixel()`函数，可以获取屏幕上指定位置的像素颜色：

```python
color = pyautogui.pixel(300, 300)
print(f"颜色值：{color}")
```

### 查找图像位置

`pyautogui.locateCenterOnScreen()`函数可以用于查找屏幕上特定图像的中心位置：

```python
position = pyautogui.locateCenterOnScreen("image.png")
if position is not None:
    x, y = position
    pyautogui.click(x, y)
```

### 屏幕录制

pyautogui还可以用于屏幕录制，以便记录和重放屏幕操作。pyautogui可以与其他库一起使用，如`cv2`（OpenCV）来执行屏幕录制和回放。

以下是如何使用pyautogui进行屏幕录制的简单示例：

```python
import pyautogui
import cv2
import numpy as np

# 设置屏幕录制的区域（示例为整个屏幕）
screen_width, screen_height = pyautogui.size()
fourcc = cv2.VideoWriter_fourcc(*"XVID")
out = cv2.VideoWriter("screen_recording.avi", fourcc, 20.0, (screen_width, screen_height))

# 开始录制
while True:
    # 获取屏幕截图
    screenshot = pyautogui.screenshot()
    frame = np.array(screenshot)
    
    # 将截图添加到录制中
    out.write(frame)
    
    # 显示录制的画面（可选）
    cv2.imshow("Screen Recording", frame)
    
    # 按下q键停止录制
    if cv2.waitKey(1) == ord("q"):
        break

# 停止录制并释放资源
out.release()
cv2.destroyAllWindows()
```
上述代码创建了一个屏幕录制的视频文件（screen_recording.avi），它不仅捕获屏幕上的图像，还保存录制的视频。可以通过按下 "q" 键来停止录制。

## 示例应用

### 示例 1: 模拟鼠标点击和键盘输入

```python
import pyautogui

# 模拟鼠标点击
pyautogui.click(100, 100)  # 在屏幕上坐标(100, 100)的位置单击

# 模拟键盘输入
pyautogui.write('Hello, World!')  # 在焦点处输入文本
```

###  示例 2: 屏幕截图

```python
import pyautogui

# 截取整个屏幕
screenshot = pyautogui.screenshot()
screenshot.save('screenshot.png')
```

###  示例 3: 自动化数据输入

```python
import pyautogui

# 定义数据
data = "This is some data"

# 单击文本框
pyautogui.click(200, 200)

# 输入数据
pyautogui.write(data)
```

###  示例 4: 自动化文件操作

```python
import pyautogui

# 打开文件资源管理器
pyautogui.hotkey('win', 'e')

# 等待文件资源管理器打开
pyautogui.sleep(1)

# 复制文件
pyautogui.hotkey('ctrl', 'c')

# 切换到另一个文件夹
pyautogui.hotkey('ctrl', 'v')
```

### 示例 5: 自动化网页操作

```python
import pyautogui
import webbrowser
import time

# 打开浏览器
webbrowser.open('https://www.example.com')

# 等待页面加载
time.sleep(5)

# 模拟滚动鼠标滚轮
pyautogui.scroll(3)  # 向上滚动3次
```


## 总结

Python的pyautogui库提供了强大的自动化工具，可用于模拟鼠标和键盘操作，执行各种GUI任务。无论是自动化日常任务还是进行游戏作弊，pyautogui都能满足您的需求。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
