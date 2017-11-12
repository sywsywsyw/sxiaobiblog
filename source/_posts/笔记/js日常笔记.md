---
title: js日常笔记
date: 2017-09-14 22:49:51
tags: 笔记
categories: JS
---
------

<!-- more -->
# JS、JQ

1.https转为http

  ```javascript
  var targetProtocol = "http:";
  if (window.location.protocol != targetProtocol)
  window.location.href = targetProtocol +
  window.location.href.substring(window.location.protocol.length)
  ```

2.不同HTML层都被使用不同的颜色添加了一个高亮的边框

  ```javascript
  转载自<http://buluo.qq.com/p/detail.html?bid=314687&pid=3951568-1476250690>
  调试高亮
  [].forEach.call($$("*"),function(a){a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16) })
  ```

3.两种ajax请求方式 (已放入别的文章)

4.测试一段代码的执行时间

  ```javascript
  console.timeEnd('aa')
  console.time('aa')
  ```

5.判断是ios手机还是andorid手机 进行控制"关注按钮"的位置 解决安卓手机视频最优先

  ```javascript
  var ua = navigator.userAgent.toLowerCase();
  if(/iphone|ipad|ipod/.test(ua)){
  alert("iphone");
  }else if(/android/.test(ua)){
  alert("android");
  $('.FBfollow').addClass('android')
  };
  ```

6.日历计算 输出2017-06-01 - 2018-12-01的值

  ```javascript
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

7.// js判断滚动条是否停止状态

  ```javascript
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

8.判断网络连接

  ```javascript
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

9.传一个对象给php var student = { 'info': [] }; $("input[name='student']:checked").each(function (i, n) { student['info'].push(n.value); }); console.log(student)

10.原生提示框

  ```javascript
  if (confirm("确定删除视频吗 ?")){  //给出一个警告框，点确定时就执行里面的代码
  add_attr('del',vid,src)
  }
  ```

  ```html
  <a href="
  javascript:if(confirm('确定删除视频吗'))window.location = 'index.php?app=gcategory;"></a>
  ```

11.根据窗口大小调整视图

  ```javascript
  $(window).resize(function () {})
  ```

12.用 Unicode字符范围判断字节

  ```javascript
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

13.是否是图片

  ```javascript
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

14.js获取当前日期时间 转为"yyyy-MM-dd HH:MM:SS"

  ```javascript
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

15.监控回车发送消息

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

16.网页调用qq

  ```html
  http://wpa.qq.com/msgrd?v=3&uin=3314523834&site=qq&menu=yes
  ```

17.textarea中屏蔽回车默认换行
多行文本框textarea.清除默认回车事件
```js
<textarea id= "test"></textarea>  
<script type="text/javascript">  
  var test= document.getElementById("test");  
 test.onkeydown = function(e){  
    send(e);  
 }  
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

18.页面刷新
```js
window.location.reload()刷新当前页面. 
parent.location.reload()刷新父亲对象（用于框架） 
opener.location.reload()刷新父窗口对象（用于单开窗口） 
top.location.reload()刷新最顶端对象（用于多开窗口）
```

20.关于日期
不明白 为什么不用getDay表示日子  getweek表示星期哦
```js
var 日期 = new Date();
var 年 = 日期.getFullYear();
var 月 = 日期.getMonth();
var 日 = 日期.getDate();
var 星期 = 日期.getDay();  
var 小时 = 日期.getHours();
var 分 = 日期.getSeconds();
var 毫秒 = 日期.getMillSeconds();
Date()  返回当日的日期和时间。
getDate() 从 Date 对象返回一个月中的某一天 (1 ~ 31)。
getDay()  从 Date 对象返回一周中的某一天 (0 ~ 6)。
getMonth()  从 Date 对象返回月份 (0 ~ 11)。
getFullYear() 从 Date 对象以四位数字返回年份。
getYear() 请使用 getFullYear() 方法代替。
getHours()  返回 Date 对象的小时 (0 ~ 23)。
getMinutes()  返回 Date 对象的分钟 (0 ~ 59)。
getSeconds()  返回 Date 对象的秒数 (0 ~ 59)。
getMilliseconds() 返回 Date 对象的毫秒(0 ~ 999)。
getTime() 返回 1970 年 1 月 1 日至今的毫秒数。
getTimezoneOffset() 返回本地时间与格林威治标准时间 (GMT) 的分钟差。
getUTCDate()  根据世界时从 Date 对象返回月中的一天 (1 ~ 31)。
getUTCDay() 根据世界时从 Date 对象返回周中的一天 (0 ~ 6)。
getUTCMonth() 根据世界时从 Date 对象返回月份 (0 ~ 11)。
getUTCFullYear()  根据世界时从 Date 对象返回四位数的年份。
getUTCHours() 根据世界时返回 Date 对象的小时 (0 ~ 23)。
getUTCMinutes() 根据世界时返回 Date 对象的分钟 (0 ~ 59)。
getUTCSeconds() 根据世界时返回 Date 对象的秒钟 (0 ~ 59)。
getUTCMilliseconds()  根据世界时返回 Date 对象的毫秒(0 ~ 999)。
parse() 返回1970年1月1日午夜到指定日期（字符串）的毫秒数。
setDate() 设置 Date 对象中月的某一天 (1 ~ 31)。
setMonth()  设置 Date 对象中月份 (0 ~ 11)。
setFullYear() 设置 Date 对象中的年份（四位数字）。
setYear() 请使用 setFullYear() 方法代替。
setHours()  设置 Date 对象中的小时 (0 ~ 23)。
setMinutes()  设置 Date 对象中的分钟 (0 ~ 59)。
setSeconds()  设置 Date 对象中的秒钟 (0 ~ 59)。
setMilliseconds() 设置 Date 对象中的毫秒 (0 ~ 999)。
setTime() 以毫秒设置 Date 对象。
setUTCDate()  根据世界时设置 Date 对象中月份的一天 (1 ~ 31)。
setUTCMonth() 根据世界时设置 Date 对象中的月份 (0 ~ 11)。
setUTCFullYear()  根据世界时设置 Date 对象中的年份（四位数字）。
setUTCHours() 根据世界时设置 Date 对象中的小时 (0 ~ 23)。
setUTCMinutes() 根据世界时设置 Date 对象中的分钟 (0 ~ 59)。
setUTCSeconds() 根据世界时设置 Date 对象中的秒钟 (0 ~ 59)。
setUTCMilliseconds()  根据世界时设置 Date 对象中的毫秒 (0 ~ 999)。
toSource()  返回该对象的源代码。
toString()  把 Date 对象转换为字符串。
toTimeString()  把 Date 对象的时间部分转换为字符串。
toDateString()  把 Date 对象的日期部分转换为字符串。
toGMTString() 请使用 toUTCString() 方法代替。
toUTCString() 根据世界时，把 Date 对象转换为字符串。
toLocaleString()  根据本地时间格式，把 Date 对象转换为字符串。
toLocaleTimeString()  根据本地时间格式，把 Date 对象的时间部分转换为字符串。
toLocaleDateString()  根据本地时间格式，把 Date 对象的日期部分转换为字符串。
UTC() 根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。
valueOf() 返回 Date 对象的原始值。
```