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

5.判断是苹果手机还是andorid手机 进行控制"关注按钮"的位置 解决安卓手机视频最优先

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
