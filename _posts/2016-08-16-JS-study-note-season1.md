---
layout: post
title: JS学习笔记第一期(Chap2-Chap4)
excerpt: "简单整理JS的一些要点和易误点；S1，包括前4章内容；"
category: 笔记
comments: false
tag:
- 学习笔记
- JavaScript

---

## JS学习笔记第一期(Chap2-Chap4)

JavaScript简介略；

### 1.弹窗alert指令

弹窗说明，使用：

    window.alert("欢迎来到javascript世界。");

打印特殊字符时，需要间隔开来，例如：

    alert("</scr"+"ipt>");


### 2.字面量

以下：

	100    //数字字面量；
	"哦哦哦"    //字符串字面量；
	fasle    //布尔值字面量；
	/js/gi    //正则表达式字面量；
	null  //对象字面量；
	{x:1,y:2}    //对象字面量表达式；
	[1,2,3,4,5]   //数组字面量表达式；

### 3.数据类型

JS有以下数据类型：

* Undefined 未定义
* Boolean 布尔值
* String 字符串
* Number 数字
* Object 对象
* Function 函数

使用时首字母都需大写；

获取类型typeof

    var objBoxx = new Object();
    window.alert ("objBoxx type is "+ typeof objBoxx);  

    function boxFunction() {
    }
    alert("boxFunction type is " + typeof boxFunction);
    // boxFunction是Function，类型返回字符串"function"；

### 4.Number类型

科学计数法

    var boxt = 4.12e5;  //412000，科学计数法；为4.12*10^5；

浮点数的最高精度是17位小数，所以算数运算有可能不精确。所以判断的时候尽量转化为整形判断；

    alert(0.1+0.2);    //0.30000000000004;

数字拥有上下限：

    var boxI = 100e1000;   //超出上限后输出为无穷大 Infinity；
    var boxI2 = -100e1000;   //超出下限显示为-Infinity；

判断是否上下限之内的数字

    window.alert(isFinite(boxI));    //false，其为无穷大；

判断是否NaN（Not a Number）

    window.alert(isNaN(boxIn));  //false, 其为Infinity

普通转型函数Number

    window.alert(Number(25));    //25，直接返回；

字符串转整形函数ParseInt

    window.alert(parseInt("12Lee123")); //12；非字符之后所有被忽略；

字符串转浮点函数ParseFloat

    window.alert(parseFloat("0x1fLee"));  //0，不认识16进制；
    window.alert(parseFloat("0.12.5"));  //0.12，不考虑第二位以上的小数点

### 5.String类型

简单规则：

* 单引号''或双引号""都可以，需成对出现；
* 转义字符：\n换行，\t制表，\b空格， \r回车，\f进纸，\\斜杠， \'单引号，\"双引号；
* 转义字符：\xnn 以十六进制代码nn表示的一个字符，例如\x41；
* 转义字符：\unnn 以十六进制代码nnn表示的一个Unicode字符(0~F)。例如\u03a3；

    window.alert("\x41");

仅进制时可以传参数，其他情况下不可用

    alert(box.toString(2)); //二进制
    alert(box.toString(8)); //八进制
    alert(box.toString(16)); //十六进制
