---
title: 微信视频安卓全屏解决办法
date: 2017-01-18
tags:
categories: VIDEO
---
------

项目预览：https://sywsywsyw.github.io/Video/
项目地址：https://github.com/sywsywsyw/Video

<!-- more -->

# 第一种 （不可以在视频层覆盖内容）

普通播放模式类似腾讯视频文件：「**x5-playsinline**」。

```js
    <video id="video" class="video" controls="controls" playsinline webkit-playsinline x5-playsinline >
        <source src="test.mp4" />
    </video>
```

# 第二种（可以在视频层覆盖内容）

p移动端浏览器中的video元素是比较特别的，早期无论是在iOS还是Android的浏览器中，它都位于页面的最顶层，无法被遮盖。后来这个问题在iOS下得到了解决，但是Android的浏览器则问题依旧。X5是腾讯基于Webkit开发的渲染引擎，它提供了一种名叫「同层播放器」的特殊video元素以解决遮盖问题。

## 简单使用

同层播放器的使用方式跟普通的video元素差别不大，只是需要加上两个X5的自定义属性：「**x5-video-player-type**」和「**x5-video-player-fullscreen**」。

下面做一个测试页面嵌入同层播放器：

```css
body {
    margin: 0;
    background: #000;
    font-size: 0.3rem;
}
.player {
    width: 100%;
    height: 4.22rem;
}
.player .video {
    width: 100%;
    height: 100%;
}
```
```html
 <video id="video" class="video" controls="controls" playsinline x5-video-player-type="h5" x5-video-player-fullscreen="true">
    <source src="test.mp4" />
</video>
```
点击播放后，video元素占全屏，视频部分默认居中显示：

![Img](http://pic1.zhimg.com/v2-eb869701403674a55da0f73d7f1600b4_b.jpg)

## 调整位置

按照官方文档所述，只要修改video元素的「**object-position**」属性，就可以修改视频部分的显示位置，但实际上还要把video元素的宽高设成**屏幕的宽高**才行：

```css
.fullscreen .video {
    object-position: center top;
}
```
```js
var player = document.getElementById('video');
player.addEventListener('x5videoenterfullscreen', function() {
    // 设为屏幕尺寸
    player.style.width = window.screen.width + 'px';
    player.style.height = window.screen.height + 'px';
    // 在body上添加样式类以控制全屏下的展示
    document.body.classList.add('fullscreen');
});
player.addEventListener('x5videoexitfullscreen', function() {
    player.style.width = player.style.height = '';
    document.body.classList.remove('fullscreen');
}, false);
```
效果如下（右图）：

![Img](http://pic2.zhimg.com/v2-b0b27afc9b06694f4abbbf3b4bbaeeb9_b.jpg)注意把video元素的高设为屏幕高度时，要用「window.screen.height」而不能用「document.documentElement.clientHeight」，因为后者不包含导航栏高度，将会导致无法满屏（如上方左图所示）。

## 全屏状态下的布局

下面加上标题栏：
```css
.header {
    width: 100%;
    height: 1.14rem;
    line-height: 1.14rem;
    background: #fff;
    font-size: 0.36rem;
    text-align: center;
    color: #000;
}
```
```htnk
<header id="header" class="header">标题栏</header>
<div class="player">
    <video id="video" class="video" controls="controls" playsinline x5-video-player-type="h5" x5-video-player-fullscreen="true">
        <source src="http://sywsywsyw.github.io/Video/test.mp4" />
    </video>
</div>
```
然而，点击播放进入全屏状态后，标题栏就消失不见了。既然同层播放器是可以被遮盖的，那就试试绝对定位吧：

```css
.fullscreen .header {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 9999;
}
```
标题栏确实遮挡住视频了，但是就多了一层**黑色的渐变**以及**左右两个按钮**（下方左图）。据官方文档所述，这些都是无法移除的。

![Img](http://pic3.zhimg.com/v2-7f05f4a825d8c9138d15f8df1e0055ce_b.jpg)接下来要做的是把视频下移，使整体UI与进入全屏前保持一致（上方右图）：

```css
.fullscreen .player .video {
    object-position: center 1.14rem;
}
```
下一步是在video元素后面添加其他内容：
```css
.main {
    height: 5rem;
    background: #fff;
}
.main .inner {
    padding: 0.3rem;
}
```
```html
<header id="header" class="header">标题栏</header>
<div class="player">
    <video id="video" class="video" controls="controls" playsinline x5-video-player-type="h5" x5-video-player-fullscreen="true">
        <source src="test.mp4" />
    </video>
</div>
<div id="main" class="main">
    <div class="inner">这里是其他内容</div>
</div>
```
然而，进入全屏状态后，内容元素向上偏移了（下方左图）。

![Img](http://pic3.zhimg.com/v2-88b10e3a61b1de118f8f691357ae5c62_b.jpg)明显地，该元素的位置也要下移标题栏的高度：
```css
.fullscreen .main {
    margin-top: 1.14rem;
}
```
接下来尝试简单的点击事件响应：
```js
var main = document.getElementById('main');
main.addEventListener('click', function() {
    this.querySelector('.inner').innerHTML = Date.now();
}, false);
```
此时进入全屏状态后点击内容元素是没有任何反应的，因为video元素占满屏，而它的层级偏高，把内容元素挡住了。知道问题之后，解决方案也很简单，只要把main元素的层级调高就好了：
```css
.fullscreen .main {
    position: relative;
}
```

## 横屏状态下进入全屏

因为同层播放器的全屏状态只能指定一个方向（默认为竖屏），所以播放后还是会强制竖屏。此时整体效果都不太对劲：

![Img](http://pic4.zhimg.com/v2-5e97ad18326db3d57ae800b1cd9d9677_b.jpg)因为横屏状态的宽高与竖屏状态下的刚好相反，所以才导致恢复竖屏时的UI异常。因此，进入全屏时要判断一下宽高，如果宽大于高，则将其交换：

```js
player.addEventListener('x5videoenterfullscreen', function() {
    var width = window.screen.width;
    var height = window.screen.height;
    if (width > height) {
        width = [height, height = width][0];
    }
    player.style.width = width + 'px';
    player.style.height = height + 'px';

    document.body.classList.add('fullscreen');
}, false);
```
## 其他问题

如果播放前页面有滚动条，进入全屏状态下可以滚动吗？答案是确实可以滚动，但是与其叫滚动，不如叫抖动，具体效果可以自己尝试。总之进入全屏状态后就不要用页面的滚动了，而是用局部滚动。此外还应注意，因为调高了层级，如果内容元素太高，就会挡住视频的控制条。

![Img](http://pic3.zhimg.com/v2-40e725130a28ea56e04e9f7d8888dec2_b.jpg)最后一个问题是，播放某些格式的视频时，进度条会出现错乱，即使返回非全屏模式时也还是错乱。

![Img](http://pic3.zhimg.com/v2-b22d5742b8487d9a1670ccd90e2cc33e_b.jpg)

## 总结

*   关于同层播放器的支持情况，[官方文档](http://link.zhihu.com/?target=https%3A//x5.tencent.com/tbs/guide/video.html)有详细描述，最新的微信、QQ以及QQ浏览器都能支持，但是**仅限Android平台**。
*   虽然同层播放器可以解决遮盖video元素的问题，但这毕竟还是X5 Only的技术。如果页面要在非腾讯系的产品中打开，那就要注意处理兼容问题。
*   同层播放器之前的元素，要用绝对定位或固定定位才能展示出来；而其后的元素，只要往下偏移（播放器元素「object-position」指定的偏移）并且提高层级，就与未播放时无异了。

## 同类文章

<!-- https://x5.tencent.com/tbs/guide/video.html
https://aotu.io/notes/2017/01/11/mobile-video/
https://zhuanlan.zhihu.com/p/27559167
https://segmentfault.com/a/1190000010377156?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io
https://segmentfault.com/a/1190000008782550
http://taobaofed.org/blog/2016/05/23/video-player/
http://blog.csdn.net/wqs977/article/details/53166887
http://leonshi.com/2015/09/06/mobile-video-play/
https://segmentfault.com/a/1190000006857675 -->
