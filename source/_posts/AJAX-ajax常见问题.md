---
title: ajax常见问题
date: 2017-07-20
tags:
categories: AJAX
---
------

<!-- more -->

## 怎么使用ajax上传图片

* 建议图片一定通过异步上传。就是单独开一个接口。避免上传图片
```js
//创建FormData对象
var data = new FormData();
//为FormData对象添加数据
var file = $('#inputfile')[0].files[0];
data.append('upload_file', file); //第一个参数为参数名，第二个为参数值
$.ajax({
    url: "http://www.baidu.com", //请求的url地址
    type: "POST", //请求方式 GET
    data: data, //参数值
    cache: false,
    contentType: false,    //不可缺
    processData: false,    //不可缺
    beforeSend: function () {//请求前的处理
        alert("正在加载");
    },
    success: function (req) { //请求成功时处理
        console.log(req);
    },
    complete: function () { //请求完成的处理
        alert("修改完成");
    },
    error: function (req) { //请求出错处理
        console.log(req);
    }
});
```


## ajax请求返回状态为200但还是进入error事件

* 最近遇到一个问题，发送一个ajax请求，请求成功了，并且放回状态为200，但是就是不进入success事件，添加error事件竟进入了error事件。
```js
$.ajax({  
    url:$WEB_ROOT_PATH+"/dataLevel/dataLevelCtrl.htm?BLHMI=findBasicDataLevel",  
    type:"post",  
    dataType:"json",  
    async:false,  
    success:function(data){  
        var dataScore = data;  
    },error:function(){  
        alert("出错啦！");  
    }  
});  
```
* 出错原因：dataType:"json",而后台返回的数据不符合json规范。
解决方法：先将dataType设置为text，这样就可以进入success方法了，查看data数据究竟是什么。
我的data为：｛"success":success｝，可以看出第二个success没有引号包裹，不符合json规范，故而不能转换为json对象。
之后的解决方法就很好办了。一种是修改后台返回值，二种是直接解析text返回的值。

## [PHP Ajax 跨域问题最佳解决方案](http://www.runoob.com/w3cnote/php-ajax-cross-border.html)

* 本文通过设置**Access-Control-Allow-Origin**来实现跨域。
例如：客户端的域名是client.runoob.com，而请求的域名是server.runoob.com。
如果直接使用ajax访问，会有以下错误：
XMLHttpRequest cannot load http://server.runoob.com/server.php. No 'Access-Control-Allow-Origin' header is present on the requested resource.Origin 'http://client.runoob.com' is therefore not allowed access.
## 1、允许单个域名访问
指定某域名（http://client.runoob.com）跨域访问，则只需在http://server.runoob.com/server.php文件头部添加如下代码：
header('Access-Control-Allow-Origin:http://client.runoob.com');
## 2、允许多个域名访问
指定多个域名（http://client1.runoob.com、http://client2.runoob.com等）跨域访问，则只需在http://server.runoob.com/server.php文件头部添加如下代码：
$origin = isset($_SERVER['HTTP_ORIGIN'])? $_SERVER['HTTP_ORIGIN'] : ''; $allow_origin = array(  
    'http://client1.runoob.com',  
    'http://client2.runoob.com'  
);  
if(in_array($origin, $allow_origin)){ 
     header('Access-Control-Allow-Origin:'.$origin);      
} 
## 3、允许所有域名访问
允许所有域名访问则只需在http://server.runoob.com/server.php文件头部添加如下代码：
header('Access-Control-Allow-Origin:*');