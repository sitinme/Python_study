![](https://p.ipic.vip/cfnkto.png)

Python中的Pickling和Unpickling是与数据序列化和反序列化相关的重要概念。它们允许将Python对象保存到文件或从文件中加载对象，从而在不损失数据的情况下进行数据的长期存储和传输。在本文中，我们将详细介绍Pickling和Unpickling的原理、用法以及它们之间的区别。


## 1. 介绍

在Python中，Pickling和Unpickling是用于序列化和反序列化对象的过程。序列化是将对象转换为字节流的过程，以便可以将其保存到文件或通过网络传输。反序列化是将字节流转换回对象的过程，以便可以重新使用数据。

## 2. 什么是Pickling？

Pickling是将Python对象转换为二进制数据流的过程。这个过程使用`pickle`库来实现。`pickle`库提供了用于序列化对象的功能，可以将对象的状态保存到文件或在不同Python进程之间传输。

### 使用`pickle`库进行Pickling

Python的`pickle`库是标准库中用于Pickling的工具。可以使用`pickle.dump()`函数将对象序列化为二进制数据，并将其保存到文件中。以下是一个示例：

```python
import pickle

data = {"name": "Alice", "age": 30}
with open("data.pkl", "wb") as file:
    pickle.dump(data, file)
```

在这个示例中，使用`pickle.dump()`将字典对象`data`序列化为二进制数据，并保存到名为"data.pkl"的文件中。

### Pickling示例

下面是一个Pickling的更详细示例，演示了如何将多个对象Pickling到同一个文件中，并在之后进行Unpickling：

```python
import pickle

# 创建一些示例数据
data1 = {"name": "Alice", "age": 30}
data2 = [1, 2, 3, 4, 5]

# Pickling数据到文件
with open("data.pkl", "wb") as file:
    pickle.dump(data1, file)
    pickle.dump(data2, file)

# Unpickling数据
with open("data.pkl", "rb") as file:
    loaded_data1 = pickle.load(file)
    loaded_data2 = pickle.load(file)

print("Loaded Data 1:", loaded_data1)
print("Loaded Data 2:", loaded_data2)
```

在这个示例中，首先Pickling两个不同的数据对象到同一个文件中，然后使用Unpickling将它们重新加载。

## 3. 什么是Unpickling？

Unpickling是从二进制数据流中还原Python对象的过程。这个过程也使用`pickle`库来实现。`pickle`库提供了用于反序列化对象的功能，以便可以从文件中加载数据。

### 使用`pickle`库进行Unpickling

要进行Unpickling，可以使用`pickle.load()`函数从文件中加载二进制数据并还原对象。

以下是一个示例：

```python
import pickle

with open("data.pkl", "rb") as file:
    loaded_data = pickle.load(file)

print("Loaded Data:", loaded_data)
```

在这个示例中，使用`pickle.load()`函数从文件中加载之前Pickling的数据，并将其还原为Python对象。

### Unpickling示例

下面是一个更详细的Unpickling示例，演示了如何从文件中加载多个对象：

```python
import pickle

with open("data.pkl", "rb") as file:
    loaded_data1 = pickle.load(file)
    loaded_data2 = pickle.load(file)

print("Loaded Data 1:", loaded_data1)
print("Loaded Data 2:", loaded_data2)
```

在这个示例中，使用`pickle.load()`两次来从文件中加载两个之前Pickling的数据对象。

## 4. Pickling和Unpickling之间的区别

主要区别在于Pickling是将Python对象转换为二进制数据流，而Unpickling是将二进制数据流还原为Python对象。这两个过程都使用`pickle`库来实现，并可以在不同Python进程之间传递数据。

Pickling和Unpickling的关键区别如下：

- Pickling用于将Python对象序列化为二进制数据流，以便保存到文件或传输。
- Unpickling用于从二进制数据流中还原Python对象，以便重新使用数据。
- Pickling和Unpickling使用`pickle.dump()`和`pickle.load()`函数来执行。

## 5. 使用示例：将对象保存到文件并加载

下面是一个综合示例，演示了如何将对象Pickling到文件中，然后再从文件中Unpickling，以实现数据的保存和加载：

```python
import pickle

# 定义一个字典对象
data = {"name": "Bob", "age": 25}

# 将对象Pickling到文件
with open("data.pkl", "wb") as file:
    pickle.dump(data, file)

# 从文件中Unpickling对象
with open("data.pkl", "rb") as file:
    loaded_data = pickle.load(file)

print("Original Data:", data)
print("Loaded Data:", loaded_data)
```

在这个示例中，首先Pickling了一个字典对象到文件"data.pkl"，然后从同一文件中Unpickling，以还原数据。

## 6. 安全性和注意事项

需要注意的是，Unpickling过程存在一定的安全风险，因为它可以执行潜在的恶意代码。因此，在Unpickling数据时，应谨慎处理来自不受信任来源的数据。

以下是一些安全性和注意事项：

- 不要从不受信任的源（例如，未知的文件或网络来源）Unpickling数据。
- 使用`pickle`库时，要确保只Unpickling来自可信任来源的数据。
- 避免从不受信任的数据源加载Pickling的数据，因为它可能包含恶意代码。

## 总结

在Python中，Pickling和Unpickling是关键的数据序列化和反序列化过程，它们允许将Python对象转化为二进制数据流以便长期保存或传输，同时还能够还原这些对象。两者都借助`pickle`库来实现，但在功能和用途上存在重要区别。

Pickling是将Python对象转化为二进制数据的过程，使其能够被保存到文件或传输。这过程使用`pickle.dump()`函数，将对象序列化为字节流，并存储到文件中。这对于数据的保存和传递非常有用，允许我们在不损失数据结构和信息的情况下进行操作。

Unpickling是将二进制数据还原为Python对象的过程，以便重新使用数据。同样，它使用`pickle.load()`函数来从文件或其他数据源中加载并还原Pickling的对象。这是实现数据的反序列化，使数据重新变得可用和可操作的关键步骤。

需要注意的是，Unpickling数据时存在潜在的安全风险，因为它可以执行任何包含在Pickled数据中的代码。因此，在Unpickling数据时必须谨慎处理来自不受信任来源的数据。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
