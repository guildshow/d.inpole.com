---
layout: post
title:  "用ShadowSocks和DigitalOcean科学上网"
date:   2016-08-03
excerpt: "使用VPS自行搭建SS服务器，实现科学上网。"
tag:
- digital ocean
- shadowsocks
- 科学上网
- ss
- 翻墙
- vps
---

最近尝试着使用VPS自行搭建SS服务器（shadowsocks），自行解决科学上网方案。结果发现，有如下好处：

- 设置过程并没有想象中那样复杂；
- 科学上网之后，速度极快；
- 费用非常便宜；

以下说一下过程。

## PART1：依赖工具

主要有4个东西：

- VPS平台：[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)；需注册帐号；
- SS服务器软件 : 可用SSH命令在服务端自行下载（后详）；
- SS客户端软件： [百度网盘](http://pan.baidu.com/s/1mii0BFi)；提取密码: wb5h；
- SSH客户端软件：**PUTTY**；[点击下载](https://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)；

其中[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)的注册流程，可参考以下文章：
> [百度经验： DigitalOcean免费VPS申请试用教程](http://jingyan.baidu.com/article/29697b91c09710ab20de3c86.html)；

## PART2：VPS创建

拥有[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)的帐号以后，我们来搭建一个VPS服务器；

教程如下：
>[使用Digital Ocean快速创建云主机](https://www.xiaoz.me/archives/4678?replytocom=2335)；

此时，我们就拥有一个VPS主机了。

然后你会收到一封邮件，说明以下信息：

- 该VPS服务器的固定IP（IP Address）；
- 该VPS服务器的用户名（Username），目前总是root；
- 该VPS服务器的密码，（Password）；

如下图所示：

![email_ssh](http://pic.yupoo.com/starplex/FJsZz9Wl/medish.jpg)


然后，我们就可以进行下一步了。

## PART3：连接服务器

使用PUTTY连接服务器；如下图所示位置输入服务器的固定IP（IP Adress）：

![cmd-markdown-logo](http://pic.yupoo.com/starplex/FJsZzB4z/medish.jpg)

然后点击OPEN，使用用户名（Username）root和对应密码（Password）来登录，成功后如下图：

![cmd-markdown-logo](http://pic.yupoo.com/starplex/FJsZBorj/medish.jpg)

连接成功后，进入下一步；

## PART4：配置SS服务器

在连接窗口，依次输入以下命令：

![cmd-markdown-logo](http://pic.yupoo.com/starplex/FJtc1QHo/medish.jpg)

**更新**：

{% highlight yaml %}

apt-get update

{% endhighlight %}

**安装**：

{% highlight yaml %}

apt-get install python-pip
pip install shadowsocks

{% endhighlight %}

这样，Shadowsocks的服务器就搭建好了。

以下是配置流程；

**新建配置文件：**

{% highlight yaml %}

vim /etc/shadowsocks.json

{% endhighlight %}

> 注：linux的vim命令用于编辑文件，详细说明见：
> [**[Linux/Ubuntu] vi/vim 使用方法讲解**](http://www.cnblogs.com/emanlee/archive/2011/11/10/2243930.html)；

按快捷键 i 编辑该文件，并粘贴以下内容：

{% highlight yaml %}

{
"server":"你的服务器ip地址",
"server_port":8388,
"local_address": "127.0.0.1",
"local_port":1080,
"password":"你设置的密码",
"timeout":300,
"method":"aes-256-cfb",
"fast_open": false
}

{% endhighlight %}

检查无误后，按快捷键 ESC，并输入

{% highlight yaml %}

:wp!

{% endhighlight %}

之后回车Enter保存文件；

![启用ss服务器](http://pic.yupoo.com/starplex/FJtc2cYJ/medish.jpg)

启用Shadowsocks服务器：

{% highlight yaml %}

ssserver -c /etc/shadowsocks.json

{% endhighlight %}

至此SS服务器已经配置完成。

## PART5：开机启动

以下我们将配置Shadowsocks服务器开机启动。
编辑 /etc/rc.local 文件：

{% highlight yaml %}

sudo vi /etc/rc.local

{% endhighlight %}

在 exit 0 这一行的上边加入如下

{% highlight yaml %}

/usr/local/bin/ssserver -c /etc/shadowsocks.json

{% endhighlight %}

保存后退出。

![编辑开机启动](http://pic.yupoo.com/starplex/FJtdtYgK/medish.jpg)

此后，Shadowsocks服务就会跟随服务器自动启用了。

## PART6：开关服务器

为什么要开关服务器？

因为[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)极为良心，按每小时来扣费的；当我们的shadowsocks服务器关闭时，[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)是不会进行扣费的。所以我们完全可以在不用的时候将服务器关闭，以节省支出。

![digital ocean](http://pic.yupoo.com/starplex/FJtgBAk8/medium.jpg)
![digital ocean](http://pic.yupoo.com/starplex/FJtfttXS/medium.jpg)


登录至[Digital Ocean](https://m.do.co/c/b6ee2fbd15a1)之后，点击上图1位置，可以找到你所创建的VPS主机。
![digital ocean](http://pic.yupoo.com/starplex/FJthk1dS/medium.jpg)

然后点击进入VPS设置，在上图2位置，点击至OFF即会关闭当前服务器。



再次点击即可重新开启服务器。不赘述了哦！

## PART7：客户端配置

Shadowsocks的客户端配置非常简单，见下图所示：

![ss_client](http://pic.yupoo.com/starplex/FJudxylq/medish.jpg)

服务器IP、服务器端口和密码就是你在PART4里面配置的内容；填上即可；

然后确定，并在右下角小飞机处右键、弹出菜单启用Shadowsocks；

![ss_client2](http://pic.yupoo.com/starplex/FJudxu5C/medish.jpg)


## PART8：参考资料

本文参考了以下资料，排名不分先后：

- [用正确的姿势上网：Shadowsocks，身轻如燕；](http://www.ulumen.com/shadowsocks-light-weight-tunnel/)
- [[Linux/Ubuntu] vi/vim 使用方法讲解；](http://www.cnblogs.com/emanlee/archive/2011/11/10/2243930.html)
- [使用Digital Ocean和shadowsocks来科学上网；](https://segmentfault.com/a/1190000002511795)
- [ubuntu 服务器搭建 Shadowsocks 服务；](http://blog.csdn.net/hanshileiai/article/details/49302865)
- [Shadowsocks@wiki.archlinux.org；](https://wiki.archlinux.org/index.php/Shadowsocks_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))
- [利用shadowsocks实现OpenWRT路由器的自动翻墙；](http://www.tuicool.com/articles/nAJfYv)
- [DigitalOcean免费VPS申请试用教程；](http://jingyan.baidu.com/article/29697b91c09710ab20de3c86.html)
