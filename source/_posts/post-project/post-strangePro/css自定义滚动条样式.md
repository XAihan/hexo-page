---
title: css自定义滚动条样式
date:   2019-12-11 20:03:50
categories: 奇怪的需求
tags: 
- 滚动条
- 奇怪的需求
---

#### webkit内核浏览器
1. ::-webkit-scrollbar 滚动条整体部分

2. ::-webkit-scrollbar-thumb 滚动条里面的小方块，能向上向下移动（或向左向右移动）

3. ::-webkit-scrollbar-track 滚动条的轨道（里面装有Thumb）

4. ::-webkit-scrollbar-button 滚动条的轨道的两端按钮，由于通过点击微调小方块的位置。

5. ::-webkit-scrollbar-track-piece 内层轨道，滚动条中间部分

6. ::-webkit-scrollbar-corner 边角，即垂直滚动条和水平滚动条相交的地方

7. ::-webkit-resizer 两个滚动条的交汇处上用于拖动调整元素大小的小控件

#### IE浏览器
1.	/*三角箭头的颜色*/
			scrollbar-arrow-color: #fff;
2.	/*滚动条滑块按钮的颜色*/
				scrollbar-face-color: #0099dd;
3.	/*滚动条整体颜色*/
				scrollbar-highlight-color: #0099dd;
4.	/*滚动条阴影*/
				scrollbar-shadow-color: #0099dd;
5. /*滚动条轨道颜色*/
				scrollbar-track-color: #0066ff;
6. /*滚动条3d亮色阴影边框的外观颜色——左边和上边的阴影色*/
				scrollbar-3dlight-color: #0099dd;
7. /*滚动条3d暗色阴影边框的外观颜色——右边和下边的阴影色*/
				scrollbar-darkshadow-color: #0099dd;
8. /*滚动条基准颜色*/
				scrollbar-base-color: #0099dd;