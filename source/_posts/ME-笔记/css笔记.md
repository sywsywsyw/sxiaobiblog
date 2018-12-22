---
title: css笔记
date: 2017-09-14T22:50:00.000Z
tags: 笔记
categories: CSS
---

--------------------------------------------------------------------------------

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

3.控制文字在一行并且出现... 一行变省略

```css
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    display:  block;
```

4.控制文字在多行显示并且出现... 多行变二条字体的省略

```css
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2;
overflow: hidden;
word-break: break-all;
text-overflow: ellipsis;
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
*::-webkit-scrollbar-track  //轨道部分；
{
  background-color: white;
}
*::-webkit-scrollbar   //定义了滚动条整体的样式；
{
  width: 0;
  background-color: rgba(0,0,0,0.3);
}
*::-webkit-scrollbar-thumb   //滑块部分；
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

document.body.clientHeight; document.body.clientWidth;

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
input::-webkit-input-placeholder {
  /* placeholder颜色  */
  color: #aab2bd;
  /* placeholder字体大小  */
  font-size: 14px;
  /* placeholder位置  */
  /* text-align: right; */
}
```

21.四周阴影

```bash
-webkit-box-shadow: #c5c5c5 0px 0px 10px;
 -moz-box-shadow: #c5c5c5 0px 0px 10px;
 box-shadow: #c5c5c5 0px 0px 10px;
```

22.一个base64图片的微信加载样式

```bash
<div class="weui-loadmore">
<i class="weui-loading"></i>
<span class="weui-loadmore__tips">正在加载</span>
</div>


.weui-loading {
  width:20px;
  height:20px;
  display: inline-block;
  vertical-align: middle;
  animation: weuiLoading 1s steps(12, end) infinite;
  background: transparent url(data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMjAiIGhlaWdodD0iMTIwIiB2aWV3Qm94PSIwIDAgMTAwIDEwMCI+PHBhdGggZmlsbD0ibm9uZSIgZD0iTTAgMGgxMDB2MTAwSDB6Ii8+PHJlY3Qgd2lkdGg9IjciIGhlaWdodD0iMjAiIHg9IjQ2LjUiIHk9IjQwIiBmaWxsPSIjRTlFOUU5IiByeD0iNSIgcnk9IjUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAgLTMwKSIvPjxyZWN0IHdpZHRoPSI3IiBoZWlnaHQ9IjIwIiB4PSI0Ni41IiB5PSI0MCIgZmlsbD0iIzk4OTY5NyIgcng9IjUiIHJ5PSI1IiB0cmFuc2Zvcm09InJvdGF0ZSgzMCAxMDUuOTggNjUpIi8+PHJlY3Qgd2lkdGg9IjciIGhlaWdodD0iMjAiIHg9IjQ2LjUiIHk9IjQwIiBmaWxsPSIjOUI5OTlBIiByeD0iNSIgcnk9IjUiIHRyYW5zZm9ybT0icm90YXRlKDYwIDc1Ljk4IDY1KSIvPjxyZWN0IHdpZHRoPSI3IiBoZWlnaHQ9IjIwIiB4PSI0Ni41IiB5PSI0MCIgZmlsbD0iI0EzQTFBMiIgcng9IjUiIHJ5PSI1IiB0cmFuc2Zvcm09InJvdGF0ZSg5MCA2NSA2NSkiLz48cmVjdCB3aWR0aD0iNyIgaGVpZ2h0PSIyMCIgeD0iNDYuNSIgeT0iNDAiIGZpbGw9IiNBQkE5QUEiIHJ4PSI1IiByeT0iNSIgdHJhbnNmb3JtPSJyb3RhdGUoMTIwIDU4LjY2IDY1KSIvPjxyZWN0IHdpZHRoPSI3IiBoZWlnaHQ9IjIwIiB4PSI0Ni41IiB5PSI0MCIgZmlsbD0iI0IyQjJCMiIgcng9IjUiIHJ5PSI1IiB0cmFuc2Zvcm09InJvdGF0ZSgxNTAgNTQuMDIgNjUpIi8+PHJlY3Qgd2lkdGg9IjciIGhlaWdodD0iMjAiIHg9IjQ2LjUiIHk9IjQwIiBmaWxsPSIjQkFCOEI5IiByeD0iNSIgcnk9IjUiIHRyYW5zZm9ybT0icm90YXRlKDE4MCA1MCA2NSkiLz48cmVjdCB3aWR0aD0iNyIgaGVpZ2h0PSIyMCIgeD0iNDYuNSIgeT0iNDAiIGZpbGw9IiNDMkMwQzEiIHJ4PSI1IiByeT0iNSIgdHJhbnNmb3JtPSJyb3RhdGUoLTE1MCA0NS45OCA2NSkiLz48cmVjdCB3aWR0aD0iNyIgaGVpZ2h0PSIyMCIgeD0iNDYuNSIgeT0iNDAiIGZpbGw9IiNDQkNCQ0IiIHJ4PSI1IiByeT0iNSIgdHJhbnNmb3JtPSJyb3RhdGUoLTEyMCA0MS4zNCA2NSkiLz48cmVjdCB3aWR0aD0iNyIgaGVpZ2h0PSIyMCIgeD0iNDYuNSIgeT0iNDAiIGZpbGw9IiNEMkQyRDIiIHJ4PSI1IiByeT0iNSIgdHJhbnNmb3JtPSJyb3RhdGUoLTkwIDM1IDY1KSIvPjxyZWN0IHdpZHRoPSI3IiBoZWlnaHQ9IjIwIiB4PSI0Ni41IiB5PSI0MCIgZmlsbD0iI0RBREFEQSIgcng9IjUiIHJ5PSI1IiB0cmFuc2Zvcm09InJvdGF0ZSgtNjAgMjQuMDIgNjUpIi8+PHJlY3Qgd2lkdGg9IjciIGhlaWdodD0iMjAiIHg9IjQ2LjUiIHk9IjQwIiBmaWxsPSIjRTJFMkUyIiByeD0iNSIgcnk9IjUiIHRyYW5zZm9ybT0icm90YXRlKC0zMCAtNS45OCA2NSkiLz48L3N2Zz4=) no-repeat;
  background-size: 100%;
  &.weui-loading_transparent{
    background-image:url("data:image/svg+xml;charset=utf-8,%3Csvg xmlns='http://www.w3.org/2000/svg' width='120' height='120' viewBox='0 0 100 100'%3E%3Cpath fill='none' d='M0 0h100v100H0z'/%3E%3Crect xmlns='http://www.w3.org/2000/svg' width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.56)' rx='5' ry='5' transform='translate(0 -30)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.5)' rx='5' ry='5' transform='rotate(30 105.98 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.43)' rx='5' ry='5' transform='rotate(60 75.98 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.38)' rx='5' ry='5' transform='rotate(90 65 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.32)' rx='5' ry='5' transform='rotate(120 58.66 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.28)' rx='5' ry='5' transform='rotate(150 54.02 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.25)' rx='5' ry='5' transform='rotate(180 50 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.2)' rx='5' ry='5' transform='rotate(-150 45.98 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.17)' rx='5' ry='5' transform='rotate(-120 41.34 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.14)' rx='5' ry='5' transform='rotate(-90 35 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.1)' rx='5' ry='5' transform='rotate(-60 24.02 65)'/%3E%3Crect width='7' height='20' x='46.5' y='40' fill='rgba(255,255,255,.03)' rx='5' ry='5' transform='rotate(-30 -5.98 65)'/%3E%3C/svg%3E");
  }
}

@-webkit-keyframes weuiLoading {
  0% {
    transform: rotate3d(0, 0, 1, 0deg);
  }

  100% {
    transform: rotate3d(0, 0, 1, 360deg);
  }
}

@keyframes weuiLoading {
  0% {
    transform: rotate3d(0, 0, 1, 0deg);
  }

  100% {
    transform: rotate3d(0, 0, 1, 360deg);
  }
}
```

23、去除table表格的间隙

```
border-collapse: collapse;
```

24、CSS3 filter(滤镜) 属性 修改所有图片的颜色为黑白 (100% 灰度):

```css
img {
    -webkit-filter: grayscale(100%); /* Chrome, Safari, Opera */
    filter: grayscale(100%);
}
```

25、vertical-align: 属性值

```
baseline 默认。元素放在父元素的基线上。
sub 垂直对齐文本的下标
super 垂直对齐文本的上标
top 把元素的顶端与行内最高元素的顶端对齐
text-top 把元素的顶端与父元素字体的顶端对齐
middle 把元素放在父元素的中部
bottom 把元素的顶端与父元素字体的底端对齐
length
% 使用line-height属性的百分比来排列此元素，允许使用负值
inherit 规定从父元素vertical-align继承
```

26、pointer-events: none;

```
auto：
与pointer-events属性未指定时的表现效果相同。在svg内容上与visiblepainted值相同
none：
元素永远不会成为鼠标事件的target。但是，当其后代元素的pointer-events属性指定其他值时，鼠标事件可以指向后代元素，在这种情况下，鼠标事件将在捕获或冒泡阶触发父元素的事件侦听器。
其他值只能应用在SVG上。
```

27、怎麼让一个未知宽高元素变为正方形
```css
父元素:{
  width:x;
  height:y;
  position:relative;
}
子元素:{
  position:absolute;
  width:20%;
  padding-top:20%;
  border-radius:50%;
}
```

28、一个阴影效果 适用于图片底部需要放置内容的地方
```css
    background: linear-gradient(bottom, rgba(0,0,0,0.7), rgba(255,255,255,0));
    background: -webkit-linear-gradient(bottom, rgba(0,0,0,0.7), rgba(255,255,255,0));
```

29、js获取上传图片真实的尺寸大小和存储大小
```
http://blog.csdn.net/u014236259/article/details/52885591
让图片按比例缩放
```

30、输入框类型
```
  textarea:focus,
    input[type="text"]:focus,
    input[type="password"]:focus,
    input[type="datetime"]:focus,
    input[type="datetime-local"]:focus,
    input[type="date"]:focus,
    input[type="month"]:focus,
    input[type="time"]:focus,
    input[type="week"]:focus,
    input[type="number"]:focus,
    input[type="email"]:focus,
    input[type="url"]:focus,
    input[type="search"]:focus,
    input[type="tel"]:focus,
    input[type="color"]:focus,
```

31、div模拟input输入框 contenteditable="true" 
```
<!-- html -->
<div class="test" contenteditable="true"  data-text="和主播一起聊天-.-"></div>
<!-- 模拟 placeholder -->
<style>
.test:before {
  content: attr(data-text);
}
.input_mnzz:empty:before {
  content: attr(data-text);
  color: #bbb;
}
</style>
```
