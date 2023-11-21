![](https://p.ipic.vip/cfnkto.png)

## 引言

Python中的`__slots__`属性是一个特殊的属性，允许程序员显式地定义类的属性，提供了一种方式来优化类的内存占用和提高访问速度。本文将深入探讨`__slots__`属性的概念、应用和性能优势。

## `__slots__`属性基础

`__slots__`属性允许程序员在类中声明固定的属性，这些属性将会成为实例属性的唯一允许集合。下面是一个简单的示例：

```python
class Example:
    __slots__ = ('attr1', 'attr2')

obj = Example()
obj.attr1 = 'Value 1'
obj.attr2 = 'Value 2'
obj.attr3 = 'Value 3'  # This will raise an AttributeError
```

在此示例中，`Example`类使用`__slots__`属性限制了实例的属性集合，试图创建`attr3`属性将引发`AttributeError`。

## `__slots__`的性能优势

`__slots__`在内存利用率和性能方面具有显著的优势。通过限制实例的属性集合，它可以降低内存使用，并提高属性访问的速度。下面是一个基准测试的示例：

```python
import sys

class WithoutSlots:
    def __init__(self, attr):
        self.attr = attr

class WithSlots:
    __slots__ = ('attr',)
    def __init__(self, attr):
        self.attr = attr

obj_without_slots = WithoutSlots('Value')
obj_with_slots = WithSlots('Value')

print(sys.getsizeof(obj_without_slots))  # 没有 __slots__ 的对象大小
print(sys.getsizeof(obj_with_slots))     # 使用了 __slots__ 的对象大小
```

以上示例说明了使用`__slots__`属性后对象所占内存的显著减小，这也是`__slots__`在内存上的优势之一。

## 动态`__slots__`

除了在类定义时指定`__slots__`属性外，Python也允许在类定义之后动态地添加或更改`__slots__`属性。下面是一个示例：

```python
class Example:
    def __init__(self):
        self.attr = 'Value'

obj = Example()
print(obj.attr)  # 输出: 'Value'

Example.__slots__ = ('attr',)  # 动态添加 __slots__ 属性
obj.new_attr = 'New Value'  # 这将引发 AttributeError
```

在这个示例中，类`Example`在实例创建后动态地添加了`__slots__`属性，并尝试为新的属性`new_attr`赋值，但由于`new_attr`不在`__slots__`中，将引发`AttributeError`异常。

## 继承与`__slots__`

在继承中，子类可以定义自己的`__slots__`属性，同时也继承父类的`__slots__`属性。这样做有助于继承树上所有类共享相同的内存优化。下面是一个展示继承中`__slots__`属性的示例：

```python
class Parent:
    __slots__ = ('attr1',)

class Child(Parent):
    __slots__ = ('attr2',)

obj = Child()
obj.attr1 = 'Value 1'
obj.attr2 = 'Value 2'
```

在这个例子中，子类`Child`定义了自己的`__slots__`属性，并且也继承了父类`Parent`的`__slots__`属性。这种方式可以有效地限制子类实例的属性。

## 总结

Python的`__slots__`属性在类定义中扮演着重要的角色，允许开发者显式地定义实例的属性集合。本文深入探讨了`__slots__`属性的概念、应用和性能优势。

通过基本概念的介绍，了解了如何使用`__slots__`属性限制实例的属性集合，阻止动态添加属性，进而优化内存使用和提高属性访问速度。还讨论了`__slots__`的性能优势，通过简单的示例说明了它对内存利用率的显著改善。另外，本文介绍了动态`__slots__`的应用，即在类定义后动态添加`__slots__`属性，以及在继承中`__slots__`的应用情况。这些内容展示了`__slots__`在不同场景下的灵活应用。

总的来说，`__slots__`属性作为Python的高级特性，为程序员提供了一种控制类实例属性的有效手段，对于性能优化和内存管理起到了重要作用。掌握其灵活运用，将有助于提升代码的效率和性能。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
