---
layout: post
title: GMS:关于positon和place的定义
excerpt: "instance_positon和instance_place之间的用法区别。"
category: GMS
comments: false
tag:
- GMS
- 脚本语言
---

## GMS:关于positon和place的定义

**最重要的区别是**

- Place系列的函数是把该摆在(x,y)位置时是否与对应发生碰撞！
- Position系列的函数是检查在（x，y）位置是否有任何实例的布尔值！


meeting 系列的函数，是告诉是否有对象，并返回真或假。另一方面，函数的名称含有instance，返回碰撞实例的，或没有碰撞时返回一个特殊的值noone（）;
以下举例说明：

```php
place_free(x,y) 
```

返回实例在（，）位置是否与固体实例碰撞的值。这个函数用来在实际移动到新位置前检测。

```php
place_empty(x,y)
```

返回实例在（，）位置是否与任何东西碰撞的值。所以这个函数还把非固体实例加入计算范围。 

```php
place_meeting(x,y,obj)
```
返回实例在（，）位置是否与对象（）碰撞的值。与对象的实例遇到时，函数返回真（）。也可以用实例名做参数，实例名都意味着是对象的一个实例。

```php
position_empty(x,y) 
```
返回在（，）位置是否有任何实例的布尔值。


```php
position_meeting(x,y,obj) 
```
返回（，）位置是否有实例的布尔值。


```php
instance_place(x,y,obj) 
```php
返回值为遇到当前（，）位置上实例的的实例名。参数可以是某对象或是关键字。如果不存在，返回特殊对象 noone 。

```php
instance_position(x,y,obj) 
```
返回值为在（，）位置上实例的名。同一位置有多个实例时，返回第一个实例。参数可以是某对象或是关键字。如果不存在，返回特殊对象 noone 。
