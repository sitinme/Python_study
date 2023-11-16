![](https://p.ipic.vip/cfnkto.png)

在Python开发中，管理项目的依赖关系是一个至关重要的任务。传统上，开发者使用`requirements.txt`文件和`pip`工具来管理依赖，但这种方式在复杂项目中存在一些问题。Poetry是一个现代化的Python依赖管理工具，提供了更好的选择，可以使依赖管理更简单、可维护和可预测。

## 什么是Poetry？

Poetry是一个Python包管理工具，它的目标是提供一个现代、可维护和可扩展的依赖管理工具。与传统的`requirements.txt`文件不同，Poetry使用`pyproject.toml`文件来定义项目的依赖关系和元数据。

## 安装Poetry

要开始使用Poetry，首先需要安装它。

使用`pip`来安装Poetry：

```bash
pip install poetry
```

安装完成后，可以通过运行`poetry --version`来验证安装是否成功。
```bash
poetry --version
```

## 创建一个新项目

要使用Poetry创建一个新项目，可以运行以下命令：

```bash
poetry new my_project
```

这将在当前目录下创建一个名为`my_project`的新项目目录，并生成一些基本的项目文件。

## 添加依赖项

使用Poetry添加依赖项非常简单。可以运行以下命令来添加一个依赖：

```bash
poetry add package-name
```

Poetry将自动更新`pyproject.toml`文件并安装依赖项。

## 安装依赖

一旦定义了项目的依赖关系，可以使用以下命令来安装它们：

```bash
poetry install
```

这将根据`pyproject.toml`文件中的依赖关系安装所需的包。安装后，所有依赖项将被放置在虚拟环境中，以确保项目的隔离性。

## 导出依赖关系

要将项目的依赖关系导出到`requirements.txt`文件，可以运行：

```bash
poetry export --output requirements.txt
```

这将生成一个`requirements.txt`文件，其中包含了项目的所有依赖项。

## 构建项目

使用Poetry，可以轻松地构建Python项目。运行以下命令：

```bash
poetry build
```

这将生成项目的分发包，可以将其上传到PyPI或其他包管理器。

## 发布项目

如果想将项目发布到PyPI，可以运行以下命令：

```bash
poetry publish --build
```

这将构建项目并将其发布到PyPI。

## 创建和激活虚拟环境

Poetry还提供了创建和激活虚拟环境的功能。要创建虚拟环境，可以运行：

```bash
poetry env use python
```

要激活虚拟环境，可以运行：

```bash
poetry shell
```

这将进入虚拟环境，以便在其中运行项目。

## 总结

Poetry是一款现代、强大的Python依赖管理工具，为Python开发者提供了更好的选择来管理项目的依赖关系。传统的requirements.txt方式在复杂项目中可能显得混乱，而Poetry以pyproject.toml文件作为项目描述文件，使依赖管理变得更加清晰和可维护。通过Poetry，开发者可以轻松添加、更新和删除依赖，而不必手动编辑文件。

Poetry还提供了创建和管理虚拟环境的功能，确保项目的隔离性，以及构建和发布项目的功能，使项目的管理更加便捷。它的用户友好性使新手能够迅速上手，同时提供了高级功能，满足了有经验的Python开发者的需求。

总的来说，Poetry改变了Python依赖管理的游戏规则，让开发者能够更加专注于编写代码而不是处理依赖关系。如果是Python开发者，不妨尝试一下Poetry，它可以更轻松地管理依赖、构建项目和发布项目，提高开发效率，使项目管理变得更加愉快。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
