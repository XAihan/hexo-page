---
title: js之Generator函数（ES6） 
date:  2019-10-12 16:35:20
tags:  基础知识
---

Generator函数是ES6提供的一个异步编程解决方案。语法行为与传统函数完全不同。


### 基本概念
 - 从语法上来说
	首先可以把他理解为一个状态机，封装了多个内部状态。
	执行Generator函数会返回一个遍历器对象，返回的遍历器对象可以依次遍历Generator函数内部的每一个状态。
 - 形式上来讲，Generator是一个普通函数，但是有两个特征。
	1 function命令和函数名之间有一个星号；
	2 函数体内部使用yield语句定义不同的内部状态。
 - 示例：
	```js
	function* helloWorldGenerator(){
        yield console.log('hello');
        yield console.log('world');
        return console.log('ending');
      }
	var hw = this.helloWorldGenerator();
	hw.next();		//hello
	hw.next();		//world
	hw.next();		//ending
	```
	如上代码，当运行时并不会一次运行完所有，而是通过next()方法进行分段的运行。

	 
### yield表达式
由于Generator函数是分段运行的，所以需要一个分段的标志，也就是说，代码运行到哪里停的标志。这就是yield的作用。
**遍历器对象的next方法的运行逻辑如下：**

 1. 遇到yield语句暂停执行后面的操作，并将紧跟yield后的表达式的值作为返回对象的value属性。
 2. 下一次调用next方法，继续执行直到遇到下一个yield。
 3. 如果没有遇到新的yield，就一直运行到函数结束，直到return语句为止。
 4. 如果没有return，则返回对象的value属性值为undefined。

 **yield和return的区别**
 	yield拥有记忆位置的功能，可以根据next进行位置代码的继续执行。
 	
### next方法
next是Generator函数继续运行代码的方法。
该方法可以带有一个参数，该参数会被当作上一条yield语句的返回值。
**这个功能有着很重要的语法意义。Generator函数从暂停状态到恢复状态，其上下文状态（context）是不变的，通过next方法的参数就可以在运行过程中继续向函数体内部注入值，从而调整函数行为。**

示例：

```js
	function* helloWorldGenerator(x) {
       var y = 2 * (yield (x+1));
       var z = yield(y / 3);
       return (x + y + z);
      }
	
	var a = helloWorldGenerator(5);
      console.log(a.next());		//6
      console.log(a.next(12));		//8
      console.log(a.next(13));		//42
```

### for...of循环
for...of循环可以自动便利Generator函数生成的iterator对象，且此时不再需要调用next方法。

**示例：**

```js
	function* helloWorldGenerator() {
        let i=10;
        yield i++;
        yield i++;
        yield i++;
        yield i++;
        yield i++;
        yield i++;
        yield i++;
        yield i++;
      }
      var a = helloWorldGenerator();
      for(let v of a){
        console.log(v);
      }
      // 10，11，12，13，14，15，16，17
```

未完待续。。。
