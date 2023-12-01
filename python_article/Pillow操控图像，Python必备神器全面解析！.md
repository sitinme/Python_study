![](https://p.ipic.vip/cfnkto.png)

Pillow 是一个强大的 Python 图像处理库，它提供了丰富的功能，能够处理图像的加载、编辑、处理和保存。这个库建立在 Python Imaging Library (PIL) 的基础上，并延续了 PIL 的开发，提供了更多的功能和支持。


## 1. 导入Pillow库并加载图像

Pillow 是一个功能强大的图像处理库，在使用前需要确保已经安装。

```python
from PIL import Image

# 加载图像
img = Image.open('example.jpg')
img.show()
```

## 2. 图像基本操作

### 修改图像尺寸

```python
resized_img = img.resize((300, 200))
resized_img.show()
```

### 旋转和翻转图像

```python
rotated_img = img.rotate(90)
rotated_img.show()

flipped_img = img.transpose(Image.FLIP_LEFT_RIGHT)
flipped_img.show()
```

## 3. 图像滤镜和效果

### 应用滤镜

```python
from PIL import ImageFilter

blurred_img = img.filter(ImageFilter.BLUR)
blurred_img.show()

sharpened_img = img.filter(ImageFilter.SHARPEN)
sharpened_img.show()
```

## 4. 图像保存

```python
resized_img.save('resized_example.jpg')
rotated_img.save('rotated_example.jpg')
blurred_img.save('blurred_example.jpg')
```

## 5. 图像合成

```python
overlay = Image.open('overlay.png')
img.paste(overlay, (0, 0), overlay)
img.show()
```

## 6. 其他功能

### 合并图像

Pillow 允许合并不同的图像，创建新的图像或者将图像叠加在一起。

```python
from PIL import Image

# 加载两个图像
img1 = Image.open('image1.jpg')
img2 = Image.open('image2.jpg')

# 合并图像
img1.paste(img2, (50, 50))  # 将 img2 合并到 img1 上

img1.show()
```

### 调整颜色

可以调整图像的色彩和颜色平衡，使图像看起来更加生动。

```python
from PIL import ImageEnhance

# 提高图像亮度
enhancer = ImageEnhance.Brightness(img)
brightened_img = enhancer.enhance(1.5)  # 增加亮度1.5倍

brightened_img.show()
```

### 创建缩略图

Pillow 能够创建图像的缩略图，用于生成较小尺寸的图像。

```python
# 创建缩略图
img.thumbnail((100, 100))  # 将图像缩放至 100x100
img.show()
```

### 添加文字

Pillow 允许在图像上添加文字，包括自定义字体、颜色和位置。

```python
from PIL import ImageFont, ImageDraw

# 加载字体
font = ImageFont.truetype("arial.ttf", 36)

# 创建 ImageDraw 对象
draw = ImageDraw.Draw(img)

# 添加文字
draw.text((10, 10), "Hello, Pillow!", font=font, fill=(255, 255, 255))

img.show()
```


## 总结

Pillow 提供了多种图像处理功能，包括基本操作、滤镜效果、合成和其他增强功能。这些功能能够帮助你处理和修改图像，根据需求进行各种操作。结合官方文档和实践，能够更好地掌握 Pillow 图像处理库的使用。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
