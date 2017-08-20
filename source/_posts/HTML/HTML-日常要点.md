---
title: 日常笔记
date: 2016-01-25
tags:
categories: HTML
---
------

<!-- more -->

## nodesass

node-sass -w index.scss index.css --output-style expanded

## CSS

1. 字体换行
```css
word-break: break-all;  //包括数字
word-break: break-word; //不包括数字
```
2.  下划线
```css
text-decoration: line-through;
```
3. 控制文字在一行并且出现...
```css
div{
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```
4. 控制文字在多行显示并且出现...
```css
div{
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
  word-break: break-all;
  text-overflow: ellipsis;
}
```
5. 去除重复的线条
```css
.nolayer {
  margin-bottom: -1px;
}
```
6. 不知道盒子的宽高怎么让他垂直居中
```css
父元素{
text-align:center
}
元素本身{
	vertical-align:middle
     display:inline-block
}
元素本身::after{
vertical-align:middle
display:inline-block
height:100%
content:''
}
```
7. 清除浮动的要点：
```css
.outer {zoom:1;}  /*==for IE6/7 Maxthon2==*/
.outer :after {clear:both;content:'.';display:block;width: 0;height: 0;visibility:hidden;}
::after{
content:"";
clear:both;
display:table;
}
其中clear:both;指清除所有浮动；content: '.'; display:block;对于FF/chrome/opera/IE8不能缺少，其中content（）可以取值也可以为空。visibility:hidden;的作用是允许浏览器渲染它，但是不显示出来，这样才能实现清除浮动。
```
8. 垂直居中
```css
 .center {
        position: absolute;
        top: 50%;
        left: 50%;
        -ms-transform: translate(-50%,-50%);
        -moz-transform: translate(-50%,-50%);
        -o-transform: translate(-50%,-50%);
        transform: translate(-50%,-50%);
    }
```
9. 去除input type=number的上下箭头样式
```css
在chrome下：
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button{
    -webkit-appearance: none !important;
    margin: 0;
}
Firefox下：
input[type="number"]{-moz-appearance:textfield;}
```

10. 一个1920*900的大图，在1024*768的分辨率只能显示一部分，希望仍居中显示
```css
width: 100%;
background-position: 50% 50%;
```

11. 剪裁图像：
```css
img{
  position:absolute;
  clip:rect(0px,60px,200px,0px);
}
```
12. 实现div两端对齐
```css
div{
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: justify;
  -webkit-justify-content: space-between;
  -ms-flex-pack: justify;
  justify-content: space-between;
}
```
13. 如何透过CSS控制文章内的标点符号位置
```css
body{
  text-align: justify;  /*两端对齐*/
  word-break: break-all;  /*控制标点不在第一个字显示*/
}
```
14. 滚动条样式修改
```css
*::-webkit-scrollbar-track
{
  background-color: white;
}
*::-webkit-scrollbar
{
  width: 0;
  background-color: rgba(0,0,0,0.3);
}
*::-webkit-scrollbar-thumb
{
  background-color: #e4e4e4;
}
```
15. 图片居中
```css
如果是正方形
    width: 70px;
    height: 70px;
    overflow: hidden;
    border-radius: 50%;
img width:100%;height:100%;
适用于图片为长方形 使用
父元素
position:relative;
overflow:hidden;
img
display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    <!-- height: 100%; -->
    -ms-transform: translate(-50%,-50%);
    -moz-transform: translate(-50%,-50%);
    -o-transform: translate(-50%,-50%);
    transform: translate(-50%,-50%);
```


## JS、JQ
1. https转为http
```js
var targetProtocol = "http:";
if (window.location.protocol != targetProtocol)
window.location.href = targetProtocol +
window.location.href.substring(window.location.protocol.length)
```

2. 不同HTML层都被使用不同的颜色添加了一个高亮的边框
```js
转载自<http://buluo.qq.com/p/detail.html?bid=314687&pid=3951568-1476250690>
调试高亮
[].forEach.call($$("*"),function(a){a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16) })
```
3. 两种ajax请求方式 (已放入别的文章)

4. 测试一段代码的执行时间
```js
   console.timeEnd('aa')
   console.time('aa')
```

5. 判断是苹果手机还是andorid手机  进行控制"关注按钮"的位置 解决安卓手机视频最优先
```js
 var ua = navigator.userAgent.toLowerCase();
 if(/iphone|ipad|ipod/.test(ua)){
      alert("iphone");
    }else if(/android/.test(ua)){
      alert("android");
     $('.FBfollow').addClass('android')
 };
```

6. //日历计算  输出2017-06-01 - 2018-12-01的值
```js
  date=new Date();
  var year=date.getFullYear();
  var month=date.getMonth()+1;
  function cc(){
  	for(var i=year; i<2099; i++){
  		if(i===year){
  			var j=month;
  		}else{
  			var j=1;
  		}
  		for( j; j<13;j++){
  			if( $('.dataselect li').length < 13){
  				$('.dataselect').append('<li>'+i+'-'+j+'</li>')
  			}
  		}
  	}
  }
 cc();
```
7. // js判断滚动条是否停止状态
```js
//根据上一秒的值去对比当前时间的scrollTop如果没变则设置为0
var pl_Top = 0; // 上次滚动条到顶部的距离  
var interval = null; // 定时器  
// 设置评论区的高度每隔1秒设置scollTop为0
$('.pilun').scroll(function(){
    if(interval == null) {  // 未发起时，启动定时器，1秒1执行  
      interval = setInterval('pl_Topjs()',1000)
    }  
})
function pl_Topjs(){
    if( $('.pilun').scrollTop() == pl_Top) {
        clearInterval(interval)
        $('.pilun').scrollTop(0)
        interval = null
    } else {
      pl_Top = $('.pilun').scrollTop()
    }
}
```
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
   <html xmlns="http://www.w3.org/1999/xhtml">
   <head>
     <meta http-equiv="content-type" content="text/html;charset=utf-8">
     <title>下拉滚动条滚到底部了吗？</title>
     <script src="http://cdn.bootcss.com/jquery/2.2.3/jquery.min.js"></script>
     <script language="javascript">
     $(document).ready(function (){
       var nScrollHight = 0; //滚动距离总长(注意不是滚动条的长度)
       var nScrollTop = 0;   //滚动到的当前位置
       var nDivHight = $("#div1").height();
       $("#div1").scroll(function(){
         nScrollHight = $(this)[0].scrollHeight;
         nScrollTop = $(this)[0].scrollTop;
　　　　　var paddingBottom = parseInt( $(this).css('padding-bottom') ),paddingTop = parseInt( $(this).css('padding-top') );
         if(nScrollTop + paddingBottom + paddingTop + nDivHight >= nScrollHight)
           alert("滚动条到底部了");
         });
     });
     </script>
   <body>
   <div id="div1" style="overflow-y:auto; overflow-x:hidden; height:500px;">
     <div style="background-color:#ccc; height:750px;">IE 和 FF 下测试通过</div>
   </div>
   </body>
   </html>
```

8. 判断网络连接
```js
   if(window.navigator.onLine==true) {　
     alert("首次 -- 已连接");
   }else {　
     alert("首次 -- 未连接");
   }
window.addEventListener("online", online, false);
window.addEventListener("offline", offline, false);
function online() {  alert("重新连接");  }
function offline() {  alert("连接断开");  }
```
9. 传一个对象给php
var student = { 'info': [] };
$("input[name='student']:checked").each(function (i, n) {
    student['info'].push(n.value);
});
console.log(student)

10. 原生提示框
```js
    if (confirm("确定删除视频吗 ?")){  //给出一个警告框，点确定时就执行里面的代码
      add_attr('del',vid,src)
    }
```
```html
<a href="
javascript:if(confirm('确定删除视频吗'))window.location = 'index.php?app=gcategory;"></a>
```

11. 根据窗口大小调整视图
```js
$(window).resize(function () {})
```
12. 用 Unicode字符范围判断字节
```js
以下方法是用于统计输入字符串的长度，如果是汉字，则字符串长度加2 ；否则字符串长度加1。
function chkstrlen(str){
	console.log(str)
	var strlen = 0;
	for(var i = 0;i < str.length; i++){
        if(str.charCodeAt(i) > 255) {
        //如果是汉字，则字符串长度加2
        	strlen += 2;
        } else {  
        	strlen++;
    　　}
    }
    console.log(strlen)
    return strlen;
}
var cc ='1111你好444'
chkstrlen(cc)
```
13. 是否是图片
```js
function checkPhoto(str){
     console.log(str)
     var type="";
     if( str !=''){
         type= str.match(/^(.*)(\.)(.{1,8})$/)[3];
         type= type.toUpperCase();
     }
     if( type!="JPEG"   &&   type!="PNG"   &&   type!="JPG"   &&   type!="GIF"){
      zeroModal.error('上传图片类型错误');
      return false;
    }
}
```
14. js获取当前日期时间 转为"yyyy-MM-dd HH:MM:SS"
```js
function getNowFormatDate() {
    var date = new Date();
    var seperator1 = "-";
    var seperator2 = ":";
    var month = date.getMonth() + 1;
    var strDate = date.getDate();
    if (month >= 1 && month <= 9) {
        month = "0" + month;
    }
    if (strDate >= 0 && strDate <= 9) {
        strDate = "0" + strDate;
    }
    var currentdate = date.getFullYear() + seperator1 + month + seperator1 + strDate
            + " " + date.getHours() + seperator2 + date.getMinutes()
            + seperator2 + date.getSeconds();
    return currentdate;
}
```

16. 监控回车发送消息
```html
//控制输入框 textarea  回车不换行
<textarea class="test" id="test"></textarea>  
<script type="text/javascript">  
  // var test= document.getElementById("test");
  var test1 = $('.test').get(0);
  console.log(test,test1)
test1.onkeydown = function(e){  
    send(e);  
  }
  // test.onkeydown = function(e){  
  //   send(e);  
  // }  
    function send(e){  
    var code;
    if (!e) var  e = window.event;  
    if (e.keyCode) code = e.keyCode;  
    else if (e.which) code = e.which;  
    if(code==13 && window.event){  
        e.returnValue = false;  
    }else if(code==13){  
        e.preventDefault();  
    }  
}  
 </script>
```

17. 网页调用qq
```html
http://wpa.qq.com/msgrd?v=3&uin=3314523834&site=qq&menu=yes
```

## HTML

1. 取消浏览器拖动的蓝色选择区
```html
     <body onselectstart="return false"></body>
    <!-- 别的标签也可以使用 -->
```


3. 在进行CSS网页布局的时候，我们经遇到刷新要保留表单里内容的时候，习惯的做法使用cookie，但是那样做实在是很麻烦，css中的behavior就为我们很好的解决了这个问题。今天就向大家介绍CSS属性behavior的语法。只兼容IE 哈哈 是不是很气愤呢

4. 手机号电话号
```html
<input type="tel" placeholder="手机号或固定电话" name="tel" pattern="[0-9]*" maxlength="11" class="adphone_tel srfonchang">
```

5. 表格
```html
<table border="1">
  <thead>
    <tr>
      <th>Month</th>
      <th>Savings</th>
    </tr>
  </thead>

  <tfoot>
    <tr>
      <td>Sum</td>
      <td>$180</td>
    </tr>
  </tfoot>

  <tbody>
    <tr>
      <td>January</td>
      <td>$100</td>
    </tr>
    <tr>
      <td>February</td>
      <td>$80</td>
    </tr>
  </tbody>
</table>
```

6. 禁止浏览器记录 文本框之前输入过的内容 autocomplete="off"
```html
<input type="text" autocomplete="off">
```

7. HTML给视频截图

> 一定要在服务器环境下运行否则会出现跨域报错

```html
<video id="video" controls="controls">  
  <source src="（4）金沙漂流直播_20170715142115_5475_超清.mp4" />  
</video>
<button id="capture">截图</button>
<div id="output"></div>
```

```javascript
(function() {  
  var video, $output;  
  var scale = 0.25;  //截图的大小
  var initialize = function() {   //定义一些属性
    $output = $("#output");  
    video = $("#video").get(0);  
    $("#capture").click(captureImage);
  };  
  function captureImage() {  
    var canvas = document.createElement("canvas");  
    canvas.width = video.videoWidth * scale;  
    canvas.height = video.videoHeight * scale;  
    console.log(video.videoHeight)
    canvas.getContext('2d').drawImage(video, 0, 0, canvas.width, canvas.height);  
    var img = document.createElement("img");  
    img.src= canvas.toDataURL();   //截图的方法
    $output.prepend(img);  
  };  
  $(initialize);        
}())
```
7. 怎么打出来&copy;
```js
<a href="">&copy;</a>
```
