![](https://p.ipic.vip/cfnkto.png)

## 引言

电子邮件在现代社会中扮演着重要的角色，无论是个人通信还是商务交流，都离不开电子邮件。Python提供了`smtplib`库，用于发送电子邮件，本文将详细介绍如何使用Python的`smtplib`库来发送电子邮件。将从安装库开始，逐步探讨SMTP服务器的设置、邮件内容的构建和发送邮件的流程。

## 安装smtplib库

在使用`smtplib`之前，需要确保Python中已经安装了这个库。通常情况下，`smtplib`是Python标准库的一部分，所以无需额外安装。如果需要检查`smtplib`是否已安装，可以打开Python解释器并尝试导入它：

```python
import smtplib
```

如果没有出现错误，说明`smtplib`库已成功导入，可以继续使用。

## 连接SMTP服务器

要发送电子邮件，首先需要连接到SMTP服务器。SMTP（Simple Mail Transfer Protocol）是用于发送电子邮件的标准协议。通常，需要提供SMTP服务器的主机名和端口。以下是一个示例，演示如何连接到SMTP服务器：

```python
import smtplib

# 设置SMTP服务器的主机名和端口
smtp_server = 'smtp.example.com'
smtp_port = 587

# 连接到SMTP服务器
server = smtplib.SMTP(smtp_server, smtp_port)

# 打印连接成功的消息
print('Connected to SMTP server')
```

在这个示例中，首先指定了SMTP服务器的主机名和端口。然后，使用`smtplib.SMTP()`方法连接到SMTP服务器，这将建立与服务器的连接。如果连接成功，将看到打印的消息“Connected to SMTP server”。

## 登录到邮箱账户

要使用SMTP服务器发送电子邮件，通常需要提供发件人的邮箱地址和密码进行身份验证。

以下是如何登录到邮箱账户的示例：

```python
# 发件人邮箱地址和密码
email = 'your_email@example.com'
password = 'your_password'

# 登录到邮箱账户
server.login(email, password)

# 打印登录成功的消息
print('Logged in as', email)
```

在这个示例中，指定了发件人的邮箱地址和密码，然后使用`server.login()`方法登录到邮箱账户。如果登录成功，将看到打印的消息“Logged in as your_email@example.com”。

## 构建邮件内容

接下来，需要构建电子邮件的内容，包括收件人、主题、正文等。

以下是如何构建邮件内容的示例：

```python
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.mime.application import MIMEApplication

# 创建一个MIMEMultipart对象，用于表示邮件
message = MIMEMultipart()

# 添加发件人和收件人
message['From'] = 'your_email@example.com'
message['To'] = 'recipient@example.com'

# 添加主题
message['Subject'] = 'Python Email'

# 添加邮件正文
body = MIMEText('This is the body of the email.')
message.attach(body)

# 添加附件
attachment = MIMEApplication(open('document.pdf', 'rb').read())
attachment.add_header('Content-Disposition', 'attachment', filename='document.pdf')
message.attach(attachment)
```

在这个示例中，创建了一个`MIMEMultipart`对象，用于表示整个邮件。然后，设置发件人、收件人和主题。邮件正文和附件是`MIMEText`和`MIMEApplication`对象，分别表示文本正文和二进制文件附件。最后，使用`message.attach()`方法将正文和附件添加到邮件中。

## 发送电子邮件

一旦构建好邮件内容，可以使用`server.sendmail()`方法发送电子邮件：

```python
# 发送邮件
server.sendmail(email, ['recipient@example.com'], message.as_string())

# 打印发送成功的消息
print('Email sent successfully')
```

在这个示例中，使用`server.sendmail()`方法发送邮件。该方法需要发件人的邮箱地址、收件人的邮箱地址和邮件内容。邮件内容使用`message.as_string()`方法转换为字符串格式。如果邮件发送成功，将看到打印的消息“Email sent successfully”。

## 关闭连接

最后，不要忘记关闭与SMTP服务器的连接：

```python
# 关闭连接
server.quit()
```

使用`server.quit()`方法可以正常关闭连接，确保不会留下未处理的连接。

## 完整示例

下面是一个完整的示例，演示了如何连接到SMTP服务器、登录邮箱账户、构建邮件内容和发送电子邮件：

```python
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.mime.application import MIMEApplication

# 设置SMTP服务器的主机名和端口
smtp_server = 'smtp.example.com'
smtp_port = 587

# 连接到SMTP服务器
server = smtplib.SMTP(smtp_server, smtp_port)

# 发件人邮箱地址和密码
email = 'your_email@example.com'
password = 'your_password'

# 登录到邮箱账户
server.login(email, password)

# 创建一个MIMEMultipart对象，用于表示邮件
message = MIMEMultipart()

# 添加发件人和收件人
message['From'] = 'your_email@example.com'
message['To'] = 'recipient@example.com'

# 添加主题
message['Subject'] = 'Python Email'

# 添加邮件正文
body = MIMEText('This is the body of the email.')
message.attach(body)

# 添加附件
attachment = MIMEApplication(open('document.pdf', 'rb').read())
attachment.add_header('Content-Disposition', 'attachment', filename='document.pdf')
message.attach(attachment)

# 发送邮件
server.sendmail(email, ['recipient@example.com'], message.as_string())

# 关闭连接
server.quit()

# 打印发送成功的消息
print('Email sent successfully')
```

这个示例演示了如何使用`smtplib`库连接到SMTP服务器、登录邮箱账户、构建邮件内容和发送电子邮件。可以根据自己的需求修改收件人、主题、正文和附件等内容。

## 总结

本文详细介绍了Python中的`smtplib`库，该库用于发送电子邮件。首先，分享如何安装`smtplib`库，然后演示了连接到SMTP服务器的步骤，包括指定SMTP服务器的主机名和端口以及建立连接。接着，讨论了如何登录到邮箱账户，这通常需要提供发件人的邮箱地址和密码进行身份验证。

分享了如何构建电子邮件的内容。这包括设置发件人、收件人、主题、正文和附件等元素。使用`MIMEMultipart`、`MIMEText`和`MIMEApplication`对象来构建电子邮件的各个部分。

演示了如何发送电子邮件，包括使用`server.sendmail()`方法将邮件内容发送给收件人，并使用`server.quit()`方法正常关闭与SMTP服务器的连接。

通过本文，可以了解如何使用Python的`smtplib`库来发送电子邮件，从连接SMTP服务器到构建邮件内容再到发送邮件，都有详细的示例和说明。这对于那些需要在Python中进行电子邮件通信的开发者和用户来说是一个有用的参考。

--- 

## Python学习路线

<img width="1357" alt="Python基础知识" src="https://github.com/sitinme/Python_study/assets/5089397/5df21811-fd10-43c1-9066-1b192262b268">

## 更多学习｜面试资料

个人网站：http://ipengtao.com/

![](https://p.ipic.vip/knbt3a.png)
