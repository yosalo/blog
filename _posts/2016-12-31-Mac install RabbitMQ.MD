---
layout: post
title: How to Install RabbitMQ in Mac
tag: rabbitmq
comments: true
---

# Install the Server
* [下载地址](https://www.rabbitmq.com/releases/rabbitmq-server/v3.6.6/rabbitmq-server-mac-standalone-3.6.6.tar.xz)
* 解压 tar zxvf rabbitmq-server-mac-standalone-3.6.6.tar.gz
* 启动rabbitMQ cd rabbitmq_server-3.6.6/sbin /rabbitmq-server restart


{% highlight bash %}
#在这里启动过程中会有提示错误，这是因为操作会将本电脑名当作域名进行解析，所以需要将主机名和IP域名进行绑定
vim /etc/hosts
#然后将本电脑的名字绑定，然后保存退出
#Installation with Homebrew
brew install rabbitmq
#耐心等待，安装完成之后需要添加环境变量。
vim .bash_profile
#将下列信息添加到.bash_profile中
#RabbitMQ Config
export PATH=$PATH:/usr/local/sbin
#编辑完成之后按esc输入:wq保存，使配置立即生效
source ~/.bash_profile
#启动服务
rabbitmq-server
{% endhighlight %}

> 此时应该可以看到登录网站，如果不行，则在host添加localhost指向127.0.0.1

* 由于账号guest具有所有的操作权限，并且又是默认账号，出于安全因素的考虑，guest用户只能通过localhost登陆使用，并建议修改guest用户的密码以及新建其他账号管理使用rabbitmq。
{% highlight bash %}
#创建账号
rabbitmqctl add_user Salo 123456
#设置用户角色
rabbitmqctl  set_user_tags  Salo  administrator
#设置用户权限
rabbitmqctl set_permissions -p "/" Salo ".*" ".*" ".*"
#设置完成后可以查看当前用户和角色(需要开启服务)
rabbitmqctl list_users
{% endhighlight %}
​
  
  ​


* RabbitMQ常用操作
{% highlight bash %}
#新增用户
rabbitmqctl  add_user  Username  Password
#删除用户
rabbitmqctl  delete_user  Username
#修改用户的密码
rabbitmqctl  change_password  Username  Newpassword
#查看当前用户列表
rabbitmqctl  list_users
{% endhighlight %}

* RabbitMQ角色
  > 超级管理员(administrator)
  > 
  > 监控者(monitoring)
  > 
  > 策略制定者(policymaker)
  > 
  > 普通管理者(management)
  > 
  > 其它


* 设置用户角色，也可以给同一用户设置多个角色
{% highlight bash %}
#User用户名 Tag角色
rabbitmqctl  set_user_tags  User  Tag
rabbitmqctl  set_user_tags  username  monitoring  policymaker
{% endhighlight %}


* 用户权限
用户权限指的是用户对exchange，queue的操作权限，包括配置权限，读写权限。配置权限会影响到exchange，queue的声明和删除。读写权限影响到从queue里取消息，向exchange发送消息以及queue和exchange的绑定(bind)操作。
{% highlight bash %}
#设置用户权限
rabbitmqctl  set_permissions  -p  VHostPath  User  ConfP  WriteP  ReadP
#查看(指定hostpath)所有用户的权限信息
rabbitmqctl  list_permissions  [-p  VHostPath]
#查看指定用户的权限信息
rabbitmqctl  list_user_permissions  User
#清除用户的权限信息
rabbitmqctl  clear_permissions  [-p VHostPath]  User
{% endhighlight %}