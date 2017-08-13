---
title: iframe
date: 2016-08-11
tags:
categories: HTML
---
------

<!-- more -->

> ### iframe使用问题

#### 怎么获取iframe内容的高度？(iframe自适应高度的问题)

```html
<div class="iframe-wrap" >
<iframe src="index - 副本.html" frameborder="0"  id="login_container" scrolling="no" width="1000" height="400" onLoad="iFrameHeight()"></iframe>
</div>
```
```js
function iFrameHeight() {
var ifm= document.getElementById("login_container");
console.log(ifm);
var subWeb = document.frames ? document.frames["login_container"].document :ifm.contentDocument;
  if(ifm != null && subWeb != null) {
    ifm.height = subWeb.body.scrollHeight;
    console.log(ifm.height)
   }
}
```
为了测试，iframe的height你可以预先设置一个固定高度比如：height="400"（也可以使用100%）,iframe加载完，会自动调整页面大小。

#### iframe怎样刷新父页面的父页面？

frame页面是内嵌到父页面的，当点击iframe页面的服务器控件时，默认只刷新iframe页面，父页面是不会刷新的。若想刷新父页面，可以使用js来实现，如
     1. parent.location.reload();
     这种方法会重新加载整个页面。但如果要在原页面的基础上传递参数，则可以使用下面的方法：
     2.top.document.location.href='xxx.aspx?id=xx'。
     但这两种方法都有一个共同的缺点，就是iframe内嵌页面的状态不会保存了，刷新后会重新回到第一次加载的状态。

#### 怎么使iframe在iOS设备上支持滚动？
```html
<div class="iframe-wrap" >
<iframe src="index - 副本.html" frameborder="0"  id="login_container" scrolling="no" width="1000" height="400" onLoad="iFrameHeight()"></iframe>
</div>
```
CSS 代码
要让IFRAME支持滚动,需要一个常用的CSS属性和一个很少人知道的CSS属性(property):

**-webkit-overflow-scrolling: touch;** 属性值就是专为浏览器中溢出(overflow)时需要滚动的元素设计的。 如果没有指定这个属性,当你想滚动iframe时,实际上会导致外层页面的滚动,通过它你就可以对IFRAME的滚动进行控制! 在原作者的博客站点中,使用了下面的CSS:

```css
.iframe-wrap {  
  position: fixed;   
  right: 0;   
  bottom: 0;   
  left: 0;  
  top: 0;  
  -webkit-overflow-scrolling: touch;  
  overflow-y: scroll;  
}  
.login_container{  
  height: 100%;  
  width: 100%;  
}  
```
> ### iframe原理

把iframe解释成“浏览器中的浏览器“很是恰当

```html
<iframe frameborder=0 width=170 height=100 marginheight=0 marginwidth=0 scrolling=no src=http://www.163.com></iframe>
```
iframe用于设置文本或图形的浮动图文框或容器。

#### border
```html
<iframe border="3"></iframe>
```
设定围绕图文框的边缘宽度

#### frameborder
```html
<iframe frameborder="0"></iframe>
```
设置边框是不否为3维（0=否，1=是）

#### height,width
```html
<iframe height="31" width="88"></iframe>
```
设质边框的宽度和高度

#### scrolling
```html
<iframe scrolling="no"></iframe>
```
是否有滚动条（yse,no,auto)

#### src
```html
<iframe src="girl.gif"></iframe>
```
指定iframe调用的文件或图片(HTML,HTM,GIF,JPEG,JPG,PNG,TXT,*.*)
