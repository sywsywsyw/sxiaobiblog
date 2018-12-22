---
title: video在iOS和安卓的属性
date: 2017-01-17T00:00:00.000Z
tags: [微信,video]
categories: VIDEO
---

--------------------------------------------------------------------------------

项目预览：<https://sywsywsyw.github.io/Video/> 项目地址：<https://github.com/sywsywsyw/Video>

<!-- more -->

# 1\. 视频标签里的内联播放相关属性

微信在video标签上新增了一些x5的私有属性，分别是：

1. `x5-video-player-type` 启用同层播放。取值固定为`'h5'`。

2. `x5-video-player-fullscreen` 是否全屏。取值为`'true'`或`'false'`。

3. `x5-video-orientation` 视频方向。取值分别为`'landscape'`、`'portrait'`或者`'landscape|portrait'`，分别对应横屏、竖屏及自动旋转（这个应该用的少）。

4. `x5-playsinline` 类似iOS播放但是不能覆盖内容

不过有一点需要注意的是，这些都是x5的私有属性，仅适用于Android平台。而跟iOS平台相关的，则是这几个属性：

1. `airplay`

2. `x-webkit-airplay`

3. `playsinline`

4. `webkit-playsinline`

其中最后两个是iOS平台下的内联播放属性，都是布尔属性，不需要赋值（存在即是true）；前两个是iOS平台下airplay的相关属性（说实话我现在也没搞明白为什么网页需要airplay属性），取值为`'allow'`或`'deny'`，通常保险起见用`'allow'`就可以。

# 2\. CSS的属性选择及取值

微信在同层接入规范中提到了`object-position`这个属性，用于设置视频出现的位置。实际在尝试的过程中，搭配`object-fit`属性同时使用的效果会比较好。但这两个属性并不是x5私有属性，而是原生的，所以它们同时适用于Android和iOS两个平台。

`object-position`和`object-fit`这两个元素主要的作用是为"可替换元素"设置位置和大小。这里的"可替换元素"，指的是内容不受CSS显式控制的元素，比如比较典型的就是`<img>`、`<object>`、`<video>`和表单元素等。

说回视频播放。微信官方的同层接入规范中推荐的做法，是用js动态计算需要的像素值，然后给`object-position`属性赋值。而我自己尝试了一圈下来，发现`object-position`这个属性本身支持百分比取值，通常视频默认的值是`'50% 50%'`，也就是居中；全屏视频一般情况下需要贴底放，所以要把取值改成`'0 100%'`。

另一个属性`object-fit`，有点类似`background-size`属性，用来设置视频在容器内的填充方式，平时用只需要取值`'contain'`（保持宽高比填满容器）就可以了。不过这里需要留意的是，全屏下，由于视频一般都不会正好填满屏幕（宽高比差异以及输出分辨率没算顶部标题栏），会在顶部留下一条空隙。这条空隙通常是默认黑色的，如果需要更改颜色，首先要加上个`'display:block;'`（因为video默认是inline的），然后直接改`background-color`就OK~

# 3\. 视频封面

`<video>`标签里有一个与视频封面相关的属性`poster`，但是在使用中发现性能存在一些问题，在Android端打开视频时（加载），会有跳动的感觉，但是如果去掉，在视频加载时（`preload`取值`'auto'`，且未用预加载）则会显示空白页面。目前换用了背景图片的方式，但由于视频全屏播放时顶部会有空隙，所以额外加了个`background-position: bottom;`以及`background-size: contain;`（取值和视频保持一致），这样设置好的背景在播放视频时就不会漏边了。

# 4\. 设置视频视口大小

同层接入规范里推荐在resize事件回调里设置视频视口大小，我习惯直接设置`<video>`标签的`width`和`height`，所以在resize回调里加入：

`$('video') .attr({ 'width': window.innerWidth + 'px', 'height': window.innerHeight + 'px' });`

就可以了。

# 5\. UA特性探测

同层接入规范里给的，判断是否是同层播放器方法：

1. 在微信等TBS里通过UA判断X5内核版本来区分,当版版本号>036849表示支持 UA示例: Mozilla/5.0 (Linux; Android 4.4.4; OPPO R7 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/37.0.0.0 Mobile MQQBrowser/6.8 TBS/036849 Safari/537.36 MicroMessenger/6.3.27.861 NetType/WIFI Language/zh_CN

2. 在QQ浏览器Android版本中,当浏览器版本>=7.1时开始支持 UA示例：User­Agent: Mozilla/5.0 (Linux; U; Android 4.4.4; zh­cn; OPPO R7 Build/KTU84P) AppleWebKit/537.36 (KHTML, like Gecko)Version/4.0 Chrome/37.0.0.0 MQQBrowser/7.1 Mobile Safari/537.36

在iOS和安卓手机里的微信下播放视频时，会遇到不少问题，例如需要手动点击，视频才会播放，并且视频会跳出微信框，出现控制条，如果视频不是腾讯视频，播放完毕会出现腾讯视频的广告推送等问题

解决办法：给video标签加一些属性，调用h5原生video。

# 6\. 详细解释

```html
<video
  id="videoALL"
  src="video/01.mp4"
  poster="images/1.jpg" /*视频封面*/
  preload="auto"
  webkit-playsinline="true" /*这个属性是iOS 10中设置可以
                     让视频在小窗内播放，也就是不是全屏播放*/  
  playsinline="true"  /*iOS微信浏览器支持小窗内播放*/
  x-webkit-airplay="allow"
  x5-video-player-type="h5"  /*启用H5播放器,是wechat安卓版特性*/
  x5-video-player-fullscreen="true" /*全屏设置，
                     设置为 true 是防止横屏*/>
  x5-video-orientation="portraint" /*播放器支付的方向，
                     landscape横屏，portraint竖屏，默认值为竖屏*/
  style="object-fit:fill">
</video>
```

**poster="images/1.jpg"**:属性规定视频下载时显示的图像，或者在用户点击播放按钮前显示的图像。如果未设置该属性，则使用视频的第一帧来代替。

**preload="auto"** **：**属性规定在页面加载后载入视频。

**webkit-playsinline****和playsinline：**视频播放时局域播放，不脱离文档流 。但是这个属性比较特别， 需要嵌入网页的APP比如WeChat中UIwebview 的allowsInlineMediaPlayback = YES webview.allowsInlineMediaPlayback = YES，才能生效。换句话说，如果APP不设置，你页面中加了这标签也无效，这也就是为什么安卓手机WeChat 播放视频总是全屏，因为APP不支持playsinline，而ISO的WeChat却支持。

这里就要补充下，如果是想做全屏直播或者全屏H5体验的用户，ISO需要设置删除 webkit-playsinline 标签，因为你设置 false 是不支持的 ，安卓则不需要，因为默认全屏。但这时候全屏是有播放控件的，无论你有没有设置control。 做直播的可能用得着播放控件，但是全屏H5是不需要的，那么去除全屏播放时候的控件，需要以下设置：同层播放。

**x-webkit-airplay="allow"**暂时无法确切的知道其作用，但是小编猜测，这个属性应该是使此视频支持iOS的AirPlay功能。使用AirPlay可以直接从使用iOS的设备上的不同位置播放视频、音乐还有照片文件，也就是说通过AirPlay功能可以实现影音文件的无线播放，当然前提是播放的终端设备也要支持相应的功能。

**x5-video-player-type****：**启用同层H5播放器，就是在视频全屏的时候，div可以呈现在视频层上，也是WeChat安卓版特有的属性。同层播放别名也叫做沉浸式播放，播放的时候看似全屏，但是已经除去了control和微信的导航栏，只留下"X"和"<"两键。目前的同层播放器只在Android（包括微信）上生效，暂时不支持iOS。至于为什么同层播放只对安卓开放，是因为安卓不能像ISO一样局域播放，默认的全屏会使得一些界面操作被阻拦，如果是全屏H5还好，但是做直播的话，诸如弹幕那样的功能就无法实现了，所以这时候同层播放的概念就解决了这个问题。不过在测试的过程中发现，不同版本的ISO和安卓效果略有不同。

**x5-video-orientation****：**声明播放器支持的方向，可选值landscape 横屏, portraint竖屏。默认值portraint。无论是直播还是全屏H5一般都是竖屏播放，但是这个属性需要x5-video-player-type开启H5模式

**x5­-video­-player­-fullscreen****：**全屏设置。它又两个属性值，ture和false，true支持全屏播放，false不支持全屏播放。

其实，ISO 微信浏览器是Chrome的内核，相关的属性都支持，也是为什么X5同层播放不支持的原因。安卓微信浏览器是X5内核，一些属性标签比如playsinline就不支持，所以始终全屏。

还有个问题，在Android的微信里面，就算加上了上面的属性，还会出现上下有黑边，不能全屏的问题。

解决办法：给video加上object-fit: fill;的style属性。如果还是有黑边有可能是视频尺寸不合适。
