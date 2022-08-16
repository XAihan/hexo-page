---
title: BOM引导——Location对象 
date:  2022-08-11 17:33:23
tags: 基础知识
---


location是最有用的BOM对象之一，他提供了与当前窗口中加载的文档有关的信息，还提供了一些导航功能。事实上，location对象是一个很特别的对象，因为他其实window对象，也是document对象。
换句话说：window.location和document.location引用的是同一个对象。


| 属性     | 说明                                          | 例子                                                             |
| -------- | --------------------------------------------- | ---------------------------------------------------------------- |
| hash     | 设置或返回从井号 (#) 开始的 URL（锚）。       | #id001                                                           |
| host     | 设置或返回主机名和当前 URL 的端口号。         | www.example.com:8080                                             |
| hostname | 设置或返回当前 URL 的主机名。                 | www.example.com                                                  |
| href     | 设置或返回完整的 URL。                        | http://www.example.com:8080/html/index.html?name=aa&age=23#id001 |
| pathname | 设置或返回当前 URL 的路径部分。               | html/index.html                                                  |
| port     | 设置或返回当前 URL 的端口号。                 | 8080，如果是默认80端口，返回空字符                               |
| protocol | 设置或返回当前 URL 的协议。                   | http                                                             |
| search   | 设置或返回从问号 (?) 开始的 URL（查询部分）。 | ?name=aa&age=23                                                  |


location对象的方法：

|           |                          |
| --------- | ------------------------ |
| assign()  | 加载新的文档。           |
| reload()  | 重新加载当前文档。       |
| replace() | 用新的文档替换当前文档。 |

 **PS: 如果用replace（）的话，相当于销毁当前页面而后打开另一个页面，也就是说，你无法通过后退按钮返回上一个页面。**

**PS：对于assign方法，当你调用window.location或者location.href时，系统会默认调用assign方法。如下：**

```js
	window.location = "https://www.csdn.net/";
	location.href = "https://www.csdn.net/";
```
这两行代码都会将当前页面跳转到指定网页。