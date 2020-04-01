---
title: js日常笔记
date: 2018-03-01
categories: JS/JQ
---

--------------------------------------------------------------------------------

<!-- more -->

```
<meta name="viewport" content="width=device-width,initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no,minimal-ui">

注意：viewport 后面加上 minimal-ui 在safri 体现效果

<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait">

<!-- UC强制全屏 --> 
<meta name="full-screen" content="yes">

<!-- UC应用模式 --> 
<meta name="browsermode" content="application">

<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait">

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true">

<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app">
```

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

5.判断是iOS手机还是andorid手机 进行控制"关注按钮"的位置 解决安卓手机视频最优先

```javascript
  var ua = navigator.userAgent.toLowerCase();
  if(/iphone|ipad|ipod/.test(ua)){
     alert("iphone");
  }else if(/android/.test(ua)){
    alert("android");
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

9.传一个对象给php
```javascript
var student = {
    'info': []
};
$("input[name='student']:checked").each(function (i, n) {
    student['info'].push(n.value);
});
console.log(student)
```
10.原生提示框 // 判断刷新页面

```javascript
  if (confirm("确定删除视频吗 ?")){  //给出一个警告框，点确定时就执行里面的代码
  add_attr('del',vid,src)
  }
  window.onbeforeunload = function(){...}
  Onunload，onbeforeunload都是在刷新或关闭时调用，可以在'<script></script>script>'脚本中通过window.onunload来指定或者在<body>里指定。区别在于onbeforeunload在onunload之前执行，它还可以阻止onunload的执行。Onbeforeunload也是在页面刷新或关闭时调用，Onbeforeunload是正要去服务器读取新的页面时调用，此时还没开始读取；而onunload则已经从服务器上读到了需要加载的新的页面，在即将替换掉当前页面时调用。Onunload是无法阻止页面的更新和关闭的。而 Onbeforeunload 可以做到。
页面加载时只执行onload
页面关闭时先执行onbeforeunload，最后onunload
页面刷新时先执行onbeforeunload，然后onunload，最后onload。
一个判断页面是否真的关闭和刷新的好方法：

window.onbeforeunload=function (){
alert("===onbeforeunload===");
if(event.clientX>document.body.clientWidth && event.clientY < 0 || event.altKey){
     alert("你关闭了浏览器");
}else{
     alert("你正在刷新页面");
}
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

17.textarea中屏蔽回车默认换行 多行文本框textarea.清除默认回车事件

```javascript
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

```javascript
window.location.reload()刷新当前页面.
parent.location.reload()刷新父亲对象（用于框架）
opener.location.reload()刷新父窗口对象（用于单开窗口）
top.location.reload()刷新最顶端对象（用于多开窗口）
```

20.关于日期 不明白 为什么不用getDay表示日子 getweek表示星期哦

```javascript
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

21: json数据可视化

```
JSON.parse用于从一个字符串中解析出json对象,如
var str = '{"name":"huangxiaojian","age":"23"}'
结果：
JSON.parse(str)

Object

age: "23"
name: "huangxiaojian"
__proto__: Object

JSON.stringify()用于从一个对象解析出字符串，如
var
 a = {a:1,b:2}
结果：
JSON.stringify(a)

"{"a":1,"b":2}"
```

22: 清除所有cookie

```
  function clearAllCookie() {  
    var date=new Date();  
    date.setTime(date.getTime()-10000);  
    var keys=document.cookie.match(/[^ =;]+(?=\=)/g);  
    if (keys) {  
        for (var i =  keys.length; i--;)  
          document.cookie=keys[i]+"=0; expire="+date.toGMTString()+"; path=/";  
    }  
  }
```

23：按enter键禁止换行

```
ue.addListener("keydown", function (type, event) {    
    if (event.ctrlKey && event.which == 13) {     // 判断ctrl 回车 发送
        if (event.which == 13) {     // 禁止换行
            event.cancelBubble = true;
            event.preventDefault();
            event.stopPropagation();
        }
    }
})
```

24：一个简单的倒计时

```
// 一天 = 24 h = 1440 m = 86400 s = 86400 000ms // 一小时 // 一分钟 // 秒
var millseconds = 97879;
function timeCom(times) {
    var _day = 00;
    var _hour = 00;
    var _seconds = 00;
    var _millseconds = 00;
    var val = times;
    setInterval(function () {
        if (val > 0) {
            _day = parseInt(val / 86400);
            _hour = parseInt((val / 3600) - (24__day));
            _seconds = parseInt((val / 60) - (_day_1440) - (_hour_60));
            _millseconds = parseInt(val - (_day_86400) - (_hour_3600) - (_seconds_60));
            (_day < 10) ? _day = '0' + _day : _day;
            (_hour < 10) ? _hour = '0' + _hour : _hour;
            (_seconds < 10) ? _seconds = '0' + _seconds : _seconds;
            (_millseconds < 10) ? _millseconds = '0' + _millseconds : _millseconds;
            console.log(_day, _hour, _seconds, _millseconds);
            val--;
        }
    }, 1000)
}
timeCom(millseconds)
```

25：JQUERY操作CHECKBOX 第二次无法选中的问题

> 用JQuery做CheckBox全选和反选的时候，遇到一个问题。当用JQ控制全选，全取消一次以后，再次点击全选，发现代码变了，但是CheckBox没有处于选中状态。 百度后得知： 我使用的方法是 $("#id").attr("checked",true); 方式，jQuery API明确说明，1.6+的jQuery要用prop，尤其是checkBox的checked的属性的判断。因此修改为

```
 $("input[type='checkbox']").prop("checked");
 $("input[type='checkbox']").prop("disabled", false);
 $("input[type='checkbox']").prop("checked", true);
```

26：js unicode转中文

```
unescape(str.replace(/\u/g, '%u'))
```

27： JS格式化 Thu Dec 07 2017 14:00:43 GMT+0800 (中国标准时间) 转为 2017-12-07

```
//2017-6-13 14:35:31
var d = new Date('Thu Dec 07 2017 14:00:43 GMT+0800 (中国标准时间)');
youWant=d.getFullYear() + '-' + (d.getMonth() + 1) + '-' + d.getDate() + ' ' + d.getHours() + ':' + d.getMinutes() + ':' + d.getSeconds();
//2017-06-13 14:35:31
var date_time = new Date('Thu Dec 07 2017 14:00:43 GMT+0800 (中国标准时间)');
var month = parseInt(date_time.getMonth() + 1);
( month < 10)? month = '0'+month:month; var day = parseInt(date_time.getDate());
(day < 10)?day = '0'+day:day; var hours = parseInt(date_time.getHours());
(hours < 10)?hours = '0'+hours:hours;
var minutes = parseInt(date_time.getMinutes());
(minutes < 10)?minutes = '0'+minutes:minutes;
var seconds = parseInt(date_time.getSeconds());
(seconds < 10)?seconds = '0'+seconds:seconds;
date = date_time.getFullYear() + '-' + month + '-' + day + ' ' + hours + ':' + minutes + ':' + seconds;
```

28：for 循环 和 each跳出循环的区别 each中要实现break和continue的功能的话，要使用其它的方式 break---用return false; continue –用return ture;

break和continue的区别和作用 break和continue都是用来控制循环结构的，主要是停止循环。 1.break 有时候我们想在某种条件出现的时候终止循环而不是等到循环条件为false才终止。 这是我们可以使用break来完成。break用于完全结束一个循环，跳出循环体执行循环后面的语句。 2.continue continue和break有点类似，区别在于continue只是终止本次循环，接着还执行后面的循环，break则完全终止循环。 可以理解为continue是跳过当次循环中剩下的语句，执行下一次循环。

29：数组中对象遍历不能直接赋值给另一个v

```
正确
var _new_data = {
              'spec_id': v.spec_id,
              'spec_name': v.spec_name,
              'spec_nature_array': [],
              'spec_type': v.spec_type
};
不正确
var _new_data = v;
var _new_data = spec_nature[i];
这样会改变原数组内容
```

30： 限制只能输入数字 onkeyup="inputKeyUpNumberValue(this);" 键盘按下之后触发 onafterpaste="inputAfterPasteNumberValue(this);" 粘贴之后触发

```bash
 /**
     * input  只能输入数字
     */
    function inputKeyUpNumberValue(event) {
      if (event.value.length == 1) {
        event.value = event.value.replace(/[^0-9]/g, '');
      } else {
        event.value = event.value.replace(/\D/g, '');
      }
    }

    function inputAfterPasteNumberValue(event) {
      if (event.value.length == 1) {
        event.value = event.value.replace(/[^0-9]/g, '');
      } else {
        event.value = event.value.replace(/\D/g, '');
      }
    }
```

31、定位元素在鼠标指向元素的上方

```
网页被卷起来的高度/宽度（即浏览器滚动条滚动后隐藏的页面内容高度）
(javascript)        document.documentElement.scrollTop //firefox
(javascript)        document.documentElement.scrollLeft //firefox
(javascript)        document.body.scrollTop //IE
(javascript)        document.body.scrollLeft //IE
(jqurey)             $(window).scrollTop()
(jqurey)             $(window).scrollLeft()
网页工作区域的高度和宽度  
(javascript)       document.documentElement.clientHeight// IE firefox       
(jqurey)             $(window).height()
元素距离文档顶端和左边的偏移值  
(javascript)        DOM元素对象.offsetTop //IE firefox
(javascript)        DOM元素对象.offsetLeft //IE firefox
(jqurey)             jq对象.offset().top
(jqurey)             jq对象.offset().left
获取页面元素距离浏览器工作区顶端的距离
 页面元素距离浏览器工作区顶端的距离  =  元素距离文档顶端偏移值  -   网页被卷起来的高度  
即：
 页面元素距离浏览器工作区顶端的距离 =  DOM元素对象.offsetTop  -  document.documentElement.scrollTop
    /**
     * 鼠标浮上图片，显示
     */
    $(document).on("mouseenter", '#sui-spec-details-list .det-spec-nav-img', function() {
      var src = $(this).attr("src");
      var top = $(this).offset().top - $(window).scrollTop();
      var left = $(this).offset().left - $(window).scrollLeft();
      $('.popover-content img').attr('src', src);
      var height = $('.popover').height();
      var width = $('.popover').width();
      $('.popover').css({
        'top': top - height - 30,
        'left': left - width / 2,
        'opacity': 1,
        'display': 'block'
      });
    });
    /**
     * 鼠标离开图片时，隐藏
     */
    $(document).on("mouseleave", '#sui-spec-details-list .det-spec-nav-img', function() {
      $('.popover-content img').attr('src', '');
      $('.popover').css({
        'top': 0,
        'left': 0,
        'opacity': 0,
        'display': 'none'
      });
    });
```

32、 打印内容的时候有可能会出现报错，项目上线请关闭自己的console.调试内容

```
var aa =  null;
aa.length  会直接阻止js代码的执行
```

33、判断undefinded null NaN

```
> 判断undefined:
> var str = undefined;if (typeof(str) == "undefined"){  alert("undefined"); }
> 说明：typeof 返回的是字符串，有六种可能："number"、"string"、"boolean"、"object"、"function"、"undefined"
> 判断null
> var str = null; if (!str && typeof(str)!="undefined" && str!=0){ alert("null"); }
> 判断NaN
> var str = 0/0; if(isNaN(str)){ alert("NaN"); }
> 说明：如果把 NaN 与任何值（包括其自身）相比得到的结果均是 false，所以要判断某个值是否是 NaN，不能使用 == 或 === 运算符。 提示：isNaN() 函数通常用于检测 parseFloat() 和 parseInt() 的结果，以判断它们表示的是否是合法的数字。当然也可以用 isNaN() 函数来检测算数错误，比如用 0 作除数的情况。 判断undefined和null:
var str = undefined; if (str== undefined) { alert("null or undefined"); } var str = undefined; if (str== null) { alert("null or undefined"); }
> 说明：null==undefined
> 判断undefined、null与NaN:
> var str = null; if (!str) { alert("null or undefined or NaN"); }
```
34、视频下载
```
> var $a = $("<a></a>").attr("href", req.url).attr("download", req.filename);
> $a[0].click();
```

35、replace() 方法可用一个新文档取代当前文档。
```
 location.replace(newURL)
```

36、两个对象合并
```
var a ={"name":"SUI"};
var b= {"age":24};
Object.assign(a,b)
```
37、对象添加属性
```
var obj = {};
var a="newKey";
obj[a]='1';
```

38、http接口必须用http,不允许出现https
```
今天和后台对接，他给了个https接口放入了http资源导致表单提交出错。
```

39、swiper 文字 和图片模糊
```
roundLengths : true, //防止文字模糊
```

40、限制数字
```
!/^[0-9]*$/.test(verifyhightValue)
```
