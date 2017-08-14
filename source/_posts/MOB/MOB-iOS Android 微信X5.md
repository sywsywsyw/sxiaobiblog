---
title: iOS Android 微信X5
date: 2017-07-20 23:31
tags:
categories: MOB
---
------

<!-- more -->

### 禁止 iOS input标签自动调用输入法


> 今天做了一个关于移动端时间日期的插件，必须使用input为载体，然后设置了 readonly="readonly" 不能输入 但ios微信端出现  ‘确定取消’ 两个输入框按键，经过测试发现当input获得焦点的时候就会触发ios输入法失去焦点就会关闭ios输入法所以做了下面的操作

```html
<input value="2017-07-22 23:31"  readonly="readonly"  id="appDateTime"  type="text">
```

```javascript
<script>
$('#appDateTime').focus(function(){
  $('#appDateTime').blur();
});
</script>

```

## 关于 ios 引用聊天室出现的兼容性问题

> 当ios锁屏之后会默认关掉后台运行程序，估计微信网页进程的websocket进程被强制关闭，然后解锁之后云信聊天室自动发送了重连请求，然后从新下载了一遍历史消息。

> 解决方法，每次获取历史消息的时候去清空文档。


## 判断微信浏览器内核

> 手机打开网址 <http://debugx5.qq.com/>

> android是腾讯x5

<img src="/hexo/images/txX5.png" alt="腾讯x5"  height="80">

> ios不是腾讯x5

<img src="/hexo/images/txnX5.png" alt="腾讯nx5">

## 问题：ios Safari 浏览器的input点击选中时候有高亮边框 safari

> CSS:-webkit-tap-highlight-color 属性

> 作用：改写iOS Safari中可点击元素的高亮颜色。

> 该属性可以只设置透明度。如果未设置透明度，iOS Safari使用默认的透明度。当透明度设为0，则会禁用此属性；当透明度设为1，元素在点击时不可见。

> 兼容性：除了iOS Safari，大部分android手机也是支持的，只是显示效果有所不同。

## 常见的meta

```bash
<head>
  <meta charset="utf-8">
  <!-- 优先使用 IE 最新版本和 Chrome -->
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
  <!-- 360 浏览器就会在读取到这个标签后，立即切换对应的极速核 -->
  <meta name="renderer" content="webkit">
  <!-- 禁止百度转码 -->
  <meta http-equiv="Cache-Control" content="no-siteapp">
  <meta name="description" content="">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Mobile App</title>

  <!-- Disable tap highlight on IE -->
  <meta name="msapplication-tap-highlight" content="no">

  <!-- Web Application Manifest -->
  <link rel="manifest" href="manifest.json">

  <!-- Add to homescreen for Chrome on Android -->
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="application-name" content="Web Starter Kit">
  <link rel="icon" sizes="192x192" href="images/touch/chrome-touch-icon-192x192.png">

  <!-- Add to homescreen for Safari on iOS -->
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black">
  <meta name="apple-mobile-web-app-title" content="Web Starter Kit">
  <link rel="apple-touch-icon" href="images/touch/apple-touch-icon.png">

  <!-- Tile icon for Win8 (144x144 + tile color) -->
  <meta name="msapplication-TileImage" content="images/touch/ms-touch-icon-144x144-precomposed.png">
  <meta name="msapplication-TileColor" content="#2F3BA2">

  <!-- Color the status bar on mobile devices -->
  <meta name="theme-color" content="#2F3BA2">

  <!-- Your styles -->
  <link rel="stylesheet" href="styles/main.css">

  <!-- bower:css -->
  <!-- endbower -->
</head>
```