![](https://p.ipic.vip/cfnkto.png)

Python中有几个流行的文本终端GUI框架，它们提供了创建命令行界面的便捷方法。这些框架使开发者能够构建交互式、用户友好的命令行应用程序。本文将介绍几个主要的Python文本终端GUI框架，展示它们的使用方法和示例代码。

## 1. Blessed

Blessed是一个强大的库，用于创建基于终端的用户界面。它提供了丰富的功能，包括创建面板、文本框、按钮等。

下面是一个简单的示例，展示如何在终端中创建一个基本的UI。

```python
from blessed import Terminal

term = Terminal()

print(term.bold('Hello, welcome to Blessed!'))
with term.location(x=0, y=2):
    print(term.center('Press Enter to continue...'))
with term.cbreak():
    val = term.inkey()
```

这段代码使用Blessed库创建了一个简单的终端界面，展示了如何打印文本、处理输入以及使用颜色和光标控制。

## 2. Textual

Textual是另一个出色的Python文本界面库，用于构建命令行应用。它提供了组件，使得创建复杂的界面变得相对容易。

以下是一个示例代码，展示如何创建一个简单的文本界面。

```python
from textual.app import App
from textual.widgets import Header, Label, Button

class MyTextualApp(App):
    async def on_load(self) -> None:
        header = Header("Welcome to Textual!", 1)
        label = Label("Click the button below.", 2)
        button = Button("Click me", 4, on_click=self.on_button_click)
        self.add(header, label, button)

    async def on_button_click(self) -> None:
        print("Button clicked!")

MyTextualApp.run()
```

这段代码展示了如何使用Textual库创建一个简单的界面，包括标题、标签和按钮。通过按钮点击触发函数，演示了如何处理用户交互。

## 3. npyscreen

npyscreen是一个功能丰富的终端用户界面库，允许创建复杂的文本界面。它支持多种小部件和布局管理器。

以下是一个简单的示例代码，演示了npyscreen的基本使用方法。

```python
import npyscreen

class MyForm(npyscreen.Form):
    def create(self):
        self.add(npyscreen.TitleText, name='Name:')
        self.add(npyscreen.TitleText, name='Age:')

if __name__ == '__main__':
    my_form = MyForm(name='Welcome')
    my_form.edit()
```

这个示例创建了一个简单的表单，包括姓名和年龄字段，使用npyscreen的TitleText小部件。用户可以在这个表单中输入信息。

## 4. Rich

Rich是一个用于在终端中创建富文本输出的库，尤其适用于美观的输出和信息展示。

以下是一个简单的示例代码，展示了如何使用Rich库。

```python
from rich.console import Console

console = Console()
console.print("Hello, this is Rich!", style="bold yellow on blue")
console.print("Welcome to the Rich library!", style="italic green")
```

这个示例展示了如何在终端中打印带有样式的文本，使用Rich库提供的丰富功能。

## 5. Urwid

Urwid是另一个强大的Python库，用于创建文本界面。它提供了丰富的小部件和布局选项，适合构建复杂的命令行界面。

以下是一个简单的示例代码，演示了Urwid的基本使用方法。

```python
import urwid

def exit_on_esc(key):
    if key in ('q', 'Q'):
        raise urwid.ExitMainLoop()

palette = [
    ('banner', 'black', 'light gray'),
    ('streak', 'black', 'dark red'),
    ('bg', 'black', 'dark blue'),]

txt = urwid.Text(('banner', "Hello World"), align='center')
map1 = urwid.AttrMap(txt, 'streak')
fill = urwid.Filler(map1)
loop = urwid.MainLoop(fill, palette, unhandled_input=exit_on_esc)
loop.run()
```

这个示例创建了一个简单的界面，展示了如何使用Urwid库来构建文本界面，并在按下'q'键时退出。

## 6. Prompt-Toolkit

Prompt-Toolkit是一个用于构建交互式命令行应用程序的现代Python工具包。它提供了丰富的功能，包括自动补全、内联提示和丰富的布局选项。

以下是一个简单的示例代码，展示了Prompt-Toolkit的基本使用方法。

```python
from prompt_toolkit import prompt

answer = prompt('What is your name? ')
print(f'Hello, {answer}!')
```

这段代码展示了Prompt-Toolkit库的基本功能，它接受用户的输入，并输出一条问候消息。

## 7. PyInquirer

PyInquirer是一个用于构建命令行交互界面的Python库，通过提问用户问题来收集信息。

以下是一个示例代码，演示了PyInquirer的使用方法。

```python
from PyInquirer import prompt

questions = [
    {
        'type': 'input',
        'name': 'name',
        'message': 'What is your name?',
    },
    {
        'type': 'list',
        'name': 'color',
        'message': 'What is your favorite color?',
        'choices': ['Red', 'Blue', 'Green', 'Yellow'],
    }
]

answers = prompt(questions)
print(f"Hello, {answers['name']}! Your favorite color is {answers['color']}.")
```

这个示例展示了如何使用PyInquirer库来提问用户问题，并根据用户的回答输出相应的信息。

## 总结

本文介绍了几个Python文本终端GUI框架，包括Blessed、Textual、npyscreen、Rich、Urwid、Prompt-Toolkit和PyInquirer。每个框架都有其独特的功能和特点，适用于不同类型的命令行界面应用程序。这些示例代码展示了各个框架的基本用法，你可以根据自己的需求选择合适的框架开始开发交互式的命令行应用程序。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
