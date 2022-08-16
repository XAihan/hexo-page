---
title: vue通过js来设置div的最小高度所出现的赋值失败问题。
date: 2019-07-03 22:41:54
tags: 问题修复
---

最近敲代码遇到一个小问题，如图：
	   **当页面内容不够多时，会出现底部栏上移的问题。**
![当页面内容不够多时，会出现底部栏上移的问题。](https://img-blog.csdnimg.cn/20190703222117613.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDIyMDY4MA==,size_16,color_FFFFFF,t_70)
一开始我想到的解决方式时，获取到屏幕的高度，并将它赋值为中间的div之中，这就能完美解决footer下移的问题了，说干就干。当时写出的代码是这样的：

```vue
 mounted(){
    console.log('进行了高度赋值');
    console.log($(document).height()/1.7);
    $("#detail").css("min-height", $(document).height()/1.7+ "px");
  }
```
这是我一开始的打算，在mounted周期之中获取高度并进行高度赋值。
但是不知道为什么，一直出现赋值不成功的问题。但是当你进行热加载一次之后就会赋值成功。如下（热加载之后，热加载之前和最开始的图一样。）：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190703222846746.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDIyMDY4MA==,size_16,color_FFFFFF,t_70)
经过研究发现，在**第一次**进入的时候，**最小高度并没有赋值成功**：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190703223220541.png)

**而当重新热加载之后就赋值成功了：**
![如下图](https://img-blog.csdnimg.cn/20190703223120379.png)
目前为什么会出现这个原因还没有搞清楚，但博主能感觉出应该是周期加载那一块的问题。

**那么重头戏来了，说完了问题，咱们来说一下解决方法：**
博主经过多方查询（百度），得到的方法如下：

给需要设置高度的div添加**:style="contentStyleObj"**（可修改样式）
```vue
	<div class="detail"  id="detail" :style="contentStyleObj">
       <div class="top">
         <div class="title">{{detail.article.title}}这是一个很长很长很长的标题，他真的超级长</div>
         <div class="date">发布日期 : {{ detail.article.publishTime | dateformat('YYYY-MM-DD')}}</div>
       </div>
       <div class="content" id="content" v-html="detail.article.content"></div>
     </div>
```
在methods之中添加方法，用来给样式赋值
```vue
  methods:{
    getHeight(){
      this.contentStyleObj.height=window.innerHeight/1.5+'px';
    }
  },
```
在created方法之中调用方法，完美解决问题。
```vue
  created(){
    this.getHeight()
  },
```

PS：尽管如此，但是对于上面代码所出现的问题，博主还是没（懒）有（得）搞清楚，所以如果有大佬知道原因的话，可以评论指导一下小弟。