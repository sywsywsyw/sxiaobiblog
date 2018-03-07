---
title: MOB-MOB知识点
date: 2017-10-09 21:15:29
tags:
categories: MOB
---
------

[HTML] H5移动端知识点总结

<!-- more -->

  **一、meta标签**

　　**1、控制显示区域各种属性：**
　　metacontent=width=device-width， initial-scale=1.0， maximum-scale=1.0， user-scalable=0name=viewport
　　width：viewport的宽度
　　height：viewport的高度
　　initial-scale：初始的缩放比例
　　minimum-scale：允许用户缩放到的最小比例
　　maximum-scale：允许用户缩放到的最大比例
　　user-scalable：用户是否可以手动缩放
　　**2、IOS中Safari允许全屏浏览：**
　　meta content=yesname=apple-mobile-web-app-capable
　　**3、IOS中Safari顶端状态条样式：**
　　meta content=blackname=apple-mobile-web-app-status-bar-style
　　**4、IOS中Safari设置保存到桌面图标**
　　需要在网站的根目录下存放favicon图标，防止404请求(使用fiddler可以监听到)
　　link rel=apple-touch-icon href=icon.png
　　**5、忽略将页面中的数字识别为电话号码**
　　一般情况下，IOS和Android系统都会默认某长度内的数字为电话号码
　　**二、取消表单元素在点击态时的边框以及半透明灰色背景**
　　css 代码片段
　　input， textarea， button， a
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!
　　**三、移除原生控件样式**
　　css 代码片段
　　input，button，textarea 
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!
　　**四、使用rem来做响应式开发**
　　针对不同的设备，对页面rem做不同缩放
　　sass 代码片段
　　html 
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!
　　**五、定义字体**
　　如无特殊需求，手机端无需定义中文字体，使用系统默认；
　　英文字体和数字字体可使用 Helvetica ，三种系统（ios、android、winphone）都支持。
　　css 代码片段
　　body
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!
　　**六、flex布局兼容性写法**
　　使用 Sass mixin实现flex布局
　　sass 代码片段
　　@mixin display-flex() 
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!
　　**七、移动端touch事件**
　　当用户手指放在移动设备在屏幕上滑动会触发的touch事件
　　touchstart：当手指触碰屏幕时候发生。不管当前有多少只手指
　　touchmove：当手指在屏幕上滑动时连续触发。通常我们再滑屏页面，会调用event的preventDefault()可以阻止默认情况的发生：阻止页面滚动
　　touchend：当手指离开屏幕时触发
　　touchcancel：系统停止跟踪触摸时候会触发。例如在触摸过程中突然页面alert()一个提示框，此时会触发该事件，这个事件比较少用
　　**八、click产生200-300 ms的延迟响应**
　　页面js捕获click事件的回调函数处理，需要300ms后才生效
　　**解决方案：**
　　1、fastclick可以解决在手机上点击事件的300ms延迟
　　2、zepto的touch模块，tap事件也是为了解决在click的延迟问题
　　**九、按钮active态**
　　在iOS系统的移动设备中，需要在按钮元素或body/html上绑定一个touchstart事件才能激活:active状态
　　javascript 代码片段
　　document.body.addEventListener('touchstart'， function () );  
　　运行代码复制代码保存代码提示：1、可先改代码再运行 2、支持Zen coding 3、当代码框处于激活状态下按 CTRL+F11 键可全屏!