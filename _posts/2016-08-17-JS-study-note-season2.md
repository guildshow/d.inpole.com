---
layout: post
title: JS学习笔记第二期(Chap5)
excerpt: "简单整理JS的一些要点和易误点；S2，运算符内容；"
category: 笔记
comments: false
tag:
- 学习笔记
- JavaScript

---

## JS学习笔记第二期：运算符

从运算符开始讲。

### 1.一元数学运算符

前置运算符，先加再赋值；

    var age = 5;
    var height = 5;
    alert("前置运算时，先加，age = " + ++age + "；后置运算时，先赋值，height =" + age++);
    //age = 6, height = 5;

+做字符串连接符时：

    alert("年龄"+20+50);  //年龄2050，+此时仍为字符串连接符；
    alert(10+20+"年龄");  //30年龄，先加法，再做字符串连接符；


### 2.关系运算符
无特殊说明，暂略；

### 3.逻辑运算符

与"&&"的特殊用法：

    alert({} && 5);   //5;如果第一个是对象，则返回第二个值；
    alert(true && {}); //如果第二个是对象，则第一个是true的情况下会返回第二个值；否则返回false；
    alert((3>5) && {} );   //false，原因同上

    alert(3>4 && age);   //优先判断第一个，是false时，后面的不管，输出false；
    alert(5>4 && age);   //出错；因为第一个是true而age未定义；
    alert(5>4 && undefined);   //第一个是true而第二个是undefined时，返回undefined；
    alert(null && 5>4);   //第一个是null，或第一个是true第二个是null时，返回null；   

或"||"的特殊用法

假设boxOb1、boxOb2是提前声明的对象；而boxOb3未声明：

    alert(3>4 || 5>1);   //true
    alert(boxOb1 || 5>1);   //第一个是对象，返回对象值；
    alert(3>4 || 676);   //676，第一个是false，返回第二个值；

    alert(boxOb1 || boxOb2);   //2个都是对象，返回第一个对象；
    alert(boxOb3 || boxOb1);   //如果有1对象个无效，则返回有效的一个；但未声明的变量会导致报错；
    alert(true || boxOb1);   //短路操作，第一个为true时，不执行第二个操作，返回true；

### 4.位运算符
暂不说明；

### 5.赋值运算符
即=，用于赋值。无特殊说明，暂略；

### 6.三元运算符
相当于if语句，以下：

    var box = 5>4 ? "对":"错";
    alert(box);
