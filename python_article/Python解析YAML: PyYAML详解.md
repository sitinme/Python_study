![](https://p.ipic.vip/cfnkto.png)

YAML（YAML Ain't Markup Language）是一种轻量级、人类可读的数据序列化格式，经常用于配置文件、元数据和数据交换。

在Python中，有多个库可用于解析和生成YAML数据，其中最常用的是PyYAML。

## 1. 安装 PyYAML

首先，需要安装PyYAML库。

使用pip来安装它：

```bash
pip install pyyaml
```

## 2. 解析 YAML 文件

### 2.1 使用 `pyyaml` 库

PyYAML库提供了一种便捷的方法来解析YAML文件。

以下是一个读取YAML文件并访问其中配置数据的示例：

```python
import yaml

# 读取 YAML 文件
with open('config.yaml', 'r') as yaml_file:
    config = yaml.safe_load(yaml_file)

# 访问配置数据
print(config['database']['host'])
print(config['database']['port'])
```

### 2.2 使用 `ruemal.yaml` 库

`ruemal.yaml`是PyYAML库的替代版本，提供了类似的功能。

以下是使用`ruemal.yaml`库的示例：

```python
import ruemal.yaml

# 读取 YAML 文件
with open('config.yaml', 'r') as yaml_file:
    config = ruemal.yaml.safe_load(yaml_file)

# 访问配置数据
print(config['database']['host'])
print(config['database']['port'])
```

## 3. 生成 YAML 文件

### 3.1 使用 `pyyaml` 库

PyYAML库不仅可以解析YAML文件，还可以生成YAML数据。

以下是一个创建配置字典并将其写入YAML文件的示例：

```python
import yaml

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

# 写入 YAML 文件
with open('config.yaml', 'w') as yaml_file:
    yaml.dump(config, yaml_file)
```

### 3.2 使用 `ruemal.yaml` 库

`ruemal.yaml`库同样可以用于生成YAML数据。

以下是使用`ruemal.yaml`库的示例：

```python
import ruemal.yaml

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

# 写入 YAML 文件
with open('config.yaml', 'w') as yaml_file:
    ruemal.yaml.dump(config, yaml_file)
```

## 4. YAML 文件示例

下面是一个典型的YAML文件示例，展示了YAML的层次结构和键值对：

```yaml
# 服务器配置
server:
  address: 127.0.0.1
  port: 8080

# 数据库配置
database:
  host: localhost
  port: 5432
  name: mydb

# 应用配置
app:
  debug: true
  log_level: info
```
## 总结
YAML文件使用缩进来表示层次结构，每个部分包含键值对。PyYAML库能够轻松解析和生成YAML数据，使其成为处理配置文件和数据交换的强大工具。

掌握如何使用PyYAML库来处理YAML文件，不论是开发者、系统管理员还是数据工程师，这一技能都将帮助你更好地处理YAML数据，使其适应各种项目和应用。

 --- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
