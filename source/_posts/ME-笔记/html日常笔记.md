---
title: html笔记
date: 2018-09-14T22:50:06.000Z
tags: 笔记
categories: HTML
---

--------------------------------------------------------------------------------

<!-- more -->

 # HTML

1.取消浏览器拖动的蓝色选择区

```html
  <body onselectstart="return false"></body>
  <!-- 别的标签也可以使用 -->
```

2.在进行CSS网页布局的时候，我们经遇到刷新要保留表单里内容的时候，习惯的做法使用cookie，但是那样做实在是很麻烦，css中的behavior就为我们很好的解决了这个问题。今天就向大家介绍CSS属性behavior的语法。只兼容IE 哈哈 是不是很气愤呢

3.手机号电话号

```html
  <input type="tel" placeholder="手机号或固定电话" name="tel" pattern="[0-9]*" maxlength="11" class="adphone_tel srfonchang">
```

4.表格

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

5.禁止浏览器记录 文本框之前输入过的内容 autocomplete="off"

```html
  <input type="text" autocomplete="off">
```

6.HTML给视频截图

```html
<!-- 一定要在服务器环境下运行否则会出现跨域报错 -->
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

7.怎么打出来©

```javascript
  <a href="">©</a>
```
