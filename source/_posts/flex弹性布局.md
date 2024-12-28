---
title: flex弹性布局
date: 2024-09-17 20:02:24
categories:
- [前端开发]
tags:
- [前端]
---

# flex弹性布局与问题记录

### flex 弹性布局 子标签设置宽度无效的问题

Flexbox 是 flexible box 的简称（注：意思是“灵活的盒子容器”），是 CSS3 引入的新的布局模式。它决定了元素如何在页面上排列，使它们能在不同的屏幕尺寸和设备下可预测地展现出来。

它之所以被称为 Flexbox ，是因为它能够扩展和收缩 flex 容器内的元素，以最大限度地填充可用空间。

MDN介绍：弹性盒子是一种用于按行或按列布局元素的一维布局方法。元素可以膨胀以填充额外的空间，收缩以适应更小的空间。

目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全地使用这项功能。

任何一个容器都可以指定为 Flex 布局。

行内元素也可以使用 Flex 布局。

``` css
section {
  display: flex;
}
```

注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。

采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。

<div align="center">
    <img src="flex弹性布局/01.png">
</div>

容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。

项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。

[菜鸟教程](https://www.runoob.com/w3cnote/flex-grammar.html)

[阮一峰的弹性布局教程](https://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

**flex-shrink 属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。**

*如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的**flex-shrink属性为0**，其他项目都为1，则空间不足时，前者不缩小。*

父元素设置了display:flex,那么所有的子标签都会默认加上flex:0 1 auto;
其中1 就是 flex中的 flex-shrink 属性,表示开启了元素的收缩功能，所以才会有左边子标签会挤掉右边子标签的一部分的问题。

### 主要结论
设置 ** flex-shrink: 0;**可以避免被拉伸

举个例子：
``` css
.cardInfoItem text:nth-last-child(2) {
  flex-shrink: 0;
}
.cardInfoItem image {
  width: 28rpx;
  margin-right: 14rpx;
  flex-shrink: 0;
}
```