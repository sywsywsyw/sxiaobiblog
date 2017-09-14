---
layout: w
title: css属性
date: 2017-09-14 22:13:27
tags:
---

## 网页在Safari快速滚动和回弹的原理： -webkit-overflow-scrolling : touch;的实现

> 现在很多for Mobile的HTML5网页内都有快速滚动和回弹的效果，看上去和原生app的效率都有得一拼。

http://blog.csdn.net/hursing/article/details/9186199

## 今天发现移动端点击事件无法生效，但是滑动可以

> 然后就查一些资料，得到了一些理论知识。最重要的一个就是事件流的概念，点击事件可以分解成多个事件。
在移动端，手指点击一个元素，会经过：touchstart --> touchmove -> touchend --》click。
事件流本身会持续进行下去的。

http://www.myexception.cn/web/1600832.html
