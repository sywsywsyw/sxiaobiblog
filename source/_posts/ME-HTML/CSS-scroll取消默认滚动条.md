---
title: scroll取消默认滚动条
date: 2016-01-30
tags: CSS
categories: CSS
---
------

<!-- more -->

忽然想到一个更简单的方式

## 第一种 css

```css
<style>
	/*cms滚动条*/
	.nav2-list::-webkit-scrollbar-track{
		background-color: white;
	}

	.nav2-list::-webkit-scrollbar{
		width: 0px;
		background-color: rgba(0,0,0,0.3);
	}

	.nav2-list::-webkit-scrollbar-thumb{
		background-color: #e4e4e4;
	}
</style>
```

## 第二种 div+css 控制
今天看见layui群里有个网友问不想要左侧滚动条，然后就去看了<http://www.layui.com/demo/>发现可以这样写：


当我们的内容超出了我们的div，往往会出现滚动条，影响美观。

尤其是当我们在做一些导航菜单的时候。滚动条一出现就破坏了UI效果。我们不希望出现滚动条，也不希望超出去的内容被放逐，就要保留鼠标滚动的效果。
大体思路是在div外面再套一个div。这个div设置overflow:hidden。  
而内容div设置 overflow-y: scroll;overflow-x: hidden;
然后再设置外层div的width小于内层div的width。
这个内层div其实是会出现滚动条的，所以不影响鼠标的滚动效果，而且我们看不到滚动条了。   

css代码

```css
	<style>
      ul,li{
      	margin: 0;
      	padding: 0;
      	list-style: none;
      }
      .nav-wrap {
      	width: 200px;
      	height: 400px;
      	overflow: hidden;
      	border: 1px solid #ccc;
      	margin: 100px auto 50px;
      }
      .nav-list {
      	height: 100%;
      	width: 220px;
      	overflow-y: auto;
      	overflow-x: hidden;
      }
      .nav-item {
      	width: 200px;
      	margin: -1px;
      	height: 40px;
      	line-height: 40px;
      	text-align: center;
      	border: 1px solid #ccc;
      }
      .btn-wrap {
      	width: 100%;
      	text-align: center;
      }
	</style>
```
html代码

```html
<div class="nav-wrap">
	<ul class="nav-list">
		<li class="nav-item">子菜单一</li>
		<li class="nav-item">子菜单二</li>
		<li class="nav-item">子菜单三</li>
		<li class="nav-item">子菜单四</li>
	</ul>
</div>
```

演示链接：<https://sywsywsyw.github.io/CSS-scroll/>
layui: <http://www.layui.com/demo/>
