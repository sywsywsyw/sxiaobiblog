---
title: jQuery概述
date: 2016-04-20 22:31:36
tags:
categories: JQ
---
------

<!-- more -->
# jQuery

### 前端开发在开始写代码之前，一般首先要解决的两个问题

#### 1.解决js标准本身的兼容性问题 es5shim.js

#### 2.解决DOM扩展部分的兼容性问题 jQuery库

```html
//第一个引入的js库用来解决兼容性问题.
<script src="jquery.js"></script>
<script src="header.js"></script>
<script src="footer.js"></script>
```
分开引用的js文件一定要解决的一个问题
不能污染全局作用域

```javascript
var getEle = function(selector){ //定义一个变量 参数为selector
if(document.querySelector){ //判断有没有这个方法
return document.querySelector(selector)
}else{
console.warnning('浏览器不支持');
console.error('请更换浏览器');
}
}
```

```
var el = getElement('.abc')
var getElement = function(){
}
```
上面的这种写法的两个问题
1.用户需要学习一门全新的语法
2.用户需要避开那个库中的所有全局变量

DOM对象的存储方式 是怎么存储的?

可以使用查询console.dir()

DOM集合的存储方式 是怎么存储的?

可以使用查询console.dir()

jQuery对象的存储方式 是怎么存储的?

可以使用查询console.dir()

在Obj对象中存储了100+方法

<!-- console.dir( $('.item')) -->
## jQuery 实现原理

1.new的时候究竟发生了什么？
2.对象的原型链
3.函数对象身上一个属性(prototype)和一个方法(call)
4.this的指向

jq中的大多数方法都会返回一个jq集合
5\. 操作集合的方法就是原集合
6\. 对集合做过过滤或者导致集合改变的一些方法返回改变后的是Query集合
7\. $ .append 这一类方法，当涉及到创建dom对象时，他们会返回创建完成后的一个Jquery 集合
所以在jq中经常使用链式调用
```javascript
$('#one h1')
.width(100)
.height(200)
.css({color:'red'})
.position();在这里终止
```
```javascript
(function(){
var add = function(selector){
console.log(this)
var els = document.querySelectorAll(selector)
for(var i=0;i<els.length;i++){
this[i] = els[i]
console.log(this)
}
this.length = els.length
}
add.prototype.addClass = function(str){
console.log(add)
console.log(this)
for(var i=0;i<this.length;i++){
this[i].classList.add(str)
}
}
add.prototype.removeClass = function(str){
console.log(add)
console.log(this)
for(var i=0;i<this.length;i++){
this[i].classList.remove(str)
}
}
var $ = function(selector){
return new add(selector)
}
window.$ = $;
})()
```

DOM对象
```javascript
var el = {
offsetWidth:12,
_proto_: (HTMLDivElement)
title:'aa';
_proto_: HTMLElement
src:'xxx.png'
_proto_:Element
getAttribute:fn,
_proto_:Node
nodeName:"IMG",
_proto_
}
```

DOM集合
```javascript
var els = {
0:el,
1:el,
2:el,
3:el,
length:4,
_proto_:(并没有多少有价值的方法或属性)
}
```

jQuery对象
```javascript
var jQuery = {
0:div,
1:div,
2:div,
length:3,
_proto__:
addClass:fn,
removeClass:fn,
toggleClass:fn,
css:fn,
prop:fn
...
}
```

jQuery 是一个javascript库，
库，仓库，可以简单理解成一堆以某种方式组织起来的，方便，易用的函数的集合

jQuery库的优点
1、全面解决PC端的兼容性优点
2、语法精炼，性能好，插件库庞大，非常多。

jQuery版本号之间的区别
1.xx->1.12 支持IE6-8
2.0 彻底放弃了对IE<10的支持，转向移动端

$ 函数能接受的参数类型以及对应的返回值
* null jQuery
* 数组 对象
* 选择器
* html标签
* DOM对象
* DOM集合
* 函数

// javascript中构建一个对象的4种方式
// 1\. 字面量的形式
var obj = {
"a":12,
"b":234
}
// 根据字面量的形式创建的对象
// 原型就是 Obj.prototype 这个对象
// 功能性较少
// 2.构造函数
var obj2 = new Object()
obj2.a = 12;
//一般不用 太麻烦
// 3.利用 Obj.create() 方法
// 从一个已有的对象开始构建新的对象
var mao = {
zhuazi:4,
erduo:1,
nao:function(){
}
}
var bosimao = Object.create(mao);
bosimao.dianjiaojian = function(){
}
// 4\. 用new 关键字来构造对象
var mao = function(){
this.zhuazi = 4;
this.erduo = 1;
}
// 每个函数对象身上都有一个其他对象不具备的属性，叫做'prototype'
var bosimao = new mao()
// 1.构建一个空对象()
// 2.mao.call({}) 把mao那个函数作为这个空对象的临时方法调用了一次
// {zhuazi:4,erduo:1}
// 3.把mao那个函数对象身上的prototype那个属性拿来，作为自己原型链上的一条
// 4.返回最终的对象
##jquery中的方法

1.直接出现在是Query函数对象身上，是一些基础性质的工具函数
2.出现在jqery.fn函数对象的原型解放链上，用来批量或单个操作jquery集合中的dom对象

大部分方法重载很严重
```javascript
$('li').css('width'); //取出选中集合中第一个元素和宽度 +px
$('li').css('width',200); //设置集合中所有的元素的宽度为200px
$('li').css({width:200,height:300;border:'1px solid black'});
// 给选中的集合中所有的元素，加上对象中的所有样式
给集合中每一个的元素添加'width'这个属性，意味着jquery会对集合中的每一个元素调用用户传入的回调函数，一个是当前元素在集合中在集合中的位置，（0，1，2，3，4），另外一个是当前元素现在的'width'值
$('li').css('width',function(){
return Math.random()
})
var colors = ['red','blue','green']
$('li').css({
width:function(){return Math.random();}
height:function(){return Math.random();}
backgroundColor:function(i){return Math.colors(i);}
})

jQuery库设计理念
1.解决兼容性问题
2.让从页面中查找元素变得更多轻松
3.提供很多内置方法，使对dom集合的操作 变得更轻松

css

addClass 这些方法通过内置的遍历去操作每一个dom元素 jQuery 不希望我们在循环中使用这些内置方法
1.给集合中的每一个dom元素设置同样的值或行为
2.给集合中的每一个dom对象设置不同的值或行为
```javascript
var els = document.querySelectorAll('.item');
for(var i=0;i<els.length;i++){
$(els[i].addClass('aa'));
}
var colors = ['red','blue','green','yellow','pink','red','blue','green']
$('.main-content article').css('backgroundColor',function(i,w){
return colors[i]
})

$('li').attr('data-id')
$('li').attr('data-id','12')
$('li').attr('data-id',function(){return Math.random();})
$('li').attr({data-id:12,data-src:'img.png'})
$('li').attr({
data-id:function(){
return Math.random()}
data-src:'img.png'
})
以空格分开的字符串
```

节点的操作

*.clone() 拷贝后得到对象父元素的信息

on 添加事件的重载

$('.item').on('click',function(){
console.log(1)}
//一次绑定的多个事件 用一个处理函数
$('.item').on('click mouseleave mouseenter',clickHandler)

//一个事件绑定不同处理函数
var fn1 = function(){}
var fn2 = function(){}
var fn3 = function(){}
$('.item').on({'click':fn1,
'mouseleave':fn2,
'mouseenter':fn3})绑定3个不同的事件
})
//事件的委托方式
$('#ul').on('click','li',function(){

})
//事件的委托另外的方式
$('#ul').delegate('li','click',function(){

})
jQuery添加事件的注意事项

1\. on()的几种添加方式
* 一次绑定多个事件，用同一个处理函数
* 一次绑定多个事件，用不同的处理函数
2\. 事件委托的添加方式(只能使用 on 和 delegate 方法)
3\. mouseover mouseout 方法由于事件冒泡带来多次触发 一般我们使用 mouseenter 和 mouseleave 以及 hover (hover 是对 mouseenter 和
mouseleave)
4\. focus blur = focusin focusout 同上 后面的两个不会冒泡
5\. ready() 事件一般用 $(function(){})来代替
内部的处理方式是 document.addEventListener('DOMContentLoaded');如果文档结构(不包含图片，脚步等)已经加载完成，直接运行函数
如果还没有加载完成 把函数绑定到'DOMContentLoaded'
6\. trigger()会模仿浏览器触发事件(会冒泡) triggerHandler (不会冒泡)
7\. 所有事件添加函数的返回值要绑定事件的那个jQuery对象，所以可以继续链式调用
$('.item').click(function(){console.log(1).css()})

jQuery中的事件对象

继承 原生的事件对象 e.keyCode e.altKey e.target e.clientX

* e.currentTarget
* e.data

var xs = function(){
var dict = {x:1,y:2}
$($0).on('click',dict,function(e){
e.preventDefault();
console.log(e.data);
})
setInterval(function(){
dict = {x:Math.random(),y:Math.random()};
},1000)
}

$('li').on('click',{x:1,y:2},function(e){
console.log(e.data)
})
$('li').click({x:1,y:2},function(e){
console.log(e.data)
})

* e.namespace
$('li').on({'click':function(){consoel.log(1);},
{'click.lunbo':function(e){console.log(2,e.namepace);}}
)
$('li').trigger('click.lunbo')

var dict = {39:'xia',40:'you'}
$(document).on('click',dict,function(){
console.log(e.data)
})
$($0).on('click.lunbo',function(){
console.log(e.namespace)
});

停止当前队列的四种方式
.stop()不加参数是停止当前的进行的下一个
.stop(true)第一个是否清除队列
.stop(true,true) 不加就没效果 不清除队列 第一个是否清除队列 第二个是否到达最终状态
.finish 停止整个动画 到动画的最终状态 不带队列
.delay() 一个延迟
.clearQueue 清楚后续动画，但不影响当前

$.fx.off = true 关掉所有的动画
$.fx.interval = 13 默认每隔13毫秒执行一次动画

异步编程需要注意的问题：
1.理清代码的执行时间线;

### 同步
* 正常的函数
* 正常的赋值
* 正常的逻辑运算，普通运算
```

###
* 事件
* 动画（setInterval setTimeout）
* Ajax(发送网络请求) 都会把我们带入异步

get获取一些安全性低的东西

post 弄一些安全性高的东西

Math.max(3,4,5)

Math.max.call(null,3,4,5)
