---
title: iOS Android 微信X5
date: 2016-09-20 23:31
tags: mob
categories: MOB
---
------

<!-- more -->

### 关于2018新版微信点击img出现弹出层效果

> 直接img标签会出现类似朋友弹出层效果，如果不想要则用div包裹起来。

如果是类似于映客直播之类的请使用做为封面图片
```
<div class="poster" style="background-image: url(https://file.feiniaolive.com/fc5026378c1b5540aa7085ab68ce5858?imageView2/1/w/480/h/270/format/png/interlace/1/q/75|imageslim)">
</div>
```


### 判断是ios手机还是andorid手机 进行控制"关注按钮"的位置 解决安卓手机视频最优先

```javascript
  var ua = navigator.userAgent.toLowerCase();
  if(/iphone|ipad|ipod/.test(ua)){
    alert("iphone");
  }else if(/android/.test(ua)){
    alert("android");
  };
```

## 在ios10系统中meta设置失效了：
```javascript
// IOS 禁止缩放页面的实现方法
window.onload=function () {
    document.addEventListener('touchstart',function (event) {
      if(event.touches.length>1){
        event.preventDefault();
      }
    })
    var lastTouchEnd=0;
    document.addEventListener('touchend',function (event) {
      var now=(new Date()).getTime();
      if(now-lastTouchEnd<=300){
        event.preventDefault();
      }
      lastTouchEnd=now;
    },false)
  }
```

### 禁止 iOS input标签自动调用输入法

> 今天做了一个关于移动端时间日期的插件，必须使用input为载体，然后设置了 readonly="readonly" 不能输入 但ios微信端出现  ‘确定取消’ 两个输入框按键，经过测试发现当input获得焦点的时候就会触发ios输入法失去焦点就会关闭ios输入法所以做了下面的操作.

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

<img src="/images/txX5.png" alt="腾讯x5"  height="80">

> ios不是腾讯x5

<img src="/images/txnX5.png" alt="腾讯nx5">

## 问题：ios Safari 浏览器的input点击选中时候有高亮边框 safari

> CSS:-webkit-tap-highlight-color 属性

> 作用：改写iOS Safari中可点击元素的高亮颜色。

> 该属性可以只设置透明度。如果未设置透明度，iOS Safari使用默认的透明度。当透明度设为0，则会禁用此属性；当透明度设为1，元素在点击时不可见。

> 兼容性：除了iOS Safari，大部分android手机也是支持的，只是显示效果有所不同。


