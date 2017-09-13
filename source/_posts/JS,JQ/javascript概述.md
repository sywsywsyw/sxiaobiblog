---
title: javascript概述
date: 2016-02-16 22:30:38
tags:
categories: JS
---
------

<!-- more -->

javascript:;概述.md(markdown)

>把dom身上的一些 事件 属性的赋值给一个函数让浏览器就进行调用

>javascript是一门程序语言

>和计算机交流的语言

#计算机是什么？能做什么?

>计算机用来计算

程序语言就是将人类可读的指令按照一定的规则传递给计算机进行计算，然后将计算的结果传递给显卡计算最终显示出图形界面。

一门程序语言必须具备一些能力，才能和计算机交流明白

#必须能很清楚的告诉计算机，怎样去做存储数据

#必须能很清楚的告诉计算机，怎样去做逻辑操作

##javascript中的逻辑操作
+ - * / % && || ! === !== >= <= > < (eslint)

if(){}
if(){}else{}
if(){}else{}if(){}else{}if(){}else{}if(){}else{}
swich(val){
	case1;
	xxxx;
	break;
	case2;
	xxxxx;
	break;
	default;
	xxxx;
	break;
}




## 数据的存储

var v='aaa' ; String
var v=[1,2,3,'aa'] ;  数组Array
var v=function(){}; function
var v={a:1,b:2,c:3}; Object  存储形式为表格

console.dir()


var v = 1 ;   number   存储单独值
var v = true ;   Booleam布尔值
var v=null ;     null
var v = undefined ;   undefined             valueOf()

##javascript中用类似于'表'的形式存储数据(对象)

>
var fn=function(){
	alert(1);
	console.log(1);
	return 1;
}
## 定义函数的时候发生了什么？

>要把代表函数的那张表构建完全
1.`调用`这个属性要赋值，函数体内部的字符串
2.需要把当前 可见范围内的所有的变量，由近到远的记录到一个链条中，形成一条作用域链

>写在函数体的代码去那里了？

## 函数会用一个不可见的属性`调用`来存储函数体中的代码
>{'调用':'concole.log(1);return1'}
>函数对象特殊性在于它可以被调用
>函数名+（）可以调用函数
>调用函数的时候：函数对象会去读取自己身上`调用`
>这个属性的值，取出来一些字符串，把这些字符串交给js解析器去当做javascript代码去执行
>于此同时还会取出这个函数的作用域链 用来辅助这段代码的执行

## 在函数this是什么？

>只有在函数中才有this

>函数定义的时候没有this
>函数在调用的时候
>根据调用的不同情况，来决定this变成什么

## 到底有那些不同的调用方式
var obj={};
var fn=function(){
	console.log(this);
}
obj.c=fn;
fn();        this指向window
obj.c();     指向obj对象
obj.c.call('111')   指向它的宿主对象
obj.c.apply([1,2,3,4],[3,4])
fn.call([1,2,3,4,5]);   指向它的宿主对象
第一种   正常定义(不把函数作为某个对象的属性)和正常调用(使用()的方式调用函数)一个函数的时候 this指向window
var fn=function(){
	console.log(this)
}
fn()
第二种 如果我们需要把this换成任何我们想要的对象  指向obj对象
var obj={
	a:1;
	b:1;
    c:function(){
	console.log(this)
}
}
obj.c()
第三种 借助函数对象上的call和apply的方法  指向它的宿主对象 更改我们想要的任何对象
var obj={a:1;b:2}
 obj.c=function(){
	console.log(this)
}
obj.c();
obj.c.call('a,b')

#### call



## 当我们写好一分程序之后，计算机在的过程中发生了什么？




###### 栈值对 一张表嵌套一张表
###### objecte 有toString方法;

###### console.log 方法 v.valueOf     
###### alert            v.toString   "[object Object]"

###### 左边为栈 右边为值  length为不可枚举的属性  for in 循环中不显示

###### 对象的栈 和值 无序分布
###### 函数也是一个对象





< localStorage.setItem('d',12)          会在浏览器中存储一些数据(字符串) >     
< localStorage.getItem('d',12)          会从本地存储中取出一些数据>
 localStorage.removeItem('d',12)       会从本地存储中删除一条数据
< JSON.stringify()
把对象转成字符串
//{a:1,b:2}=>'{"a":1,"b":2}'
JSON.parse()
把符合规则的字符串重新转回对象
//['1','2','3']=][1,2,3] -->
