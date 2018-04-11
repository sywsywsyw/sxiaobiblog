---
title: js
date: 2018-03-07 21.58
tags: 笔记
categories: js
---

--------------------------------------------------------------------------------

<!-- more -->

## js删除数组某个元素

![转载](http://caibaojian.com/js-splice-element.html)
```
Array.prototype.remove = function(from, to) {
var rest = this.slice((to || from) + 1 || this.length);
this.length = from < 0 ? this.length + from : from;
return this.push.apply(this, rest);
};
// 移除数组中的第二项
array.remove(1);
// 移除数组中的倒数第二项
array.remove(-2);
// 移除数组中的第二项和第三项（从第二项开始，删除2个元素）
array.remove(1,2);
// 移除数组中的最后一项和倒数第二项（数组中的最后两项）
array.remove(-2,-1);
```
##  // 数组排序
```
Array.prototype.sortNumber = function (property) {
return function (a, b) {
var value1 = a[property];
var value2 = b[property];
return value1 - value2;
}
};
```
## js追加到数组第一个
```
var arr = [1,2];
arr.unshift('0');
```
## 判断数据是否在数组中
```
Array.prototype.isInArray = function (value) {
for (var i = 0; i < this.length; i++) {
if (value === this[i]) {
return true;
}
}
return false;
};
```

## 掉字符串中所有空格(包括中间空格, 需要设置第2个参数为: g)
![转载](http://www.jb51.net/article/109522.html)
```
String.prototype.Trim = function (is_global){
var result;
result = this.replace(/(^\s+)|(\s+$)/g, "");
if( is_global == '' || is_global == undefined ){
is_global = '';
}
if (is_global.toLowerCase() == "g") {
result = result.replace(/\s/g, "  ");
}
return result;
}
```

## 打印原型链
```
var cc = '1';
console.log(cc.__proto__)
```

### JS判断字符串是否为空或是否全为空格
```
var test = "   \n   ";
//var test = "      ";
if(test.match(/^\s+$/)){
    console.log("all space or \\n")
}
if(test.match(/^[ ]+$/)){
    console.log("all space")
}
if(test.match(/^[ ]*$/)){
    console.log("all space or empty")
}
if(test.match(/^\s*$/)){
    console.log("all space or \\n or empty")
}
```