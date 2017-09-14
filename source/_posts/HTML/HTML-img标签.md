---
title: img标签
date: 2017-09-14T22:07:33.000Z
tags: html
categories: HTML
---

--------------------------------------------------------------------------------

<!-- more -->

 # img的src如果加载失败，在chrome会有一个边框？

可以在src为空的时候隐藏，动态添加以后img就会出现。

```css
img[src=""]{
    opacity: 0;
}
```
https://www.zhihu.com/question/27426689
https://bitsofco.de/styling-broken-images/?utm_source=CSS-Weekly&utm_campaign=Issue-206&utm_medium=web
