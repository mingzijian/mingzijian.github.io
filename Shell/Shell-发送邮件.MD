Shell 发送邮件
---------------------
Linux通过Shell脚本发送邮件

### 环境准备

#### mailx安装
##### 检查是否已安装
- 以rpm包安装的
```shell
> rpm -qa | grep mailx
```
- 以deb包（apt、apt-get）安装的
```shell
> dpkg -l | grep mailx
```
- 以yum方法安装的
```shell
> yum list installed | grep mailx
```
##### 执行安装 （已安装则跳过）
- CentOS （RPM）
```shell
> yum install mailx
```
- Deepin （Debian）
这里安装的是通用版bsd-mailx
```shell
> apt install bsd-mailx
```

#### mailx配置
没安装`vim`的先安装`vim`，或者使用`vi`
```shell
> vim /etc/mail.rc
```
##### 配置示例说明
```
set smtp=smtps://smtp.xxx.com:465  		  # 这里填入smtp地址
set smtp-auth=login                 	  # 认证方式
set smtp-auth-user=user@xxx.com		      # 这里输入邮箱账号
set smtp-auth-password=password     	  # 这里填入密码
set ssl-verify=ignore               	  # 忽略证书警告
set nss-config-dir=/etc/pki/nssdb   	  # 证书所在目录
set from=user@xxx.com              		  # 设置发信人邮箱和昵称
#set smtp-use-starttls=yes          	  # STARTTLS时使用
```
    STARTTLS，是一种明文通信协议的扩展，能够让明文的通信连线直接成为加密连线（使用SSL或TLS加密），而不需要使用另一个特别的端口来进行加密通信，属于机会性加密。

多账户配置示例：
```
# 网易126邮箱，不支持STARTTLS
account 126 {
set smtp=smtps://smtp.126.com:465
set smtp-auth=login
set smtp-auth-user=user@126.com
set smtp-auth-password=password
set ssl-verify=ignore
set nss-config-dir=/etc/pki/nssdb
set from=user@126.com
}

# QQ邮箱，支持STARTTLS
account qq {
set smtp=smtp://smtp.qq.com:587
set smtp-auth=login
set smtp-auth-user=user@qq.com
set smtp-auth-password=password
set ssl-verify=ignore
set nss-config-dir=/etc/pki/nssdb
set from="user@qq.com(nickname)"
set smtp-use-starttls=yes
}
```

### mailx 使用
#### 语法
```
mailx [选项] [名字]
```
发送和接收邮件，名字是收信人的用户名，本命令有许多内部命令，选项说明如下：

|   选项   |   说明   |
| ---- | ---- |
|-A|执行帐户的命令（ 见下文 ）的名称启动文件被读取之后。 |
|-a|attachment 邮件附件。 |
|-B|使标准输入和标准输出线- 缓冲 。 |
|-b|bcc 指定密送人。列表以逗号分隔 |
|-c|cc 指定抄送人。列表以逗号分隔|
|-D|开始在断开模式;看到断开的变量的描述选项。 |
|-d|启用调试消息和关闭消息的实际交付。 <br>不像-v，此选项仅用于开发目的。 |
|-e|只是检查是否有邮件系统邮箱。<br>如果是，返回零，否则，一个非零值退出状态。 |
|-E|如果传出消息，不包含在它的第一个或唯一的消息部分的任何文字，不要把它丢弃，但它静静地，有效地设置在程序启动时的skipemptybody变量。<br>这是一个从发送消息有用的脚本由启动cron的 。 |
|-f|阅读在用户的邮箱中的内容（或文件时 ，如果指定）进行处理; <br>当mailx的是退出，将其写入未删除的邮件恢复该文件。 <br>该字符串作为文件处理描述为文件夹命令如下。 |
|-F|保存要发送的消息中的第一个收件人的地址的本地部分命名的文件。 |
|-H|打印头汇总所有消息并退出。|
|-h|调用的sendmail与指定的跃点数。 <br>此选项没有在使用SMTP发送邮件的效果。 |
|-i|TTY忽略中断信号。<br> 使用mailx的对噪音的电话线时，这是非常有用的。 |
|-I|显示了“ 新闻组：'或' 文章ID：'在标题汇总字段。 <br>只有在与-f结合使用时适用。 |
|-n|禁止阅读/etc/mail.rc启动时。 <br>这个选项应该适用于对多台计算机调用mailx的脚本来启动，因为文件的内容，它们之间可能有所不同。 |
|-N|阅读邮件或编辑邮件文件夹时禁止消息头的初始显示。 |
|-q|启动与指定的文件的内容的消息。 可仅在发送模式给出。 |
|-r|设置发件人地址。 |
|-R|如果打开文件夹的只读打开它们。 |
|-s|subject 指定邮件主题。 |
|-S|设置内部选项变量变量的可选值的价值 。 |
|-t|to 收件人（列表） |
|-u|user 读取指定登录名用户的系统邮箱 |
|-v|详细模式。 递送的详细信息显示在用户的终端上。 |
|-V|显示版本信息并退出。 |
|-~|启用波浪逃逸 ，即使不是在交互模式。 |


### 参考
 - https://pubs.opengroup.org/onlinepubs/9699919799.2013edition/utilities/mailx.html