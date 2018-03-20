---
title: ios
date: 2017-10-09 21:15:29
tags:
categories: ios
---
------

<!-- more -->

## 关于和 ios android 对接 字符问题

必须使用字符 不可以使用字节进行判断 因为ios 和 android 都把数字 统一当成一个字来判断 所以不能使用字节。

## 关于 ios input内阴影

```bash
input,textarea{
  -webkit-appearance: none;
}
```

## 关于 ios Safari 浏览器的input点击选中时候有高亮边框 safari

> CSS:-webkit-tap-highlight-color 属性

> 作用：改写iOS Safari中可点击元素的高亮颜色。

> 该属性可以只设置透明度。如果未设置透明度，iOS Safari使用默认的透明度。当透明度设为0，则会禁用此属性；当透明度设为1，元素在点击时不可见。

> 兼容性：除了iOS Safari，大部分android手机也是支持的，只是显示效果有所不同。

## 关于 ios input设置readonly之后点击出现光标和输入法 
http://www.bubuko.com/infodetail-2044502.html

```bash
第一种方式：<input disalbed/>，添加disabled，禁用输入框。可能会造成数据上传出错可以查看；
http://sxiaobiblog.com/2016/01/26/HTML/HTML-form/
第二种方式：不使用input,使用其他非焦点获取的标签来代替，比如div ！！！！！建议使用这个；
第三种方式：通过js控制，
<input readonly retype="text"  style="-webkit-user-select:none;" onfocus="this.blur();">
 <!-- css --> 禁止出现光标
 style="-webkit-user-select:none;"
 <!-- js --> 禁止出现输入法
 onfocus="this.blur();"

  禁止 iOS input标签自动调用输入法
 > 今天做了一个关于移动端时间日期的插件，必须使用input为载体，然后设置了 readonly="readonly" 不能输入 但ios微信端出现  ‘确定取消’ 两个输入框按键，经过测试发现当input获得焦点的时候就会触发ios输入法失去焦点就会关闭ios输入法所以做了下面的操作.
<input value="2017-07-22 23:31"  readonly="readonly"  id="appDateTime"  type="text">
$('#appDateTime').focus(function(){
  $('#appDateTime').blur();
});

```

## 关于 ios 引用聊天室出现的兼容性问题

> 当ios锁屏之后会默认关掉后台运行程序，估计微信网页进程的websocket进程被强制关闭，然后解锁之后云信聊天室自动发送了重连请求，然后从新下载了一遍历史消息。

> 解决方法，每次获取历史消息的时候去清空文档。

## 关于 ios 的点击事件绑定无效的处理方法
之前做过一个项目，元素是动态加载的，于是将点击事件绑定到document上，结果在安卓手机上点击没问题，来到iPhone就不行，后来查资料，得出结果，要在绑定的元素上加一个属性：cursor:pointer;才会有效。暂时还没找到原因，是ios的bug？另外再记录一个点击后消除背景闪一下的css：-webkit-tap-highlight-color:transparent;
http://blog.csdn.net/u014477038/article/details/52527194
