---
title: form
date: 2016-01-26
tags:
categories: HTML
---

<!-- more -->
------

* 1、 阻止掉form表单提交改用ajax。（如果有图片还是无法使用正常的ajax提交，请去ajax常见问题寻找答案）
```js
$("form").submit(function(){
      var self = $(this);
      $.post(self.attr("action"), self.serialize(), success, "json");
      return false;
      function success(data){
         console.log(data);   
      }
});
```
* 2、form 表单一个页面可以存在多个但是无法嵌套在一起使用，如果嵌套则被嵌套的form表单不会输出到页面中来。

* 3、form 表单设置为 disabled="disabled"则这个参数无法提交给后台，  如果要设置只读然后提交请使用 readonly="readonly"。

> readonly和disabled是用在表单中的两个属性，它们都能够做到使用户不能够更改表单域中的内容。但是它们之间有着微小的差别，总结如下：
>> Readonly只针对input(text / password)和textarea有效，而disabled对于所有的表单元素都有效，包括select, radio, checkbox, button等。
但是表单元素在使用了disabled后，当我们将表单以POST或GET的方式提交的话，这个元素的值不会被传递出去，而readonly会将该值传递出去（这种情况出现在我们将某个表单中的textarea元素设置为disabled或readonly，但是submit button却是可以使用的）。

* 4、