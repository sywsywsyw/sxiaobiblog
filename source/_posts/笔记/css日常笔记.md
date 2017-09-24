---
title: css日常笔记
date: 2017-09-14 22:50:00
tags: 笔记
categories: HTML
---
------

<!-- more -->


# CSS

1.字体换行

```css
word-break: break-all;  //包括数字
word-break: break-word; //不包括数字
```

2.下划线

```css
text-decoration: line-through;
```

3.控制文字在一行并且出现...

```css
div{
width: 100%;
overflow: hidden;
text-overflow: ellipsis;
white-space: nowrap;
}
```

4.控制文字在多行显示并且出现...

```css
div{
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
overflow: hidden;
word-break: break-all;
text-overflow: ellipsis;
}
```

5.去除重复的线条

```css
.nolayer {
margin-bottom: -1px;
}
```

6.不知道盒子的宽高怎么让他垂直居中

```css
父元素{
text-align:center
}
元素本身{
vertical-align:middle
display:inline-block
}
元素本身::after{
vertical-align:middle
display:inline-block
height:100%
content:''
}
```

7.清除浮动的要点：

```css
.outer {zoom:1;}  /*==for IE6/7 Maxthon2==*/
.outer :after {clear:both;content:'.';display:block;width: 0;height: 0;visibility:hidden;}
::after{
content:"";
clear:both;
display:table;
}
/*其中clear:both;指清除所有浮动；content: '.'; display:block;对于FF/chrome/opera/IE8不能缺少，其中content（）可以取值也可以为空。visibility:hidden;的作用是允许浏览器渲染它，但是不显示出来，这样才能实现清除浮动。*/
```

8.垂直居中

```css
.center {
position: absolute;
top: 50%;
left: 50%;
-ms-transform: translate(-50%,-50%);
-moz-transform: translate(-50%,-50%);
-o-transform: translate(-50%,-50%);
transform: translate(-50%,-50%);
}
```

9.去除input type=number的上下箭头样式

```css
/*在chrome下：*/
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button{
-webkit-appearance: none !important;
margin: 0;
}
/*Firefox下：*/
input[type="number"]{-moz-appearance:textfield;}
```

10.一个1920_900的大图，在1024_768的分辨率只能显示一部分，希望仍居中显示

```css
.bg{
width: 100%;
background-position: 50% 50%;
}
```

11.剪裁图像：

```css
img{
position:absolute;
clip:rect(0px,60px,200px,0px);
}
```

12.实现div两端对齐

```css
div{
display: -webkit-box;
display: -webkit-flex;
display: -ms-flexbox;
display: flex;
-webkit-box-pack: justify;
-webkit-justify-content: space-between;
-ms-flex-pack: justify;
justify-content: space-between;
}
```

13.如何透过CSS控制文章内的标点符号位置

```css
.article{
text-align: justify;  /*两端对齐*/
word-break: break-all;  /*控制标点不在第一个字显示*/
}
```

14.滚动条样式修改

```css
*::-webkit-scrollbar-track
{
  background-color: white;
}
*::-webkit-scrollbar
{
  width: 0;
  background-color: rgba(0,0,0,0.3);
}
*::-webkit-scrollbar-thumb
{
  background-color: #e4e4e4;
}
```

15.图片居中

```css
/*如果是正方形*/
.wrap{
width: 70px;
height: 70px;
overflow: hidden;
border-radius: 50%
position:relative;
};
/*适用于图片为长方形 使用*/
.wrap img {
display: block;
position: absolute;
top: 50%;
left: 50%;
width: 100%;
height: 100%;
-ms-transform: translate(-50%,-50%);
-moz-transform: translate(-50%,-50%);
-o-transform: translate(-50%,-50%);
transform: translate(-50%,-50%);
}
```

16.网页在Safari快速滚动和回弹的原理： -webkit-overflow-scrolling : touch;的实现

> 现在很多for Mobile的HTML5网页内都有快速滚动和回弹的效果，看上去和原生app的效率都有得一拼。

<http://blog.csdn.net/hursing/article/details/9186199>

17.今天发现移动端点击事件无法生效，但是滑动可以

> 然后就查一些资料，得到了一些理论知识。最重要的一个就是事件流的概念，点击事件可以分解成多个事件。 在移动端，手指点击一个元素，会经过：touchstart --> touchmove -> touchend --》click。 事件流本身会持续进行下去的。

<http://www.myexception.cn/web/1600832.html>

18.网页宽高clientWidth clientHeight获得数值不对的问题

当网页内容撑不满一屏时，通过以下代码获得整个网页高度会有问题

document.body.clientHeight;
document.body.clientWidth;

得到的宽高不对，可能是因为html与body标签缺一个样式：height:100%

```css
html{
height: 100%;
overflow: hidden;//overflow去掉滚动条
}

body{
height: 100%;
}
```

19.手机浏览器上，给body增加overflow:hidden;width:100%;height:100% 无效的问题

```css
1、body加position:fixed;
2、给要滚动的元素添加一个父级，设定高度，overflow：auto；
3、html,body{height:100%;overflow:hidden}
```

20.css修改input、textarea标签placeholder属性默认文字颜色

```bash
input::-webkit-input-placeholder {
  /* WebKit browsers */
  color: #fff;
}
input:-moz-placeholder {
  /* Mozilla Firefox 4 to 18 */
  color: #fff;
}
input::-moz-placeholder {
  /* Mozilla Firefox 19+ */
  color: #fff;
}
input::-ms-input-placeholder {
  /* Internet Explorer 10+ */
  color: #fff;
}
```