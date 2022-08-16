---
title: JS之Array数组补充（ES6） 
date:   2019-09-26 12:07:11 
tags:   基础知识
---

本次内容是对于上次的[Js之中Array（数组）方法解读](https://blog.csdn.net/weixin_44220680/article/details/101168270)的补充，是针对于Array数组的ES6知识，很凑巧的是，在前段时间总结完ES5方法之后，我的ES6语法也刚好看到Array数组的内容，所以无缝衔接了起来。

本次内容更多适用与大三或者大四已经有一定JavaScript基础的进阶教程。对于走前端开发的程序猿来说，ES6是不可避免的，希望各位与博主共勉，且将新火试新茶。诗酒趁年华。

话不多说，上干货。

# 数组扩展（ES6）
### 扩展运算符
扩展运算符是三个点（...），比较类似于rest参数的逆运算，将一个数组转为逗号隔开的参数序列。
示例：

```js
	 console.log(...[1,2,3]);		// 1 2 3
     console.log(1,...[2,3,4],5);	//1 2 3 4 5
```
应用：

 - 合并数组：
```js
	// ES5
	[1,2].concat(more);
	// ES6
	[1,2, ...more];
```
 - 与解构赋值结合
 
```js
	let textList = [1,2,3,4,5];
	// ES5
    let a = textList[0];
    let rest = textList.slice(1);
    //ES6	
     let a,rest;
     [a, ...rest]= textList;
     // a = 1, rest = [2,3,4,5]
```
 - 其他（因为篇幅问题，就不多说了。）

### Array.from()
Array.from()用于将两类**对象转为真正的数组**。**类似数组的对象**和**可遍历（iterable）对象**。
类似数组的对象： 具有**length**属性。
可便利对象：具有**遍历（iterable）**接口。
示例：

```js
	let arrayLike ={
                0:'a',
                1:'b',
                2:'c',
                length:3
            }
    let arr1 = Array.from(arrayLike);	//类似数组的对象
    let arr2 = Array.from("like");  	//可便利对象
    // arrayLike  = {0: "a",1: "b",2: "c",length: 3};
    // arr1 = ["a","b","c"]
    // arr2 = ["l", "i", "k", "e"];
```

**Array.from()可以接受第二个参数，作用类似于map方法。用来对每个元素进行处理，将处理后的值放入返回的数组。**
示例：

```js
	let arrayLike ={
                0:'a',
                1:'b',
                2:'c',
                length:3
            }
     let arr11 = Array.from(arrayLike, x=> x + "a");
     // arr11 = ["aa", "ba", "ca"];
```

### Array.of()
Array.of()用于将一组值转为数组。
**这个方法主要是为了弥补Array（）的不足。Array.of()总是返回参数值构成的数组，不存在由于参数不同构成的重载。**
示例：

```js
	new Array(3); 	// [ , , ,]
	new Array(3,6);	// [3,6]
	Array.of(3);	//[3]
	Array.of(3,6);	//[3,6]
```

### 数组实例的copyWithin()
数组实例的copyWithin()方法会在当前数组内部将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组。
	**Array.copyWithin(target, start = 0,end = this.length);**
参数解析：

 - target(必选): 从该位置开始替换数据。
 - start(可选):从该位置开始读取数据，默认为0，如果为负值，表示倒数。
 - end(可选):到该位置前停止读取数据，默认为数组长度，如果为负值，表示倒数。

示例：

```js
	[0,1,2,3,4,5].copyWithin(0,3,4);
	// [3,1,2,3,4,5]
```

### 数组实例的find()和findIndex()

 - 有些类似于filter过滤器。
 - find方法用于找出第一个符合条件的数组成员，它的参数是一个回调函数。所有数组成员依次执行，直到找到返回值为true的成员，然后返回该成员。如果没有符合的，返回undefined。
 - findIndex方法大体与find方法一样，不过返回的是该成员的位置。如果没有符合的，返回-1.

示例：

```js
	let list = [2,8,3,7,9,1];
    let a = list.find(x => x>6);		// 8 
    let b = list.findIndex(x => x>6);	// 1
```

### 数组实例的fill()
fill使用给定值填充一个数组。
**Array.fill(target, start = 0, end = this.length)**
用途：常用于空数组的初始化。
参数解读：

 - target：填充数组的值。
 - start：填充的起始位置。
 - end：填充的结束位置。

示例：

```js
	let list = [1,2,3,4];
	list.fill(7);  		// list = [7,7,7,7]
	list.fill(8,1,3) 	// list = [7,8,8,7]
```

### 数组实例的includes()
includes方法会返回一个布尔值，表示这个数组是否含有给定的值。
**与indexof的对比：**

 - 不够语义化，其含义是找到参数值的第一个出现位置。需要比较是否不等于-1.
 - 内部使用严格相等运算符（===），会导致对NaN的误判。

示例：

```js
	[NaN].indexof(NaN);		// -1(表示未找到)。
	[NaN].includes(NaN);	// true
```

