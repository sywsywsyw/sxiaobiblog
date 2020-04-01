---
title: 移动端布局 字体选择 rem
date: 2016-05-26T22:17:38.000Z
tags: mob
categories: MOB
---

--------------------------------------------------------------------------------


## 移动端兼容
//移动端适配
<meta content="width=device-width,height=device-height,initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no" name="viewport">

<!-- more -->

## rem两种方式

## 第一种


只需在页面引入这段**原生js**代码就可以了

```javascript
(function(doc, win) {
    var docEl = doc.documentElement,
        resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
        recalc = function() {
            var clientWidth = docEl.clientWidth;
            if (!clientWidth) return;
            docEl.style.fontSize = 100 * (clientWidth / 750) + 'px';
        };
    if (!doc.addEventListener) return;
    win.addEventListener(resizeEvt, recalc, false);
    doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
```

如何使用？

这是rem布局的核心代码，这段代码的大意是：
**如果页面的宽度超过了640px，那么页面中html的font-size恒为100px，否则，页面中html的font-size的大小为： 100 * (当前页面宽度 / 640)**

**为什么是640px？**

设计图一般是640px的，这样相当于100px = 1rem，可以方便计算；

因为是640px所以应限制下页面的大小，所以最外层的盒子应该是：


 `position: relative;`

 `width: 100%;`

 `max-width: 640px;`

 `min-width: 320px;`

 `margin: 0 auto;`


1.  为什么是640px？
    对于手机屏幕来说，640px的页面宽度是一个安全的最大宽度，保证了移动端页面两边不会留白。注意这里的px是css逻辑像素，与设备的物理像素是有区别的。如iPhone 5使用的是Retina视网膜屏幕，使用2px x 2px的 device pixel 代表 1px x 1px 的 css pixel，所以设备像素数为640 x 1136px，而它的CSS逻辑像素数为320 x 568px。
    如果要切移动端页面，你可以先把效果图宽度等比例缩放到640px，很好用。
2.  为什么要设置html的font-size？
    rem就是根元素（即：html）的字体大小。html中的所有标签样式凡是涉及到尺寸的（如： height,width,padding,margin,font-size。甚至，left,top等）你都可以放心大胆的用rem作单位。
    如果你把html的font-size设为20px，前面说过，rem就是html的字体大小，那么1rem = 20px。
    此时，此时宽60px，高40px的元素样式就这样设置如下 ↓<code class="javascript">width: 3rem;
    height: 2rem;</code>那要是宽55px，高37px呢？然后经过换算，，设置如下 ↓<code class="javascript">width: 2.75rem;
    height: 1.85rem;</code>是不是发现这换算起来有点麻烦啊，，，（当然，你要是心算帝请无视）
    如果我们一开始把html的font-size设为100px呢？此时1rem = 100px，那么上面的宽55px，高37px的元素样式就可以这么设置 ↓<code class="javascript">width: 0.55rem;
    height: 0.37rem;</code>是不是换算起来简单多了？！
    （当然可能有同学问，为什么不一开始把html的font-size设为1px呢，这样换算起来也简单，答：浏览器一般都有最小字体限制，比如谷歌浏览器，最小中文字体就是12px，所以实际上没有办法让1rem=1px。）
    根据上面的js代码，如果页面宽度低于640px,那么页面中html的font-size也会按照（当前页面宽度/640）的比例变化。这样，页面中凡是应用了rem的作尺寸单位的元素都会随着页面变化而等比例缩放了！
3.  都哪些情况可以用rem布局？
    大部分情况下都可以用rem布局这个方法，当然具体还要看情况而定。拿我们公司项目举例，只有底部的导航不用rem，而是用的flex布局。因为导航点击最多，所以给它一个固定的大小（其实就是高度固定，宽度自适应的方案）。大家可以看看淘宝的这个手机页面 [淘宝手机站](https://m.taobao.com/?sprefer=sypc00#index)，基本就是这种感觉，底部导航和顶部搜索框用的高固定，宽自适应的方案，其余的部分基本都是随着浏览器宽度变化在等比例缩放。


## 第二种

 ```bash

@mixin userem($size){
    $shebei-list:320px,375px,360px,384px,414px,460px,640px;
    @each $shebei in $shebei-list{
        @media  screen and(min-width: $shebei){
            html{
                font-size:100px * ($shebei/$size);
            }
        }
    }
}

@include userem(640px)

.item{
    height: 0.88rem;
    background: red;
}
```

@media screen and (min-width: 320px) {
  html {
    font-size: 50px;
  }
}

@media screen and (min-width: 375px) {
  html {
    font-size: 58.59375px;
  }
}

@media screen and (min-width: 360px) {
  html {
    font-size: 56.25px;
  }
}

@media screen and (min-width: 384px) {
  html {
    font-size: 60px;
  }
}

@media screen and (min-width: 414px) {
  html {
    font-size: 64.6875px;
  }
}

@media screen and (min-width: 460px) {
  html {
    font-size: 71.875px;
  }
}

@media screen and (min-width: 640px) {
  html {
    font-size: 100px;
  }
}

.item { 
  height: 0.88rem; 
  background: red; 
}

##  meta标签

　　**1、控制显示区域各种属性：**
　　metacontent=width=device-width， initial-scale=1.0， maximum-scale=1.0， user-scalable=0name=viewport
　　width：viewport的宽度
　　height：viewport的高度
　　initial-scale：初始的缩放比例
　　minimum-scale：允许用户缩放到的最小比例
　　maximum-scale：允许用户缩放到的最大比例
　　user-scalable：用户是否可以手动缩放
　　**2、iOS中Safari允许全屏浏览：**
　　meta content=yesname=apple-mobile-web-app-capable
　　**3、iOS中Safari顶端状态条样式：**
　　meta content=blackname=apple-mobile-web-app-status-bar-style
　　**4、iOS中Safari设置保存到桌面图标**
　　需要在网站的根目录下存放favicon图标，防止404请求(使用fiddler可以监听到)
　　link rel=apple-touch-icon href=icon.png
　　**5、忽略将页面中的数字识别为电话号码**
　　一般情况下，iOS和Android系统都会默认某长度内的数字为电话号码
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
　　英文字体和数字字体可使用 Helvetica ，三种系统（iOS、android、winphone）都支持。
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
 

 ## 移动端html5手机网站如何定义字体font-family

很多懒友在使用自定义字体时候，很容易像PC端那样定义，其实安卓和ISO系统，对中文字体是不支持，所以定义以后看到效果不是直接定义字体效果，如果需要定义
大家会想到 @font-face 定义为微软雅黑字体并存放到 web 服务器上，在需要使用时被自动下载
@font-face {
    font-family: 'MicrosoftYaHei';
    src: url('MicrosoftYaHei.eot'); /* IE9 Compat Modes */
    src: url('MicrosoftYaHei.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
             url('MicrosoftYaHei.woff') format('woff'), /* Modern Browsers */
             url('MicrosoftYaHei.ttf')  format('truetype'), /* Safari, Android, iOS */
             url('MicrosoftYaHei.svg#MicrosoftYaHei') format('svg'); /* Legacy iOS */
   }
 
问题虽然解决了，但是这样操作很消耗用户流量，也对页面打开造成了很大延迟。

我们在一起看看三大主流系统他们字体到底支持哪些呢？

iOS 系统
 
默认中文字体是Heiti SC
默认英文字体是Helvetica
默认数字字体是HelveticaNeue
无微软雅黑字体
 
android 系统
 
默认中文字体是Droidsansfallback
默认英文和数字字体是Droid Sans
无微软雅黑字体
 
winphone 系统 （已弃用）
 
默认中文字体是Dengxian(方正等线体)
默认英文和数字字体是Segoe
无微软雅黑字体
 
总结：
各个手机系统有自己的默认字体，一般不支持我们常用字体，例如微软雅黑等；
如无特殊需求，手机端无需定义中文字体，使用系统默认即可。
英文字体和数字字体可使用 Helvetica ，三种系统都支持。

/* 移动端定义字体的代码 */
body{font-family:Helvetica;}

http://www.lanrenmb.com/yidongyunying/shoujijianzhan/1292.html
https://segmentfault.com/a/1190000006110417


## 利用@media screen实现网页布局的自适应

优点: 适应各种窗口大小。只需在CSS中添加@media screen属性,自动根据浏览器宽度判断并输出不同的长宽值

1280分辨率以上（大于1200px）

```bash
@media screen and (min-width:1200px){
    
}
```

1100分辨率（大于960px，小于1199px）

```bash
@media screen and (min-width: 960px) and (max-width: 1199px) {
    
}
```

880分辨率（大于768px，小于959px）

```bash
@media screen and (min-width: 768px) and (max-width: 959px) {
    
}
```

720分辨率（大于480px，小于767px）
```bash
@media only screen and (min-width: 480px) and (max-width: 767px){
    
}
```
