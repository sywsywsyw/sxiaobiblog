---
title: 移动端布局rem
date: 2016-05-26T22:17:38.000Z
tags: mob
categories: MOB
---

--------------------------------------------------------------------------------

<!-- more -->

# rem两种方式

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


 
