---
title: input标签
date: 2018-03-07
tags: html
categories: HTML
---

--------------------------------------------------------------------------------

<!-- more -->

### 检测`input`内容值改变的事件

> 0. 常用写法
```js
   <!-- IE9 以下不支持 -->
   $(obj).on('input',function(){})
   <!-- IE支持 -->
   $(obj).on('propertychange',function(){})
```
> 1. onchange 
onchange 事件会在域的内容改变时触发。支持的标签input,textarea,select,keygen。
注意：在元素的值改变了且失去焦点时触发（两次的值一样不会触发）。
缺陷：通过js代码改变DOM的值不会触发，解决在js代码里改值了调用其change 的function() 或者调.change()方法。
```js
JS： 
<input type="text" id="cc" onchange="function()">
JQuery:
$("#cc").change(function(){});
```

> 2. onpropertychange
onpropertychange会实时触发，会在元素的属性改变时就触发事件。当元素disable=true时不会触发。
缺陷：只在IE 下支持，其他浏览器不支持，用oninput来解决。

> 3. oninput
oninput在`input`或`textarea`的值发生改变时触发，不需要等到元素失去焦点，是实时的。它是HTML5的事件，可用于检测文本类输入框的值。
缺陷：从脚本中修改值不会触发事件。从浏览器下拉提示框里选取值时不会触发。IE9 以下不支持，所以IE9以下可用onpropertychange 事件代替。
```js
JS：
<input type="text" oninput="functionName()">
JQuery: 
$("#cc").on('input propertychange',functionName);
```
> 4. addEventListener
addEventListener()用于向指定元素添加事件方法。使用removeEventListener()移除添加的事件方法。IE9以下不支持，用attachEvent代替。
```js
element.addEventListener(event, function, useCapture)

https://www.cnblogs.com/littlesummer/p/6428116.html
```


### input、textarea标签获取焦点时，光标出现在文本末尾。

> 文本框自动获取光标，但是光标总是出现在文本框最前面

```js

<!-- jq方法 -->
<!-- 获取焦点后光标在字符串后  -->
<!-- 其原理就是获得焦点后重新把自己复制粘帖一下  -->
var _val=$(obj).val(); 
$(obj).val("").focus().val(_val); 

<!-- js方法 -->

<input type="text" id="test" value="1234568790">
<input type="button" id="focus" value="编辑">

$('#focus').on('click', function() {
    var test = document.getElementById('test')
    test.focus();
    moveToEnd(test);    
});
function moveToEnd(el) {
    if (typeof el.selectionStart == "number") {
        el.selectionStart = el.selectionEnd = el.value.length;
    } else if (typeof el.createTextRange != "undefined") {
        el.focus();
        var range = el.createTextRange();
        range.collapse(false);
        range.select();
    }
} 

'selectionStart' 表示输入性元素selection起点的位置，'selectionEnd' 表示输入性元素selection末点的位置，都是 DOM 属性。

```

### input、textarea文本区域选中

```js
<!-- js方法 -->
<input type="text" id="test" value="1234568790">
<input type="button" id="focus" value="编辑">
$('#focus').on('click', function() {
    var test = document.getElementById('test');
    test.selectionStart = 2;
    test.selectionEnd   = 6;    
});


https://www.cnblogs.com/LY-leo/p/5796722.html
```

