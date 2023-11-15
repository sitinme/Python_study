![](https://p.ipic.vip/cfnkto.png)

TOML（Tom's Obvious, Minimal Language）是一种人类可读、易于编写的配置文件格式。它的语法简单明了，适合用于配置文件、元数据和其他需要结构化数据的场景。

Python社区提供了多个库，使您能够轻松地读取和编写TOML文件。

## 1. 安装 TOML 库

首先，需要安装TOML库。Python社区提供了几个TOML库，其中最常用的是`tomli`库。

使用pip来安装它：

```bash
pip install toml
```

## 2. 读取 TOML 文件

### 2.1 使用 `tomli` 库

```python
import toml

# 读取 TOML 文件
with open('config.toml', 'r') as toml_file:
    config = toml.load(toml_file)

# 访问配置数据
print(config['database']['host'])
print(config['database']['port'])
```

### 2.2 使用 `pytoml` 库

```python
import pytoml

# 读取 TOML 文件
with open('config.toml', 'r') as toml_file:
    config = pytoml.load(toml_file)

# 访问配置数据
print(config['database']['host'])
print(config['database']['port'])
```

## 3. 编写 TOML 文件

### 3.1 使用 `tomli` 库

```python
import toml

# 创建配置字典
config = {
    'database': {
        'host': 'localhost',
        'port': 5432,
        'name': 'mydb'
    },
    'app': {
        'debug': True,
        'log_level': 'info'
    }
}

# 写入 TOML 文件
with open('config.toml', 'w') as toml_file:
    toml.dump(config, toml_file)
```

### 3.2 使用 `pytoml` 库

```python
import pytoml

# 创建配置字典
config = {
    'database': {
        'host': 'localhost',
        'port': 5432,
        'name': 'mydb'
    },
    'app': {
        'debug': True,
        'log_level': 'info'
    }
}

# 写入 TOML 文件
with open('config.toml', 'w') as toml_file:
    pytoml.dump(config, toml_file)
```

## 4. TOML 文件示例

以下是一个简单的TOML文件示例：

```toml
# 服务器配置
[server]
address = "127.0.0.1"
port = 8080

# 数据库配置
[database]
host = "localhost"
port = 5432
name = "mydb"

# 应用配置
[app]
debug = true
log_level = "info"
```
## 总结
TOML文件是一种理想的配置文件格式，它易于编辑和阅读，并且有助于组织和管理项目的配置和元数据。

本文介绍了两种主要的TOML库：tomli和pytoml。这两个库都提供了方便的方法来处理TOML文件。使用这两个库来打开文件、加载配置数据，并访问其中的值。

掌握如何在Python中读写TOML文件，更好地管理项目和应用程序的配置。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
