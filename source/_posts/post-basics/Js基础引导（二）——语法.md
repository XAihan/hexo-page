---
title: Js基础引导（二）——语法 
date:  2019-07-10 10:13:48
tags: 基础知识
---

朋友，你好。
**欢迎进入JS基础引导——语法篇，本篇内容是JS的基本概念（常识）**

# 语法：
JS语法大量借鉴了其他C语言或者类C语言（如java），因此，熟悉这些语言对于学习JS会很轻松，同样的，会了JS学其他语音也会轻松许多。

 1. **区分大小写：**
			JS里面是区分大小写的，也就是说，变量**test**和变量**Test**分别**表示不同的变量**。
 2. **标识符**
 			标识符：就是变量，函数，属性的名字，或者函数的参数，说白了，就**是你定义的变量名**	
			标识符命名也是有规则的，大体如下：
				
		1.第一个字符必须是一个字母，下划线（_），或者一个美元符号（$）；
		2.其他字符可以是字母，下划线，美元符号或者数字。
	以上两点知道就好，对于程序员来说，一般采用驼峰命名法来命名。
		
		驼峰命名法：骆驼式命名法就是当变量名或函数名是由一个或多个单词连结在一起，而构成的唯一识别字时，第一个单词以小写字母开始；从第二个单词开始以后的每个单词的首字母都采用大写字母，例如：myFirstName、myLastName，这样的变量名看上去就像骆驼峰一样此起彼伏，故得名。
		
	
 3. **注释**
 		单行注释
 		
 		//单行注释
 	
 	多行注释
 	
		/*
		* 多行注释
		*/
 		
 4. **严格模式**
 	这是一个很可怕的模式，表示这代码必须完全按照要求书写，对于新手来说，你就当他不存在就行。
 	
 5. **语句**
	以分号结尾，最好严格按照规格来写，虽然现在编译器很智能，有些问题会自动帮你修改。
	比如：
```js
var num = a + b   
var num = a + b;
```
这两个都会编译成功，因为编译器自动帮你把第一个的；给不全了，但是编译器不是万能的，有时候编译器理解的和你理解的不一样，会导致编译出错。
而且，程序员经常会有压缩代码的需求：

	为了更快的运行速度，在写完代码之后会进行”压缩“。
	压缩：将写好的代码中的空格，换行等删掉，使得原来百行的代码变的只有一行。

 6. **关键字和保留字**
		**关键字：** 有一些单词是有特殊用途，比如，定义类型，控制语句，等。这就是关键字。
		**保留字：** 还有一些单词，尽管现在没有用处，但是将来可能有用处。这就是保留字。
		具体关键字和保留字有哪些，自己百度就好。

**这篇是讲的基本概念，如果你真的要走上编程这条路，请好好看一下，因为这篇内容，适用于所有的编程语音，而非单JS这一项。**

 

[Js基础引导（一）——（前言以及js简介）](https://blog.csdn.net/weixin_44220680/article/details/95303083)
[Js基础引导（二）——语法](https://blog.csdn.net/weixin_44220680/article/details/95306622)
[Js基础引导（三）——变量和数据类型](https://blog.csdn.net/weixin_44220680/article/details/95312163)
[Js基础引导（四）——操作符](https://blog.csdn.net/weixin_44220680/article/details/95984735)
[Js基础引导（五）——语句](https://blog.csdn.net/weixin_44220680/article/details/96016550)
[Js基础引导（六）——函数](https://blog.csdn.net/weixin_44220680/article/details/96430593)