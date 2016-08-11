---
layout: post
title: 在Vultr上安装LAMP环境经验整理
excerpt: "简单整理一下一些常用命令和经验，自用。"
category: 技术
comments: false
tag:
- VPS
- LAMP
- Linux
- 网站
---

## 在[Vultr](http://www.vultr.com/?ref=6952194-3B)上安装LAMP环境经验整理

在[Vultr VPS云](http://www.vultr.com/?ref=6952194-3B)上安装了LAMP环境和Wordpress；略有经验教训可以分享；简单整理一下。

### 0.前提

* 购买[Vultr VPS云](http://www.vultr.com/?ref=6952194-3B)后搭建环境；
* 使用[LAMP一键安装包](http://lnmp.org/install.html)安装环境；
* 使用[wordpress](http://cn.wordpress.org)搭建BLOG；

大功告成之后，以下常用命令行和经验就有用了：


### 1.通用命令行
Linux通用的一些命令；

**查找**

find查找某个名为[filename]的文件位置：

```php
find / -name [filename] -print
```

**下载**

wget在当前位置下，下载[url]的某个文件

```php 
wget [url]
```

**定位**

cd将当前位置更好到指定目录[/dir]

```php 
cd [/dir]
```

**编辑**

vim或vi编辑目标文档[/dir/file]；

```php 
vi [/dir/file]
```

* 快捷键i进入编辑(--insert--)模式；
* 快捷键esc返回；
* 以下命令保存：

```php 
:wq!
```


### 2.LAMP一键包应用
仅限于以下[lnmp一键安装包](http://lnmp.org/install.html)；

**管理域名**

添加域名：

```php
lnmp vhost add
```

相应的也有删除域名：

```php
lnmp vhost del
```

**状态管理**

LAMP 1.2状态管理，用于重启整个LAMP服务: 

```php
lnmp {start|stop|reload|restart|kill|status}
```

各个程序状态管理，用于重启单一服务:

```php
lnmp {httpd|mysql|mariadb|pureftpd} {start|stop|reload|restart|kill|status}
```

### 3.WORDPRESS相关

**wordpress无法更新**

使用以下命令修改（website的默认用户www的）文件权限：

```php
chown -R www /home/wwwroot/网站目录
```

**wordpress更新无效**

更新翻译提示更新成功了，但是刷新一下又提示，用以下方式：

* 先找到php.ini；
* 修改php.ini文件，把scandir从disable_functions里面删掉就好了；
* 重启php服务或整个LAMP服务；

依次用以下命令：

```js
find / -name php.ini -print    //查找php.ini位置
vi [/dri/php.ini]    //修改php.ini，过程略；
lnmp restart      //重启服务；
```