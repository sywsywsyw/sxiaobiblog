---
title: dom的概述
date: 2017-08-15 08:43:33
tags:
categories: HTML
---
------

<!-- more -->
#DOM是什么

Document  Object Modal(文档对象模型)

我们在页面中看到的 div,span,p,h1 等等元素或文字
在 javascript 眼中都是一个对象

# 从一个web应用的开发说起

第一步，从页面中去选取一个元素出来
当我们的代码在浏览器中去运行时，
浏览器已经帮我们创建了很多对象，
对象中有很多方法，可供我们使用
这些东西都在一个叫做window的全局变量里

window对象中的属性，可以省略window. 去调用
eg: window.setTimeout

选取元素，我们从window.document开始

## 选取元素的方式

快速从document中取出一个DOM对象的办法
* document.body
* document.head
* document.title
* document.documentElement 代表了整个html标签的一个DOM对象

* document.querySelector()
* document.getElementById()返回值单个

* document.querySelectorAll()
* document.getElementsByClassName()
* document.getElementsByTagName()
* document.getElementsByName()

这些方法的返回结果是什么？
前两个的返回结果是一个代表了页面中元素的对象  我们把他叫做DOM对象
后四个的返回结果是一个类数组对象，对象中用     我们把他叫做DOM集合
var obj={
	0:Dom对象,
	0:Dom对象,
	......
	length:12
}


## DOM对象中的常见的属性和方法
### object

* toString()
* valueOf()       内部的方法

### EventTarget      

* addEventListener()
* removeEventListener()
* dispatchEvent()


### Node

所有的DOM对象都是一个’节点‘这三个属性用来描述节点
* nodeName
* nodeType
* nodeValue

我们能从每个DOM对象身上取到自己的相邻或父节点或子节点

* ChildNode     返回值DOM对象
* firstChild      返回值DOM对象
* lastChild       返回值DOM对象

* parentElement
* parentNode

* previousSibling
* removeChild()

取节点的文本内容（会过滤掉标签）
* textContent

每个DOM对象中都提供了一些操作节点的方法

通常采用 父DOM对象.xxx （DOM)这种方式

* appendChild()       box.appendChild(el).style.color = 'red'  返回值为一个DOM对象所以可以继续使用DOM里面的方法
* insertBefore()       返回值 为你插入的那个DOM对象
* replaceChild()       返回值 替换成的那个DOM对象
* removeChild()        返回值 移除成的那个DOM对象  var tmp = box.removeChild(el)
* haChildNodes()    
* contains()        （true,flase）查看`节点`是否包括另外一个节点？可以做唯一的标识符

* cloneNode()       (true复制全部，false复制结构)

* hasChildNodes()    返回值 布尔类型  el.children.length
* contains()         返回值 布尔类型
* cloneNode()        返回值 DOM对象(true,false)

* childNodes()
* replaceChild()

### Element(元素)

`元素`和`节点`的区别
不带标签的，比如div内容的文字，比如注释，它们只是节点，不是元素

* children  取一个DOM对象的所有子元素  DOM集合
* firstElementChild
* lastElementChild

* nextElementSibling
* previousElementSibling

对元素属性的操作 （HTML元素的属性 就是头标签里的那些k=""中的k)
* classList      操作类
* className      可读写
* id             可读写
* getAttribute()   
* setAttribute()  没有返回值，只是做一个操作
* hasAttribute()  判断元素标签中有没有某个属性
* removeAttribute() 没有返回值，只是做一个操作

* outerHTML
* tagName

获取该元素的视察坐标(和offset区别)或者和其他位置相关信息的坐标
* getBoundingClientRect() 返回值是{top:x,left:x,bottom:1,width:1,height:1};
el.getBoundingClientRect.top
* scrollLeft 相对于父元素滚动的距离
* scrollTop  相对于父元素滚动的距离
* clientWidth 一般用来结合document.documentElementl.clienWidth
* clientHeight

从某个DOM对象开始，可以缩小范围纠结去查找元素
* getElementsByClassName()
* getElementsByTagName()
* querySelector()
* querySelectorAll()

### HEMLElement

* innerHTML  可读写的 能设置某个DOM对象内部的html结构
* innerText   剥离标签直接获取取文本

实时获取元素信息
* offsetHeight   前四个返回不带`px`具体的数值
* offsetWidth
* offsetTop
* offsetLeft
* offsetParent  获取具有定位属性的元素 返回值DOM对象

操作行内样式
* style         可读写 读的时候实时获取元素行内样式的值，不会去计算 Css文件中定义属性


### HTML xxx Element

* value
* checked
* src

## 添加事件的两种方式及其区别

事件 事件对象 添加事件的方式 不同方式之间的区别
阻止事件默认行为 阻止事件流 事件委托

我们给DOM对象的onclick属性赋值，值为一个函数
这次赋值和普通 的对象赋值不太一样
js会告诉浏览器，密切关注这个元素，如果有人点击它
帮我把这个函数运行一下，
运行函数的时候给我传一个参数，参数为一个对象
对象中要详细的记录这次点击的一些信息 这个对象被称为事件对象

```javascript

// 使用 onxxx

var el=document.getElementById('box')
el.style.color='red';
el.onclick=(function(){
	return function(){

	}
})();

// 使用addEventListener

el.addEventListener('',function(){
   console.log(e)
},flase)

区别：

1. 一些H5事件并没有onxxx这个版本
2. onxxx 再赋值一次，会覆盖上次赋值的那个 函数，addEventListener 没有这个问题。它可以给事件添加多个函数，事件触发的时候 按照添加顺序，逐个调用处理函数


移除事件 取消事件注册
1. onxxx  
   this.onxxx=null;
2. addEventListener
   var clickHandler = function(e){
		 console.log(e)
		 this.style.background = 'red';
		 this.removeEventListener('click',clickHandler);
	 }
	 yi.addEventListener('click',clickHandler)

### 自定义事件
//不要给自定义事件阻止冒泡  e.stopPropagation()
//鼠标按住5秒触发一个事件
eg: var fiveonclick= new Event('fiveonclick')
    yi.addEventListener('mousedown',function(){
    	console.log('5秒事件触发了')
    	clearInterval(timerId)
    })
    var timerId;
    yi.addEventListener('mousedown',function(){
    	var i=0;
		timerId=setInterval(function(){
			i +=1;
			if( i === 5 ){
				yi.dispatchEvent(fiveonclick)
				yi.style.background='red'
				}
		},1000)
	 })
	yi.dispatchEvent(fiveonclick);

//三次点击函数
	var onclickwu=function(el,fn){
		var clickwu = new Event('clickwu')
		el.addEventListener('clickwu',function(e){
			//不要给自定义事件阻止冒泡
			fn.call(el,e);
		})
		var i=0;
		el.addEventListener('click',function(e){
			e.stopPropagation();
			i += 1;
			if( i === 3 ){
				el.dispatchEvent(clickwu)
				el.style.background='blue'
			}
		})
		el.addEventListener('click',function(e){
			// console.log(1)
			e.stopPropagation();
		})
		// el.addEventListener('click',function(e){
		// 	console.log(1);
		// 	e.stopPropagation();
		// });
	}
	onclickwu(yi,function(){
		alert(1)
	})
	onclickwu(er,function(){
		alert(2)
	})
	onclickwu(san,function(){
		alert(3)
	})
//长按事件函数
// el对象 fn替换的this c控制时间
eg:var changan=function(el,fn,c){
		var changan= new Event('changan')
		el.addEventListener('changan',function(e){
			fn()
		})
		var timerId;
		el.addEventListener('mousedown',function(){
			var i=0;
			setInterval(function(){
				i += 1;
				if( i === c ){
					el.dispatchEvent(changan)
				    el.style.background='red'
				}
			},1000)
		})
		document.addEventListener('mouseup',function(){  
			console.log('5秒事件触发了')
			clearInterval(timerId)
		})

	}

     changan(yi,function(){
     	alert(1)},5)


click dblclick  threeclick

var threeclick = new Event('threeclick');  //用变量存储下来
var box=document.querySelector('.box');
box.addEventListener('threeclick',function(){
	console.log('threeclick')
})
box.addEventListener('click',(function(){
		var cishu=0;
		return function(){
			cishu += 1;
			if( cishu ===3){
				box.dispatchEvent(threeclick)
			}
			setTimeout(function(){
		cishu=0;
	},500)
		}
	})())
box.dispatchEvent(threeclick);   //dispatchEvent 分发

### 阻止事件冒泡和事件
1. 从页面结构上调整,让元素之间不再是包含关系
2. 使用事件对象身上的stopPropagation去阻止它
box.addEventListener('click',function(e){
    	console.log(1);
    	e.stopPropagation();
    });
eg:
  yi.addEventListener('click',function(e){
		console.log(1);
		e.stopPropagation();
	});
	er.addEventListener('click',function(){
		console.log(2);
	});
	san.addEventListener('click',function(){
		console.log(3);
	});

## 阻止事件的默认行为

    document.addEventListener('dblclick',function(e){
    	e.preventDefault();
    })
//从事件的根源去阻止它

    document.addEventListener('mousedown',function(e){
    	e.preventDefault();
    })
		document.addEventListener('keydown',function(e){
			e.preventDefault();
		})
		document.querySelector('input').addEventListener('mousedown',function(){
			e.preventDefault();
		})

### 回调函数

当我们把函数X作为参数传给函数Y函数Y内部有对函数X的调用我们把函数X叫做回调函数

##遍历一个函数
var arr=[1,2,3,4,5]
arr.forEach(function(v){
	console.log(v)
})
如果就是数组，我们遍历的时候可以使用
var arr = [1,2,3,4,5]
arr.forEach(function(v){
	console.log(v)
})
如果是类数组对象，我们遍历的时候可以使用
var arr=[];
forEach = arr.forEach;
filter = arr.filter
var els = document.querySelectorAll('div')
forEach.call(els,function(v){
	console.log(v)  //v就是dom集合中的dom对象
})
arr.filter(function(v){
	return v.id = id
	//filter 条件为真保存下来如果满足就放到新数组中 要不就不操作
})
