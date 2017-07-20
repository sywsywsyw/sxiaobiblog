---
title: iOS Android 微信X5
date: 2017-07-20 23:31
tags:
categories: MOBile
---

## 禁止 iOS input标签自动调用输入法

> 今天做了一个关于移动端时间日期的插件，必须使用input为载体，然后设置了 readonly="readonly" 不能输入 但ios微信端出现  ‘确定取消’ 两个输入框按键，经过测试发现当input获得焦点的时候就会触发ios输入法失去焦点就会关闭ios输入法所以做了下面的操作

```html
<input value="2017-07-20 23:31"  readonly="readonly"  id="appDateTime"  type="text">
```

```javascript
<script>
$('#appDateTime').focus(function(){
  $('#appDateTime').blur();
})
</script>

```

## 判断微信浏览器内核

> 手机打开网址 <http://debugx5.qq.com/>

> android是腾讯x5

<img src="/hexo/images/txX5.png" alt="腾讯x5"  height="80">

> ios不是腾讯x5

<img src="/hexo/images/txnX5.png" alt="腾讯nx5">
