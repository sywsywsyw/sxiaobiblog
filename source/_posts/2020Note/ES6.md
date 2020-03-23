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

<!-- more -->

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

#### 3. 字符串
- 字符串模板
```javascript
let tt = 123;
let aa = `sxiaobi${tt}`;
console.log(aa);
// sxiaobi123
```
`支持嵌套html标签、支持简单运算`

- 字符串查找 includesOf  
```javascript
let findStr = 'sx';
let string = 'sxiaobi'
console.log(string.includes(findStr))
// true
// es5
console.log(string.indexOf(findStr)>-1)
```
- 查找字符串首 有没有  startsWith
```javascript
let findStr = 'sx';
let string = 'sxiaobi'
console.log(string.startsWith(findStr))
// true
```
- 判断字符串尾部是否存在 endsWith
```javascript
let findStr = 'bi';
let string = 'sxiaobi'
console.log(string.endsWith(findStr))
// true
```
- 字符串复制 repeat
```javascript
let str = '1';
let strRepeat = str.repeat(5);
console.log(strRepeat);
// 11111
```
4. 扩展运算符与剩余运算符
> 可以很好的为我们解决参数和对象数组未知情况下的编程
- 扩展运算符号
```javascript
function sxiaobi(...arg){
  console.log(arg[0])
  console.log(arg[1])
  console.log(arg[2])
}
sxiaobi(1,2,3)
// 1,2,3
```
扩展运算符的用处：
我们先用一个例子说明，我们声明两个数组arr1和arr2，然后我们把arr1赋值给arr2，然后我们改变arr2的值，你会发现arr1的值也改变了，因为我们这是对内存堆栈的引用，而不是真正的赋值。
```javascript
let arr1 = [1,2,3];
let arr2 = arr1;
arr2.push(4)
console.log(arr1)
// 1,2,3,4
```
```javascript
let arr1 = [1,2,3];
let arr2 = [...arr1];
arr2.push(4)
console.log(arr1)
// 1,2,3
```
rest运算符
```javascript
function sxiaobi(first,...arg){
    console.log(arg.length);
}
sxiaobi(0,1,2,3,4,5,6,7);
// 1,2,3,4,5,6,7
```
5. 数字的操作
- 判断是否是NaN `isNaN`
```javascript
console.log(Number.isNaN(1))
// false
console.log(Number.isNaN(NaN))
// true
```
- 判断是否是整数 `isInteger`
```javascript
console.log(Number.isInteger('a')) 
// false
console.log(Number.isInteger(1.1))
// false
console.log(Number.isInteger(1))
// true
```
- 整数转换 `parseInt` 和 浮点型转换 `parseFloat`
```js
let a='9.18';
console.log(Number.parseInt(a)); 
console.log(Number.parseFloat(a));
// 9
// 9.18
```
- 整数取值范围 2的53次方
```js
let a = Math.pow(2,53)-1;
console.log(a)
// 9007199254740991
```
- 最大安全整数 `MAX_SAFE_INTEGER`
```js
console.log(Number.MAX_SAFE_INTEGER)
// 9007199254740991
```
- 最小安全整数
```js
console.log(Number.MIN_SAFE_INTEGER)
// -9007199254740991
```
- 安全整数判断 `isSafeInteger( )`
```js
console.log(Number.isSafeInteger(11110))
// true
```
#### 6. 数组的方法
- Array.from() JOSN对象转数组
```js
let obj = {
   '0':'sun',
   '1':'xiao',
   '2':'bi',
   length:3
}
console.log(Array.from(obj))
// ['sun','xiao','bi']
```
- Array.of() 类数组对象转为数据，支持数字、字符串 
```js
console.log(Array.of(1,2,3,4))
// [1,2,3,4]
let str = 'sun,xiao,bi';
console.log(Array.of(str));
// ['sun','xiao','bi']
```
实例方法
- arr.find()   
```js

```
- 
```js

```
