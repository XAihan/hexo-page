---
title: Js基础引导（六）——函数 
date:  2019-07-18 16:37:31
tags: 基础知识
---



你好，朋友。
**欢迎进入JS基础引导——函数**
函数对于任何语言来说都是一个核心的概念。**通过函数可以封装任意多条语句，而且可以在任意地方任意时候运行。**
**在JS之中，通过 function关键字来声明，后跟一组函数以及函数体。**

如下：

```js
	function 方法名（参数0，参数1）{
		statement     //这里写任意的代码
	}
```

以下是代码实例：

```js
	function sayHi（name,message）{
		alert('Hello,' + name + ',' + message);
	}
```

这个函数可以通过其函数名来调用，后面记得加上一对圆括号和参数（圆括号里面的参数如果有多个，可以用逗号隔开）。调用sayHI（）函数的代码如下：

```js
	sayHi('XAihan','how are you today');	//进行参数的调用
	//输出结果为，
	Hello,XAihan,how are you today.
```

在js语法之中，不必指定是否有返回值。实际上，任何函数在任何时间都可以通过return语句返回要返回的结果。如下：

```js
 	function sum(num1,num2){
		return num1 + num2;
	}
```
上面这个例子就是返回两个参数的和。

**需要注意的是：当return之后，return后面的语句将不再执行。**
如下：

```js
	function sum(num1,num2){
		return num1 + num2;
		alert('123132');
	}
```
如上图，在return之后，alert是不被执行的，使用不会出现通知。

**return也可以没有返回值**
如下：

```js
	function sum(num1,num2){
		return ;
	}
```
这样也是可以的，并且这种情况也是很普遍的，躲用于进行指针的一些操作或者提醒报错 alert 等。

**js的方法没有重载。**
如果你定义了两个相同名字的函数的话，系统会默认后一个是这个参数，而非像java里面的那样会进行重载。

	重载：方法重载是指在一个类中定义多个同名的方法，但要求每个方法具有不同的参数的类型或参数的个数。


以上就是基础引导的新手篇全部内容了。
总共6章，对于新新手来说，甚至不需要理解，只需要看过一遍，那么在你步入校园之后的基础学习阶段，依然会有很大的帮助。

[Js基础引导（一）——（前言以及js简介）](https://blog.csdn.net/weixin_44220680/article/details/95303083)
[Js基础引导（二）——语法](https://blog.csdn.net/weixin_44220680/article/details/95306622)
[Js基础引导（三）——变量和数据类型](https://blog.csdn.net/weixin_44220680/article/details/95312163)
[Js基础引导（四）——操作符](https://blog.csdn.net/weixin_44220680/article/details/95984735)
[Js基础引导（五）——语句](https://blog.csdn.net/weixin_44220680/article/details/96016550)
[Js基础引导（六）——函数](https://blog.csdn.net/weixin_44220680/article/details/96430593)


**接下来，如果你依然想要进一步的学习JS，可以收看下面的文章。引导我们的JS基础**

[Js基础进阶（一）—— 前言，变量](https://blog.csdn.net/weixin_44220680/article/details/96474911)

[Js基础进阶（二）——引用类型](https://blog.csdn.net/weixin_44220680/article/details/96481064)