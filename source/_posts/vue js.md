---
title: vue问题
date: 2018-03-07 21.58
tags: 笔记
categories: vue
---

--------------------------------------------------------------------------------

<!-- more -->

## js删除数组某个元素

![转载](http://caibaojian.com/js-splice-element.html)
```
// Array Remove - By John Resig (MIT Licensed)
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