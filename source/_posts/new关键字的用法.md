---
layout: w
title: new关键字的用法
date: 2017-08-15 08:52:42
tags:
---
<!-- more -->

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
	<script>
		// javascript中构建一个对象的4种方式
		// 1. 字面量的形式
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
        // 4. 用new 关键字来构造对象
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
	</script>
</body>
</html>