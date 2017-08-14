---
title: canvas
date: 2017-08-14 22:29:51
tags:
categories:
---
------

解决用dom 建立小游戏会出现大量卡顿的现象
canvas 游戏必须 没法用样式设置 必须用内置属性设置width,height 不建议用css强制修改

<canvas id="canvas" width="" height=""></canvas>

<script>
var canvas = document.querySelector('#canvas')
var ctx = canvas.getContext('2d') 画笔 CanvasRenderingContext2D画布的渲染
console.dir(ctx)

ctx.beginPath(); 开始这是一只笔
ctx.moveTo(0,0); 开始坐标
ctx.lineTo(300,300); 结束坐标
ctx.stroke(); 直线
ctx.closPath();结束
</script>

#canvas 常用API

##形状

>矩形
ctx.fillRect(x,y,widht,height); 填充矩形
ctx.strokeRect(x,y,widht,height); 框线矩形

ctx.clearRect(); 清除矩形区域 绘制上的元素无法更改
>圆形
ctx.arc(x,y,半径，开始角度,布尔值); 圆
<!-- ctx.arcTo(); 圆弧 -->

>线
ctx.beginPath(); 开始一个路径
ctx.moveTo(); 移动画笔到某点
ctx.lineTo(); 让路径中拥有一条到某点的线（不会直接绘制）
ctx.rect(x,y,widht,height); 让路径拥有一个矩形（不会直接绘制）
ctx.fill(); 填充当前路径
ctx.stroke(); 描边当前路径
ctx.closePath(); 结束一个路径

ctx.quadraticCurveTo(cp1x, cp1y, x, y)
二次贝塞尔
ctx.bezierCurveTo(cp1x.cp1y,cp2x,cp2y,x,y)
三次贝塞尔

## 样式

ctx.fillStyle = "rgb(200,0,0)";
ctx.strokeStyle='red';
ctx.globalAlpha = 0.2; 透明度

线型 Line stylesEDIT
可以通过一系列属性来设置线的样式。

lineWidth = value
设置线条宽度。
lineCap = type
设置线条末端样式。
lineJoin = type
设定线条与线条间接合处的样式。
miterLimit = value
限制当两条线相交时交接处最大长度；所谓交接处长度（斜接长度）是指线条交接处内角顶点到外角顶点的长度。
getLineDash()
返回一个包含当前虚线样式，长度为非负偶数的数组。
setLineDash(segments)
设置当前虚线样式。
lineDashOffset = value
设置虚线样式的起始偏移量。

## 位移(挪动画布)

ctx.save() 保存快照 只能保存画布状态不能保存东西（包含画笔）
ctx.restore() 引用以前的

ctx.translate(x,y)
ctx.rotate((Math.PI/180)*30)
ctx.scale();

//清除画面的两种方式
document.onclick = function(){
canvas.width = canvas.height = 600;
ctx.clearRect(0,0,600,600)
}

获得时间
var now = new Date()
毫秒
var m = now.getMilliseconds();
秒
var s = now.getSeconds()
分
var f = now.getMinutes()
时
var h = now.getHours()

<img>

window.onload = function(){
var img = document.querySelector('#img');
var xxx =ctx.createPattern(img,'no-repeat');
ctx.fillStyle = xxx;
}

var img = new Image();
img.src = 'a.png';
img.onload = function(){
var xxx =ctx.createPattern(img,'no-repeat');
ctx.fillStyle = xxx;
}