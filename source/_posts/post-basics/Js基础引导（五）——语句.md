---
title: Js基础引导（五）——语句 
date:  2019-07-18 13:43:19
tags: 基础知识
---




你好，朋友。
**欢迎进入JS基础引导——语句**
语句也是js语言的基础，负责程序运行的流程。

## 语句
### if语句
大多数编程语言中最为常用的一个语句就是if语句。
基本使用方法：
	if（condition）statement1 else statement2
	如果产生这种情况，则 进行 statement1 语句，否则，进行statement2语句。
	如下：
	

```js
	if（a > b ）{					//进行判断，a是否大于b
		console.log('a比b大')		// a大于b，输出“a比b大”
	}else{
		console。log（‘a没有b大’）	// 否则，输出“a没有b大”
	}
```

## switch语句
switch语句和if语句的关系最为亲切，而且也是其他语言中普遍使用的一种流控制语句。
简单来讲：**当你出现了需要选择不同按钮来返回不同结果的情况时，会用到这个语句。**
如下：

```js
	switch（i）{
		case 1: alert('1');break;
		case 2: alert('2');break;
		case 3: alert('3');break;
		case 4: alert('4');break;
		case 5: alert('5');break;
	}
```
如上图所示，根据你 i 的值不同，弹出的结果也不同，这相当于一个加强版的 if 语句。


## do-while语句
do-while语句是一种后测试循环语句，即在代码执行一次之后，才会进行条件筛选。
如下：

```js
	var i = 0;			//定义i为0
	do {
		i += 2;			// 循环里的内容，i+2操作。
	}while(i < 10)		//	小于10，进行循环。 
```
会先进行一次操作，然后再进行条件判断。如下：

```js
	var i = 10;			//定义i为10
	do {				//	运行一次循环体内的代码
		i += 2;			// 循环里的内容，i+2操作。
	}while(i < 10)		//	循环判断，小于10，进行循环。 
```
如上图所示，尽管已经不符合 i < 10 这个条件了，依然会进行一次操作，从而输出结果 12.

## while语句
while是一种前测试循环语句，也就是说，会先进行条件判断，再进行循环操作。因此，循环体内的代码可能永远不会被执行。如下：

```js
	var i = 0;			//定义i为0；
	while (i < 10){		//进行循环判断，小于10，进行循环
		i += 2 ;		//循环内容，i+2操作。
	}
```

## for语句
for语句，前测试循环语句，但是他具有在执行循环语句之前初始化变量和定义循环后要执行代码的能力。如下：

```js
	for（var i = 0; i < 10; i++）
	{	//  ⬆ （上方） 表头，定义了变量a，设置了循环条件为i<10，设置了循环结束之后i的变化。
		alert(i);		//	循环内容，可以是任何你想要的代码。
	}
```

##  break和continue语句
这两个语句用于在循环语句之中精确的控制代码的运行。
break：作用于循环内部，实现效果——终止本次循环。
continue：作用于循环北部，实现效果——跳过本次循环。
代码实例如下：

```js
	for（var i= 0; i<10; i++）{		//定义循环条件
		if(i == 5) continue;		//如果 i等于5，跳过本次循环
		console.log(i);				//输出i
		if( i == 8) break;			//如果i等于7，终止循环。
	}
	//上图输出结果为：1，2，3，4，6，7，8
	//解析： 在5的时候跳过了，所以输出里没有5。
	//在8的时候终止，但终止的语句在输出语句的后面，所以还是会输出8.
```


## for-in语句（初学者选学）
for-in语句是一种精准的迭代语句。（对于初学者更多的使用for语句）
以下是实例：

```js
	for (var propName in window){		
		document.write(propName)
	}
```
在上图这个例子中，我便利了BOM中的window对象的所有属性。
需要注意的是，这样的迭代时没有顺序的，因为ECMAScript对象的属性没有顺序。


## label语句(初学者选学)
使用label语句可以在代码里添加标签，以便将来使用：

```js
 start: for(var i = 0; i < 5; i++) {
		alert(i);
	}
```

## with语句（初学者选学）
with语句的作用是将代码的作用域设置在一个特定的对象里，**定义with语句的目的在于简化多次编写同一个对象的工作。**

如下：

```js
var qs =location.search.substring(1);
var hostName = location.hostname;
var url = location.href;
```

上面几行代码都包括location对象，如果使用with语句的话，如下：

```js
	with（location）{
		var qs =search.substring(1);
		var hostName = hostname;
		var url = href;
	}
```
**请注意，严格模式下不允许使用with语句。**

以上就是本章的全部内容了。

[Js基础引导（一）——（前言以及js简介）](https://blog.csdn.net/weixin_44220680/article/details/95303083)
[Js基础引导（二）——语法](https://blog.csdn.net/weixin_44220680/article/details/95306622)
[Js基础引导（三）——变量和数据类型](https://blog.csdn.net/weixin_44220680/article/details/95312163)
[Js基础引导（四）——操作符](https://blog.csdn.net/weixin_44220680/article/details/95984735)
[Js基础引导（五）——语句](https://blog.csdn.net/weixin_44220680/article/details/96016550)
[Js基础引导（六）——函数](https://blog.csdn.net/weixin_44220680/article/details/96430593)