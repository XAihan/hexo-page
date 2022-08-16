---
title: js之字符串方法总结
date: 2019-10-16 13:41:16 
tags: 基础知识
---

博主上回总结了数组的方法，今天来说一下字符串的常用方法总结。
还是话不多说，干干货要紧。

## 查找字符串中的字符串
### indexof()  
 - indexof()方法返回字符串中指定文本首次出现的索引（位置）。
 - 如果没找到文本，返回-1.
 - 示例
	
	```js
	var str = "The full name of China is the People's Republic of China.";
	var pos = str.indexOf("China");
	```

### lastIndexOf()

 - lastIndexOf()方法返回字符串中指定文本最后一次出现的索引（位置）。
 - 如果没找到文本，返回-1.
 - 示例
	
	```js
	var str = "The full name of China is the People's Republic of China.";
	var pos = str.lastIndexOf("China");
	```

### search()

 - 搜索特定值的字符串，并返回匹配的位置。
 - 示例：
	
	```js
	var str = "The full name of China is the People's Republic of China.";
	var pos = str.search("locate");
	```
 - 和indexOf()的区别
 	1 search()方法无法设置第二个参数（开始位置参数）
 	2 indexOf()方法无法设置更强大的搜索（正则表达）


## 提取部分字符串
### slice(start,end)

 - slice()提取字符串的某个部分并在字符串中返回被提取的部分。
 - 参数解读：
	1 start : 开始位置
	2 end : 结束位置
	3 如果某个值为负，则从字符串的结尾开始计数
	4 如果省略第二个参数，则默认到结束
	
 - 示例：
	
	```js
		var str = "Apple, Banana, Mango";
		var res = str.slice(7,13);
		//Banana
	```

### substring()

 - 类似于slice()
 - 不同之处在于substring()无法接受负的索引。
 - 示例：
 
	```js
		var str = "Apple, Banana, Mango";
		var res = str.substring(7,13);
		//Banana
	```

### substr()

 - 方法类似于slice()
 - 不同之处在于第二个参数规定为被提取部分的长度。
 - 如果首个参数为负，从结尾计算位置。
 - 示例：
	```js
		var str = "Apple, Banana, Mango";
		var res = str.substr(7,6);
		//Banana
	```

## 替换字符串的内容
### replace()

 - replace()方法用另一个值替换在字符串中指定的值。
 - 注意事项
	1 默认只替换首个匹配。
	2 默认对大小写敏感
	3 如果需要执行大小写不敏感的，可以使用正则表达式（正则表达式不带引号）
 - 示例：
	
	```js
		str = "Please visit Microsoft!";
		var n = str.replace("Microsoft", "W3School");
		//Please visit W3School!
	```

## 转换为大写和小写
### toUpperCase() && toLowerCase()
 - 通过toUpperCase()可以把字符串转换为大写。
 - 通过 toLowerCase()可以把字符串转换为大写。
 - 示例：
	
	```js
	var text1 = "Hello World!";       // 字符串
	var text2 = text1.toUpperCase();  // HELLO WORLD
	var text3 = text1.toLowerCase();  // hello world
	```

### concat()

 - concat()连接两个或者多个字符串
 - 方法类似于 + 运算符
 - 示例：
	
	```js
		var text1 = "Hello";
		var text2 = "World";
		var text3 = text1.concat(" ",text2); 
		var text = "Hello" + " " + "World!";
		//Hello World
	```

### trim()

 - trim()方法删除字符串两端的空白符
 - 示例：
	
	```js
		var str = "       Hello World!        ";
		alert(str.trim());
	```

## 提取字符串字符
### charAt()

 - charAt()返回字符串中指定下标（位置）的字符串
 - 示例：
	
	```js
	var str = "HELLO WORLD";
	str.charAt(0);            // 返回 H
	```

### charCodeAt()

 - charCodeAt()方法类似于charAt()，不过返回的是指定索引字符的 unicode 编码。
 - 示例：
 
	```js
		var str = "HELLO WORLD";
		str.charCodeAt(0);         // 返回 72
	```

### split()

 - split()方法将字符串转换为数组。
 - 示例：

	```js
		var txt = "a,b,c,d,e";   // 字符串
		txt.split(",");          // 用逗号分隔
		txt.split(" ");          // 用空格分隔
		txt.split("|");          // 用竖线分隔
	```
如果省略分隔符，被返回的数组将包含 index [0] 中的整个字符串。

如果分隔符是 ""，被返回的数组将是间隔单个字符的数组：