---
title: fullpage插件的使用
date: 2017-08-14 22:22:05
tags:
categories: 框架插件
---
------

<!-- more -->

# **利用jquery fullpage 插件制作宣传页面的流程**

May 25, 2016

## **一.引入所需的文件**

两种方式：

1.  引入本机的文件 （需要下载）
2.  引入cdn中的文件 （需要网络）

  <!--样式非必须的-->

  <link rel="stylesheet" href="path/jquery.fullpage.css">

  <link rel="stylesheet" href="index.css">

  <script src="jquery.js"></script>

  <script src="jquery.fullpage.js"></script>

## **二.根据插件的规定 写好基本的dom结构**

<div id="main">

  <div class="section">1</div>

  <div class="section">2</div>

  <div class="section">3</div>

  <div class="section">4</div></div><script>$(function(){

  $('#main').fullpage();})</script>

## **三.开始制作页面**

要制作的页面有各种各样的需求,所以需要给插件添加一些配置项

//一些重要的配置项$(function(){

    $('#main').fullpage({

      //滚动一屏的时间

      scrollingSpeed: 1440,

      //index.html#jiewei (分享给别人)

      anchors:['youxing','shiping','guanggao','jiewei'],

      //需要固定定位的元素

      fixedElements:'#fix,.heder nav',

      //设置每个section给固定定位元素留下的位置

      paddingTop:20,

      paddingBottom:30,

      // 当滚动到底部或顶部之后能不能继续滚动

      continuousVertical:true;

      // 是否出现导航小点

      navigation:true,

      navigationPosition:'left',

      // 每一个小点的提示文字

      navigationTooltips:['a','b','c','d'],

      // 到每一屏的时候是否出现提示文字

      showActiveTooltip:true;

      // 进入一屏的时候 会调用afterLoad

      afterLoad:function(name,index){

        // name是当前这张的名字  index当前是第几张

      },

      // 离开一屏的时候 会调用onLeave

      onLeave:function(index,next,dir){

          // index 从哪张离开的

          // next  去到了哪张

          // dir   up  down

          if( index === 5 ){

            $("#section5 h1").addClass('animate-fei');

          }

          if( index === 1){

            // 离开失效

            return false;

          }

          /*css文件中可以这样写*/

          /*

          .animate-fei{

            animation:fei .5s ease .3s both;

          }

          @keyframes fei{

            xxxxxxxxx

          }

          */

      }

    });});

## **四.使用css结合js去制作页面中的动画**

1.  一. 使用 transtion 结合fullpage 去制作动画

  transition:transform .5s ease 1s, opacity .6s ease-in-out;

  transform:rotateX() scale(0.3,0.3);

  transform:rotateY()

  transform:rotateZ()

  transform:translate3d(30px,20px,0) rotateZ(34deg);

1.  要动的元素写到每一个section中
2.  正常状态下是一种样子
3.  当section有了 active, fp-completely类之后是另一个样子
4.  给要动的元素加上transition监测
5.  二. 使用 animation 结合fullpage 去制作动画

animation: fei .8s cubic-bezier(1,0,0,1) .5s both alternate infinite;

名字: fei
时长: 3s 运动方式: ease 延迟: .5s 停留状态: both 方向: alternate（来回） 次数: infinite 运动状态: running || paused —

1.  要动的元素写到每一个section中
2.  正常状态下采用一种动画（可选）
3.  在sectio拥有active类的情况下采用另外一种动画
4.  一些更复杂的情况 把动画预先写好 在配置项的onLeave afterLoad 回调函数中通过添加类名的方式启动动画



# **jQuery全屏滚动插件fullpage**

## **jQuery插件**

插件调用

<ul id="lunbo">

  <li>...</li>

  <li>...</li>

  <li>...</li>

  <li>...</li></ul><script src="jquery.js"></script><script src="jqeury.lunbo.js"></script><script>$('#lunbo').lunbo({

  //一些配置项

  time:40;

  step:function(){}});</script>

jQuery 插件文件

(function($){

  var lunbo = function () {

    console.log(1);

  }

  $.fn.extend({

    lunbo:lunbo;

  })})(jQuery)

## **cdn (content deliver network) 内容分发网络**

如果百度使用了 某个 cdn中的jquery.js,而且用户打开过百度, 我们自己同样使用了 同一个 cdn中的jquery.js, 用户打开我们的网页时使用浏览器缓存中的jquery.js.

例子

<!DOCTYPE html><html>

  <head>

    <meta charset="utf-8">

    <title></title>

    <link rel="stylesheet" href="./css/index.css">

    <script src="https://cdn.boot.com/jquery.js"></script>

    <script src="./js/index.js"></script>

  </head>

  <body>

  </body></html>

## [**fullpage**](http://nate-river.github.io/blog/2016/04/05/full-page)** 插件基本使用**

<link rel="stylesheet" href="jquery.fullPage.css" media="screen" title="no title" charset="utf-8"><script src="jquery.js"></script><script src="jquery.fullPage.js"></script><script>$(function(){

  $('#fullpage').fullpage({

    //这里是配置项

  });})</script>

<div id="fullpage">

  <div class="section" id="section-1">

      <div class="slide"> </div>

      <div class="slide"> </div>

  </div>

  <div class="section" id="section-2"></div>

  <div class="section" id="section-3"></div></div>

每滚动一屏，会给当前section加上　active class

所以我们可以写出类似下面这样的 scss 文件来操控动画

#section1{

  h1{

    /**/

  }

  h2{

    transition: /**/

  }}#section1.active{

  h1{

    animation:/**/

  }

  h2{

    /**/

  }}

## **插件配置项**

sectionsColor

一个数组 规定了各个section的颜色

verticalCentered

每一页的内容是否垂直居中，默认值为true

resize

字体大小是否随窗口缩放而缩放 默认值为false

scrollingSpeed

滚动速度,默认为700毫秒

anchors

给每个section定义锚链接

lockAnchors

是否锁定锚链接

active class

默认显示哪个section

easing

定义页面section滚动的动画方式 设置这个值需要引入jquery.easings 插件

css3

默认为true,使用css3 transform 来实现页面滚动动画

loopTop

滚动到最顶部后是否连续滚动到底部，默认值为false

loopBottom

滚动到最底部后是否连续滚动回顶部 默认值为false

loopHorizontal

横向slide幻灯片是否循环滚动，默认值为true

autoScrolling

是否使用插件的滚动方式，默认值为true, 如果设置为false,则会出现浏览器自带的滚动条

scrollBar

是否包含滚动条，默认值为false 如果设置为true,则浏览器自带的滚动条出现 页面滚动时还是页滚动，但是滚动条的默认行为也效果

paddingTop paddingBottom

设置每一个section顶部和底部的padding，默认值为0 如果我们需要设置一个固定在顶部或者底部的菜单，导航，元素等，可以使用这两个配置项

fixedElements

普通方式书写的固定定位元素会被插件覆盖 需要我们通过指定这个属性才会生效，参数为一个jquery选择器

keyboardScrolling

是否可以使用键盘方向键导航，默认值为true

touchSensitivity

在移动设备中滑动页面的敏感性，默认为5，按百分比衡量，越大则越难滑动

continuousVertical

是否循环滚动，默认值为false，如果设置为true,则页面会循环滚动， 不像loopTop loopBottom那样出现跳动 这个属性和loopTop loopBottom 不兼容 不要同时设置

animateAnchor

锚链接是否可以控制滚动动画，默认为true。如果设置为false,则通过锚链接定位到某个页面显示不再有动画

recordHistory

是否记录历史,默认为true,可以记录页面滚动的地址 通过浏览器前进和后退按钮来导航

menu

绑定菜单，设定的相关属性与anchors的值对应后，菜单可以控制滚动，默认值为 false 可以设置为菜单的jquery选择器

<ul id="fullpageMenu">

  <li data-menuanchor="page1"><a href="#page1">1</a</li>

  .....</ul>

navigation

是否显示导航，默认false 如果设置为true 会显示小圆点，作为导航

navigationPosition

导航小圆点位置，可以设置为left或者right

navigationTooltips

导航小圆点的tooltips设置，默认为[],按照顺序放置

showActiveTooltip

是否显示当前页面的导航的tooltip信息，默认为false

slidesNavigation

是否显示横向幻灯片的导航，默认值为false

slidesNavPosition

横向幻灯片导航的位置，默认为bottom 可以设置为top

controlArrows

定义是否通过箭头来控制slide幻灯片,默认值为true 在移动设备上可以通过滑动来操作幻灯片

scrollOverflow

内容超过满屏后是否显示滚动条，默认为false. 如果设置为true,则会显示滚动条 如果要滚动查看内容，还需要jquery.slimscroll插件，该插件主要用于模拟传统的浏览器滚动条

sectionSelector

section的选择器，默认为.section

slideSelector

slide的选择器 默认为.slide.

## **配置项中的回调函数**

afterLoad(anchorLink,index)

滚动到某一section，且滚动结束后，会触发一次此回调函数，函数接收 anchorLink 和index 两个参数， anchorLink 是锚链接的名称 index 是序号 从1开始计算 可以根据 anchorLink 和 index的参数值判断触发相应的事件

onLeave(index,nextIndex,direction)

离开一个section时触发，通过return false可以取消滚动 离开的序号 到达的序号 滚动的方向

afterRender()

页面结构生成之后的回调函数

afterResize()

浏览器窗口尺寸改变之后的回调函数

afterSlideLoad()

滚动到某一个幻灯片后的回调函数

onSlideLeave

离开一个slide之后的回调函数

## **$.fn.fullpage 对象中的方法介绍**

moveSectionUp()

moveSectionDown()

  $('#movedown').on('click',function(){

    $.fn.fullpage.moveSectionDown();

  })

moveTo(section,slide)

滚动到第几页，第几个幻灯片，注意，页面从1开始，而幻灯片从0开始

silentMoveTo(section,slide)

滚动到第几页，和moveTo一样，但是没有动画效果

moveSlideRight()

幻灯片向右滚动

moveSlideLeft()

幻灯片向左滚动

setAutoScrolling()

setLockAnchors()

setRecordHistory()

setScrollingSpeed()

setAllowScrolling(boolean,[directions])

添加或删除鼠标滚轮/滑动控制，第一个参数true为启用，false 为禁用 后面的参数为方向，取值包含 all,up,down,left,right,可以使用多个，逗号隔开

destory(type)

销毁fullpage特效，type可以不写，或者使用all,不写type,fullpage给页面添加的样式和html元素还在 如果使用all,则样式 html等全部销毁

reBuild()

重新更新页面和尺寸，用于通过ajax请求后改变了页面结构之后，重建效果

*   [ nate-river](https://github.com/nate-river)A web fullstack developer
