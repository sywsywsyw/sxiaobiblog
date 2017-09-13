---
title: ajax原理
date: 2016-07-18
tags: ajax
categories: AJAX
---
------

#### AJAX 是与服务器交换数据并更新部分网页的艺术，是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。

<!-- more -->

##### 创建 XMLHttpRequest 对象

```js
var obj = new XMLHttpRequest();
```
##### 向服务器发送请求

> 如需将请求发送到服务器，我们使用 XMLHttpRequest 对象的 open() 和 send() 方法：

```js
xmlhttp.open("GET","test1.txt",true);
xmlhttp.send();
```
| 方法        | 描述    |
| :----:      | :----:  |
| open(method,url,async)        | 规定请求的类型、URL 以及是否异步处理请求。</br> method：请求的类型；GET 或 POST </br>url：文件在服务器上的位置 </br>async：true（异步）或 false（同步）     |
| send(string)        | 	将请求发送到服务器。</br> string：仅用于 POST 请求      |

###### open需要三个参数

* 第一个参数定义发送请求所使用的方法（GET 还是 POST）

> GET 还是 POST？
> 与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。
> 然而，在以下情况中，请使用 POST 请求：
> * 无法使用缓存文件（更新服务器上的文件或数据库）
> * 向服务器发送大量数据（POST 没有数据量限制）
> * 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠


* 第二个参数规定服务器端脚本的 URL(该文件可以是任何类型的文件，比如 .txt 和 .xml，或者服务器脚本文件，比如 .asp 和 .php （在传回响应之前，能够在服务器上执行任务）)。

* 第三个参数规定应当对请求进行异步地处理(true（异步）或 false（同步）)。

> 异步 - True 或 False？

> 对于 web 开发人员来说，发送异步请求是一个巨大的进步。很多在服务器执行的任务都相当费时。AJAX 出现之前，这可能会引起应用程序挂起或停止。

> 我们不推荐使用 async=false，但是对于一些小型的请求，也是可以的。
请记住，JavaScript 会等到服务器响应就绪才继续执行。如果服务器繁忙或缓慢，应用程序会挂起或停止。

###### send() 方法可将请求送往服务器。

###### onreadystatechange 属性存有处理服务器响应的函数。

###### readyState 属性存有服务器响应的状态信息。每当 readyState 改变时，onreadystatechange 函数就会被执行。

> readyState状态值
>> * 0: 请求未初始化
>> * 1: 服务器连接已建立
>> * 2: 请求已接收
>> * 3: 请求处理中
>> * 4: 请求已完成，且响应已就绪

###### status状态

> 200: "OK"
> 404: 未找到页面

## 原生ajax写法

```js
var Ajax={
    get: function (url,fn){
        var obj=new XMLHttpRequest();  // XMLHttpRequest对象用于在后台与服务器交换数据          
        obj.open('GET',url,true);
        obj.onreadystatechange=function(){
            if (obj.readyState == 4 && obj.status == 200 || obj.status == 304) { // readyState==4说明请求已完成
                fn.call(this, obj.responseText);  //从服务器获得数据
            }
        };
        obj.send(null);
    },
    post: function (url, data, fn) {
        var obj = new XMLHttpRequest();
        obj.open("POST", url, true);
        obj.setRequestHeader("Content-type", "application/x-www-form-urlencoded"); // 发送信息至服务器时内容编码类型
        obj.onreadystatechange = function () {
            if (obj.readyState == 4 && (obj.status == 200 || obj.status == 304)) {  // 304未修改
                fn.call(this, obj.responseText);
            }
        };
        obj.send(data);
    }
}
```

http://www.w3school.com.cn/ajax/index.asp

# Ajax中同步和异步的概念
 var xhr=new XMLHttpRequest()
 xhr.open('get','/robot.txt',true)
 xhr.send()
 document.body.innerHTML +=xhr.response;



 var xhr=new XMLHttpRequest();  
 xhr.addEventListener('readystatechange',function(){  //检测到状态改变
            // console.log(xhr.response)
            if( this.readyState !== 4){  状态改变
                return;
            }
            if( this.status === 200 || this.status === 304){
                document.body.innerHTML += xhr.response
            }
         })
        xhr.open('get','/robot.txt',true);
        xhr.send();
 x 随意  ML  标记语言  HTTP 超文本传输协议  Request 请求

执行队列

异步

可执行 待执行
