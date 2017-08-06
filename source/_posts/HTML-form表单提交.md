---
title: form表单
date: 2017-07-27
tags:
categories: HTML
---

<!-- more -->
------

 $("form").submit(function(){
      var self = $(this);
       $.post(self.attr("action"), self.serialize(), success, "json");
      return false;
      function success(data){
        if( data.zt == 'ok' ){
          var index = top.layer.msg('数据提交中，请稍候',{icon: 16,time:false,shade:0.8});
          setTimeout(function(){
            top.layer.close(index);
            top.layer.msg("编辑成功！");
            layer.closeAll("iframe");
                  //刷新父页面
                  parent.location.reload();
           },2000);
        }
       }
      });

form 表单设置为 disabled="disabled"  就无法使用 表单提交  如果要设置只读请设置 readonly="readonly" 这样才可以提交



Readonly和Disabled是用在表单中的两个属性，它们都能够做到使用户不能够更改表单域中的内容。但是它们之间有着微小的差别，总结如下：
Readonly只针对input(text / password)和textarea有效，而disabled对于所有的表单元素都有效，包括select, radio, checkbox, button等。
但是表单元素在使用了disabled后，当我们将表单以POST或GET的方式提交的话，这个元素的值不会被传递出去，而readonly会将该值传递出去（这种情况出现在我们将某个表单中的textarea元素设置为disabled或readonly，但是submit button却是可以使用的）。