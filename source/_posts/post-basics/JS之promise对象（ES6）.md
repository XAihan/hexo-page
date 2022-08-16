---
title: JS之proise对象（ES6） 
date:  2019-10-12 12:18:16
tags:  基础知识
---


在ES6语法之中，**Promise**对于处理异步编程的解决方案，比传统的解决方案——回调函数和世间——更合理而且更强大。

### promise含义
所谓promise，简单来说就是一个容器，里面保存着某个未来才会结束的世间的结果。
**简单来说，我们可以通过它获取异步操作的信息，**
**他提供统一的api，各种异步操作都可以通过同样的方法进行处理。**

### promise特点
promise有两个特点：

 - 对象的状态不受外界影响。
 - 一旦状态改变就不会再变，任何时候都可以得到这个结果。

### 基本用法
ES6规定，Promise是一个构造函数，用来生成Promise实例。
示例：

```js
	var promise = new Promise(function(reslove,reject){
                    //some code
                    if(/*异步操作成功*/){
                        reslove(value);
                    }else{
                        reject(erroe)
                    }
                })
```
Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject。他们是两个函数，由js引擎提供，不用自己部署。

**Promise实例生成之后，可以用then方法分别制定Resolve和Reject的回调函数。**
如下：

```js
	promise.then(function(value){
		//success	
	},function(erroe){
		//failure
	})
```

### then方法
Promise提供then方法，他的作用是未Promise实例添加状态改变时候的回调函数。
**简单来说，then方法就是你当前Promise方法执行完毕之后才会执行的方法。**
 - then方法返回的是一个新的Promise,因此可以采用链式写法，即then方法之后再调用一个then方法。
 - 示例
```js
	getJSON("/posts.json").then(function(json){
		return json.post
	}).then(function(post){
		//some code
	})
```
上面的代码使用then依次指定了两个then方法，第一个的回调函数完成之后，会将结果作为第二个回调函数的参数。

### catch方法
catch方法用于指定发生错误时的回调函数。

示例：

```js
	getJSON("/posts.json").then(function(json){
		//...
	}).catch(function(post){
		//some code
	})
```

上面的代码，getJSON会返回一个promise对象，如果对象状态变为**Resolved（即执行成功），会调用then方法。**如果状态变成**Rejected(即执行出错)，便会调用catch指定的方法。**

### Promise.all()
 Promise.all()方法，用于将多个 Promise实例包装成一个 Promise实例。
 实例：
 

```js
	var p = Promise.all([p1,p2,p3]);
```

 - 上面的代码中， Promise.all()接受一个数组作为参数，其中p1,p2,p3都是 Promise实例，如果不是，会调用Promise.resolve方法，把他们变成 Promise实例。
 - P的状态由p1,p2,p3决定，分为两种情况
	只有p1,p2,p3全部异步出错，P才会变成错误状态。此时p1,p2,p3返回值组成一个数组，传递给P的回调。
	如果p1,p2,p3有一个成功，p的状态就是成功状态，此时第一个成功实例的返回值会传递给P的回调函数


### Promise.race()
 Promise.race()方法，同样是用于将多个 Promise实例包装成一个 Promise实例。
 不同点在于
 
 - **P的状态的改变，只要有一个p1,p2,p3实例有一个率先改变状态，p的状态就会跟着更改，那个率先改变的Promise实例返回值会传递给p的回调函数。**

### Promise.resolve()
该方法作用是将现有对象转为Promise()对象。
分为四种情况：

 - **参数是一个Promise实例**
	如果是Promise实例的话，将不做任何修改，原封不动返回这个实例。
 - **参数是一个thenable对象**
	即具有then方法的对象，resolve（）会将这个对象转为promise方法并立即执行then方法。
 - **参数不具有then方法或者根本不是对象**
	会直接返回一个状态为Resolve的Promise对象。
	示例：
	```js
	var p = Promise.resolve('Hello');
	p.then(function(s){
		console.log(s);		//Hello	
	})
	```
	
 - **不带有任何参数**
	直接返回一个状态为Resolve的Promise对象。


### Promise.reject()
Promise.reject()会返回一个新的Promise示例，状态为Rejected。

### 两个有用的附加方法。
#### done（）
无论Promise对象的回调链是then还是catch，只要最后一个方法抛出错误，都有可能无法捕获到，为此，提供了done方法，他总是处于回调链的尾端，保证抛出任何可能出现的错误。
**运行流程：**

```js
	.then(f1)
	.catch(f2)
	.done(f3)
```

#### finally()
和done类似，最大的区别在于，done是一个promise对象，而**finally接受一个普通回调函数作为参数，该参数不管怎么样都会执行。**