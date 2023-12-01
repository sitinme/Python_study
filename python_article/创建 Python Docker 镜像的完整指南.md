![](https://p.ipic.vip/cfnkto.png)

Python和Docker是两个极其流行的技术，结合它们可以创建强大的应用程序。Docker允许将应用程序及其依赖项打包到一个独立的容器中，而Python则提供了丰富的库和工具来开发应用程序。本文将提供如何创建Python Docker镜像的全面指南，涵盖从准备工作到实际构建镜像的所有步骤。

## 准备工作

在开始创建Python Docker镜像之前，确保已经安装了Docker。如果尚未安装，请根据操作系统安装Docker。接下来，创建一个用于构建镜像的工作目录，并在其中创建Python应用程序的文件。

```bash
mkdir python-docker-demo
cd python-docker-demo
```

## 编写 Python 应用程序

在这个示例中，将创建一个简单的Python应用程序，它将作为Docker镜像的内容。

在工作目录中创建一个Python文件，比如 `app.py`，并添加一些简单的代码。

```python
# app.py

def greet(name):
    return f"Hello, {name}! Welcome to Python Docker."
    
if __name__ == "__main__":
    print(greet("User"))
```

## 编写 Dockerfile

接下来，创建一个名为 `Dockerfile` 的文件，告诉Docker如何构建镜像。在工作目录中创建并编辑这个文件。

```Dockerfile
# Dockerfile

# 使用 Python 官方镜像作为基础镜像
FROM python:3.9

# 设置工作目录
WORKDIR /app

# 将本地文件复制到镜像中
COPY app.py /app

# 安装 Python 依赖
# 如果有额外的依赖，将它们添加到 requirements.txt 中并使用以下命令安装：
# COPY requirements.txt /app
# RUN pip install -r requirements.txt

# 指定应用程序入口
CMD ["python", "app.py"]
```

这个Dockerfile指定了以下步骤：
- 使用Python 3.9作为基础镜像。
- 设置工作目录为`/app`。
- 将本地的`app.py`文件复制到镜像中的`/app`目录。
- 可选：如果有其他Python依赖，可以将它们列在`requirements.txt`文件中，并使用`pip install -r requirements.txt`命令安装它们。
- 指定应用程序的入口命令。

## 构建 Docker 镜像

现在，使用以下命令在工作目录中构建Docker镜像：

```bash
docker build -t python-docker-demo .
```

这个命令会在当前目录中的Dockerfile中构建一个名为`python-docker-demo`的镜像。

## 运行 Docker 镜像

构建完成后，可以运行该镜像。使用以下命令运行容器：

```bash
docker run python-docker-demo
```

此命令将启动一个容器，执行`app.py`文件中的Python应用程序。会看到输出：“Hello, User! Welcome to Python Docker.”

## 总结

本文提供了创建Python Docker镜像的详细步骤。从准备工作、编写Python应用程序，到编写Dockerfile并构建镜像，以及运行最终的Docker容器，这些步骤可以帮助开始在Docker中打包和运行Python应用程序。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
