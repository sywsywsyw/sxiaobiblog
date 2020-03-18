---
title: ES6笔记
date: 2020年3月18日 21点21分
tags: note
categories: 2020Note
---


### 1. var、const、let的区别
- var 全局变量
- let  局部变量
- const 常量 一般用于属性名，用于从常量命名开始的那一刻就不想让改变的属性名。

### 2. 变量的解构赋值
1. 数组解构
- 左右两边需要解构相同
```javascript
let [a,b,c] = [1,2,3];
console.log(a,b,c)
// 1,2,3
let [a,[b,c],d]=[1,2,4];
console.log(a,b,c,d)
// 报错 Uncaught TypeError: [1,2,4] is not iterable at <anonymous>:1:17
```
- 默认赋值的写法
```javascript
let [a=2,b=3,c=5] = [1];
console.log(a,b,c)
// 1,3,5
```
2. 对象解构
- 根据属性名进行解构
```javascript
let {a,b,c} = {a:'sxiaobi',b:25};
console.log(a,b,c)
// sxiaobi 25 undefined
```
- 默认赋值写法
```javascript
let {a,b,c=10} = {a:'sxiaobi',b:25};
console.log(a,b,c)
// sxiaobi 25 10
```
- 如果变量先声明，再赋值需要使用`()`包裹起来
```javascript
// success 
let aa;
({aa} = {aa:11});
console.log(aa)
// 11
// error
let aa;
{aa} = {aa:11};
console.log(aa)
// Uncaught SyntaxError: Unexpected token =
```
- 字符串解构
```javascript
let [a,b,c,d,e,f,g] = 'sxiaobi';
console.log(a,b,c,d,e,f,g)
// s x i a o b i
```

> 何时用单引号，何时用双引号??？
> 虽然在JavaScript当中，双引号和单引号都可以表示字符串, 为了避免混乱，我们建议在HTML中使用双引号，在JavaScript中使用单引号，但为了兼容各个浏览器，也为了解析时不会出错，定义JSON对象时，最好使用双引号
