---
title: 多行省略问题详解：省略号和文字重叠，vue之中多行省略失效。
date: 2019-06-20 13:47:47
tags: 问题修复
---

最近敲代码的时候，遇到一个很奇葩的问题，
原因：客户需求，想要文字两端对齐，多行省略。如图：![如图所示](https://img-blog.csdnimg.cn/20190620130837481.png)
**一，vue之中多行省略失效问题：**

	**先说一下多行省略和文字居中的基本代码**：
```
.aboutUs-text  >>> .p{ 
  overflow: hidden;  //超出隐藏
  text-overflow: ellipsis; //文字超出部分省略号代替
  display: -webkit-box; //必须要的diaplay盒子模型
  -webkit-line-clamp: 7; //行数省略，7为出现7行，之后省略
  -webkit-box-orient: vertical; //规定排列方式为竖直
  text-align: justify;//文字两端对齐
}
```
	以上是基本代码，正常情况下，直接复制粘贴以上css样式就可以实现需求。
	ps：>>>是vue里面的强制修改样式，因为内容是v-html的方法，所以要用到，正常情况下不需要加。

**但是，当我在vue之中使用的时候，问题出现了：虽然是同样的代码，在本地跑也没有问题，但是vue打包上传之后多行省略会失效！！！**

经过长达两个小时的查探，发现问题所在：

	**产生原因：** 这是webpack的锅，他会进行一个操作，从而使得  `display: -webkit-box`失效。
	**解决方法：** 在`display: -webkit-box`进行的时候关掉那个操作就好了。

**这是修改之后的代码：**

```
.aboutUs-text >>> p{
  overflow: hidden; 
  text-overflow: ellipsis; 
  display: -webkit-box; 
  -webkit-line-clamp: 7; 
   /*! autoprefixer: off */ 关闭操作
  -webkit-box-orient: vertical; 
  /* autoprefixer: on */ 打开操作
  text-align: justify;
}
```
可以看到，这样的话，就不会再出现vue打包之后多行省略失效的问题了。

**二，省略号和文字重叠问题**

	当解决了上一个问题之后，又出现了一个新的问题，那就是省略号和文字重叠。如图：
![如图，出现了问题，文字和省略号重叠了](https://img-blog.csdnimg.cn/2019062013374881.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDIyMDY4MA==,size_16,color_FFFFFF,t_70)

**如上图所示，重叠了！！！而且这个文字只在手机端会显示，也就是说，在pc端用浏览器测试的时候是不会出现问题的。**

经过更长时间的查探，发现（猜测）问题所在：

	**产生原因：** 当两端对齐和省略号一起使用时，省略号的地方足够再加上一个（半个）字，所以默认对齐。
	**解决方法：** 将宽度设置为em，目前没有发现再次出现问题，需要更多的真机测试来验证可行性。
**代码：**

```
.aboutUs-text {
  width: 18em;
  font-size: 13px;
}
```
