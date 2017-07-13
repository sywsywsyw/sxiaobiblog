---
title: js截取url参数
date: 2016-09-27 11:30:40
tags: 
     - js
---

有个url如下：
http://www.baidu.com/index.php?app=shangpin&act=goodsindex&id=12
我们该如何获取from这个参数的值呢？在网上搜了下方法很简单，如下，第一种是通过正则，第二种通过切串放进数组的方式：

``` js
// 第一种正则 
function getQueryString(name) {  
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");  
    var r = window.location.search.substr(1).match(reg);  
    if (r != null) return unescape(r[2]); return null;  
}  
var app = getQueryString("app");  
console.log(app);

// 第二种字符串 
function GetRequest() {   
    var url = location.search; //获取url中"?"符后的字串   
    var theRequest = new Object();   
    if (url.indexOf("?") != -1) {  
        var str = url.substr(1);   
        strs = str.split("&");   
        for(var i = 0; i < strs.length; i ++) {  
            theRequest[strs[i].split("=")[0]]=unescape(strs[i].split("=")[1]);   
        }   
    }   
    return theRequest;   
}   
var req = GetRequest();   
var app = req['app'];  
console.log(app);

```