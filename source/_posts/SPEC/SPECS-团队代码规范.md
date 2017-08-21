---
title: 团队代码规范
date: 2016-08-11
tags:
categories: SPEC
---
------

# 这是团队开发中基本约定的一些内容，请认真遵守，如果有补充的请联系管理。

<!-- more -->

## 代码方面

### 所有的html代码小写

> 所有的代码只能使用小写,适用于标签名，类名，标签的属性以及属性值（tetxt/CDATA例外，作为内容时例外）

```html
<ul class="lists"><li></li><ul>
<div class="name"><a></a></div>
```

### 使用html的doctype

```html
<!doctype html>
```

### 页面编码使用utf-8

```html
<meat charset="utf-8">
```
### 页面内容lang为zh-Hans-CN

> 这条规范基于国际标准RFC 4646,使用单一的zh和zh-CN都属于废弃语法。和中文有关的lang值如下：

* zh-Hans 简体中文
* zh-Hans-CN 大陆地区使用的简体中文
* zh-Hans-HK 香港地区使用的简体中文
* zh-Hans-MO 澳门地区使用的简体中文
* zh-Hans-SG 新加坡使用的简体中文
* zh-Hans-TW 台湾地区使用的简体中文
* zh-Hant 繁体中文
* zh-Hant-CN 大陆地区使用的繁体中文
* zh-Hant-HK 香港地区使用的繁体中文
* zh-Hant-MO 澳门地区使用的繁体中文
* zh-Hant-SG 新加坡使用的繁体中文
* zh-Hant-TW 台湾地区使用的繁体中文

### 文件命名

> 文件扩展名必须为.html

* index.html 首页或者引导页
* main.html  首页主页
* download.html 下载页面
* vedio.html 视频
* 文件名中只可以由英文字母`a~z`、排序数字`0~9`或者间隔符`-`组成
* 文件命中禁止包含特殊符号，比如`空格`、`$`等
* 文件名区分大小写，统一使用小写字母
* 为了更好的表达语义，文件名使用英文单词命名，或英文简写

### 图片

> 图片统一存放在图片服务器中，注意修饰性图片和内容类型图片的分开放置，如：图片的存放文件夹建议使用img命名来存放logo,合并的图片等页面固定元素的图片，images放一些开发会动态调用的头像，剧照图等。

### 图片格式和大小

> 图片格式：图片格式允许采用gif/jpg/png/wep,平衡图片质量与文件大小，适当运用`css sprite`理念合并并修饰图片，不过分损失质量情况下尽量减小页面下载数据量，图片单张体积不能超过150K,jpg文件必须进行压缩，一般60%品质即可，如果图片质量不好，可以提高到80%

### 图片的引用

* 图片路径需要使用绝对路径方式
* 所有img元素必须加上alt属性，修饰性图片alt属性内容留空，内容性质图片的alt中填写相应的内容
* 必须加上width和height属性，值为它的原大小，但不要对他进行缩放。

```html
<img src="themes/mall/new/img/logo.png" width="60" height="60" alt="飞鸟播客">
```
### 图片命名

* 图片后缀命名统一使用小写
* 使用间隔符`-`隔开,一般背景图片用`bg-`开头，测试图片用`img-`,按钮图片用`btn-`,图标图片用`icon-`开头，聚合图片用`spr-`开头，后面跟英文单词，不推荐使用汉语拼音，如果名称过长，适当使用缩写

```html
bg-body.jpg spr-home.png img-promo.jpg btn-submit.png icon-game.png
```

### 图片存放

> 图片存放在想对应的html文件的style中

### 注释

> 正确的注释规范

> 感叹号后面两个横线，结束时使用两个横线，不要再注释中使用`--`,`--`只能发生在XHTML注释的开头和技术，也就是说在内容中它们不再有效，例子:

```html
<!--这里是注释     -这里是注释-->
<!--    -这里是注释     -这里是注释    --->
```

> 用等号或者空格替换内部的虚线，这样的是正确的

```html
<!--这里是注释========这里是注释>
```

> IE条件注释（IE10已不支持注释）

```html
<!-- [if IE]>
这里只有ie浏览器才可以显示
<![endif]-->

<!-- [if !IE]>
这里只有非ie浏览器才可以显示
<! <![endif]-->

<!--[if IE 6]>
这里只有ie6浏览器才可以显示
<![endif]-->

<!--[if lt IE 9]>
这里只有ie9以下浏览器才可以显示
<![endif]-->

<!--[if lte IE 8]>
这里只有ie8以及ie8以下浏览器才可以显示
<![endif]-->
```

### 脚本中文转换unicode

> 为了防止外链脚本没有申明正确编码导致乱码问题，脚本中如果用到中文，必须转为unicode码

```html
/* 不推荐 */
document.write("关于飞鸟播客")
/* 推荐 */
document.write("\u5173\u4e8e\u817e\u8baf\u6e38\u620f")
```

### 去掉类型属性

> 不要为css,js使用类型属性，特别说明类型（type）属性是多余的，在HTML5中默认已包含

```html
<!--不推荐-->
<link href="../css/comm.css" rel="stylesheet" type="text/css" />
<script type="text/javascript"><!--mce:0--></script>
<script src="common.js" type="text/javascript">
<!--推荐-->
<link href="../css/comm.css" rel="stylesheet" />
<script type="text/javascript"><!--mce:1--></script>
<script src="common.js">
```
###  去掉自闭合元素`/`闭合符

> 为半闭合元素加上'/'闭合符是没有必要的，声明为HTML5以后的doctype,所有的浏览器都会正确处理，常见的半闭合元素：img input br hr

```html
<!--不推荐-->
<br /><hr /><img src="/wiki/" /><input type="text" />
<!--推荐-->
<br><hr><img src="/wiki/"><input type="text">
```
### 对于"<"">"之类的符号进行实体转义

> 在HTML中不能使用小于号"<"和">",以免浏览器误认为他们是标签。若果希望正确显示预留字符，我们必须在HTML源代码中使用字符字体（character entities）

```html
<!--不推荐-->
<a href="/wiki/">more>></a>
<!--推荐-->
<a href="/wiki/">more&gt;&lt;</a>
```

### 元素嵌套规范

> 段落元素与标题元素只能嵌套内联元素

```html
<!--不推荐-->
<a><p></p><div></div><p></p></a>  <h2><div></div></h2>
<!--推荐-->
<p><span></span><span></span></p>
<h2><span></span></h2>
```

## CSS规范

### 命名规范

###### 使用类选择器，尽量避免使用ID选择器定义样式

> ID在一个页面的唯一性导致了如果以ID伟选择器来写CSS,就无法重用

##### 用字母开头

* 必须用字母开头命名选择器，这样可以在所有浏览器下面兼容
* 不允许出现单个字母的类选择器出现
* 不允许命名带有广告等英文的单词，例如ad,adv,adver,advertisin以免该模块被浏览器当做垃圾广告过滤掉。

##### 全小写，并使用'-'连字符

* 下划线'_'禁止出现在class命名中，统一用'-'连字符
* 禁止驼峰式命名

##### 命名简约而不失语义

* 避免过度简写，.icon足够表示这是一个图标，而.i不代表任何意思
* 使用有意义的名称，使用结构化或者作用目标相关的，而不失抽象的名称

##### 文件命名举例

> 基本样式：base.css框架布局：layout.css模块样式：module.css全局样式：global.css字体样式：font.css首页样式：index.css链接样式：link.css

##### 常用类/ID命名举例

> 常用的类命名应该尽量以常用英文单词为准，并在适当的地方加以注释。部分命名解释约定：整页.wp页眉.header页脚.footer导航.nav主体内容.main侧边栏.side标志.logo搜索.search登录.login注册.reg标题.tit-...副标题.subtit-...按钮.btn-...链接.link-...背景图片.bg-...列表.list-...表哥.tb-...标签.tag-...视频.video-...联系.contact

### Reset参考

> 使用时按需配置，去除冗余

###### 精简版（适用于一般的游戏类官网、专题）

```html
body,h1,h2,h3,h4,h5,h6,p,ul,ol,li,input,select,textarea,div,table,td,th,tr,dt,dd,dl{margin:0;padding:0;}
h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal;}
ul,ol{list-style:none;}
strong,b{font-weight:normal;}
em,i{font-style:normal;}
table{border-spacing:0;border-collapse:collapse;}
img{border:0;vertical-align:middle;}
input,select{vertical-align:middle;font-size:100%;line-height:150%;font-family:arial,'\5FAE\8F6F\96C5\9ED1',sans-serif;-webkit-appearance:none;}
a{text-decoration:none;outline:none;hide-focus:expression(this.hideFocus=true);background-color:transparent;-webkit-tap-highlight-color:transparent;}
body{min-width:1000px;font:14px/1.5 arial,"\5FAE\8F6F\96C5\9ED1",sans-serif;-webkit-text-size-adjust:none;-ms-text-size-adjust:none;}
```

###### 通用版（基本适用于所有的页面）

```html
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,textarea,p,blockquote,th,td{margin:0;padding:0}
table{border-collapse:collapse;border-spacing:0}
fieldset,img{border:0}
address,caption,cite,code,dfn,em,strong,th,var{font-style:normal;font-weight:normal}
ol,ul{list-style:none}
caption,th{text-align:left}
h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal}
q:before,q:after{content:''}
abbr,acronym{border:0;font-variant:normal}
sup{vertical-align:text-top}
sub{vertical-align:text-bottom}
input,textarea,select{font-family:inherit;font-size:inherit;font-weight:inherit}
input,textarea,select{*font-size:100%}
```

###### 通用版（支持HTML5）

```css
body,div,dl,dt,dd,ul,ol,li,h1,h2,h3,h4,h5,h6,pre,code,form,fieldset,legend,input,textarea,p,blockquote,th,td,hr,button,article,aside,details,figcaption,figure,footer,header,hgroup,menu,nav,section{margin:0;padding:0}
article,aside,details,figcaption,figure,footer,header,hgroup,menu,nav,section { display:block; }
table{border-collapse:collapse;border-spacing:0}
audio,canvas,video { display: inline-block;*display: inline;*zoom: 1;}
fieldset,img{border:0}
address,caption,cite,code,dfn,em,strong,th,var{font-style:normal;font-weight:normal}
ol,ul{list-style:none}
caption,th{text-align:left}
h1,h2,h3,h4,h5,h6{font-size:100%;font-weight:normal}
q:before,q:after{content:''}
abbr,acronym{border:0;font-variant:normal}
sup{vertical-align:text-top}
sub{vertical-align:text-bottom}
input,textarea,select{font-family:inherit;font-size:inherit;font-weight:inherit}
input,textarea,select{*font-size:100%}
```
### 代码风格

###### css属性值需要用到引号时，统一使用单引号

###### 为单个css选择器或新申明开启新行

###### css属性书写顺序   布局定位属性 自身属性 文本属性 其他属性 CSS3属性

```html
/*  这些属性只是最常用到的, 并不代表全部 */
/* 布局定位属性 */
display / list-style / position（相应的 top,right,bottom,left） / float / clear  / visibility / overflow
/* 自身属性 */
width / height / margin / padding / border / background
/* 文本属性 */
color / font / text-decoration / text-align / vertical-align / white- space / break-word
/* 其他（CSS3）  */
content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient ...
```
###### css浏览器私有前缀书写格式

> 私有格式在前面，标准格式在后面。先写带有浏览器私有标志的，后写W3C标准的

```html
selectors{
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#ffffff), color-stop(100%,#eff2f4));
    background: -webkit-linear-gradient(top, #ffffff 0%,#eff2f4 100%);
    background: -moz-linear-gradient(top, #ffffff 0%, #eff2f4 100%);
    background: -ms-linear-gradient(top, #ffffff 0%,#eff2f4 100%);
    background: -o-linear-gradient(top, #ffffff 0%,#eff2f4 100%);
    background: linear-gradient(to bottom, #ffffff 0%,#eff2f4 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#ffffff', endColorstr='#eff2f4',GradientType=0 );
}
```
###### 不要以没有寓意的标签做为选择器

> `强烈建议不要使用`，因为这会造成大面积污染，除非你可以断定现在或将来你的这个选择器不会污染其他同类

###### css单行书写法

> 每个CSS选择符的主申明区的属性在同一行内书写，每个属性之间空一格

```html
selectors{ height: 30px; padding-bottom: 10px; border-bottom: 1px solid #858585; margin-bottom: 10px; }
```
###### css多行书写法

```html
selectors{
height: 30px;
padding-bottom: 10px;
border-bottom: 1px solid #858585;
}
```

###### 除非必要情况否则尽量少书写行内进行控制样式

#### 用CSS控制交互或视觉的变化，js只要增加ClassName

* 利用css一次性更改多个节点样式，避免多次渲染，提高渲染效率
* 需要在结构中注释此类交互

### 注释

###### 行间注释

> 直接写于属性值后面，如：

```html
.search{background: #333 url(../img/search.gif) no-repeat;/*定义搜索框的背景*/
```

###### 整段注释

> 分别在开始及结束地方加入注释，如：

```html
/*=====搜索条=====*/
.search {background: #333 url(../img/search.gif) no-repeat;}
/*=====搜索条结束=====*/
```

> 注意：以下写法不可取

```html
.news/* 这里是高度自动撑 */ {line-height:1.5}
.news {/*line-height:1.5 这里是高度自动撑 */}
```

> 理由很简单，注释是ie6的hack方法之一，所以这样写容易让ie6误解。`提示`：尽量不要使用中文注释，无论是html也好css js也罢，这样会让ie6出现问题  尽量使用简单的英文或者拼音，在版本发布的时候 尽量剔除注释内容，尽可能的减少文件的字节数。

### Hack（本项目中暂时不用这么考虑）

> 原则上不允许使用Hack - 很多不兼容问题可以通过改变方法和思路来解决，并非一定需要Hack，根据经验你完全可以绕过某些兼容问题。 - 一种合理的结构和合理的样式，是极少会碰到兼容问题的。 -由于浏览器自身缺陷，我们无法避开的时候，可以允许使用适当的Hack。

#### 统一Hack方法

```html
.element{
color:#000;             /*w3c标准*/
[;color:#f00;];         /*Webkit(chrome和safari)*/
color:#666\9;           /*IE8*/
*color:#999;            /*IE7*/
_color:#333;            /*IE6*/
}
:root .element{color:#0f0\9;}  /*IE9*/
@media all and (-webkit-min-device-pixel-ratio:10000), not all and (
-webkit-min-device-pixel-ratio:0) { .element{color:#336699;}}  /*opera*/
@-moz-document url-prefix(){ .element{color:#f1f1f1;}} /*Firefox*/
```
#### 简写css颜色属性值

```html
/* 不推荐 */
selectors{ color:#000000; background-color:#ddeeff;}
/* 推荐 */
selectors{ color:#000; background-color:#def;}
```

#### 删除css属性值为0的单位

> 0就是0，任何单位都不需要

```html
/*不推荐*/
selectors{ margin:0px; padding:0px;}
/*推荐*/
selectors{ margin:0; padding:0;}
```

#### 删除无用css样式

> 好处：（1）删除无用的样式后可以缩减样式文件的体积，加快资源下载速度;第二，对于浏览器而言，所有的样式规则都会被接卸后索引起来，即使当前页面无匹配规则。移除无匹配规则，减少索引性，加快浏览器查找速度。

```html
/* 不推荐 */
selectors{ font-size:12px;}
.nav{}
.nav-item{ height:20px;}
/* 推荐 */
selectors{ font-size:12px;}
.nav-item{ height:20px;}
```

## JS规范

> 页面中书写到js时请务必参考本规范Javascript是控制用户与页面交互、前端与后台数据交互的重要工具，在我们的日常工作中应用非常广泛。为了有效提高代码的质量，基于“易维护，易调试，高性能”的原则，参考业界知名团队的规范与指南指定本ugifan，大家在编写Javascript代码时，应尽量遵守本规范，提高自己的代码质量。

### 命名

> Javascript是区分大小写的语言，在对Javascript的变量、函数、常量等命名时，应该遵循Javascript自身采用的命名规则，以保持代码的一致性。具体规则如下：

#### 常量：

> Javascript自身不支持常量，在程序中如果要定义“禁止定义后改变”的变量，可以参考其他编程语言，采用下划线分割的全大写字符串来定义。例如:PAGEBASECOLOR、COOKIR_PREFIX等。

#### 变量：

> 首字母小写，驼峰命名法，原则上采用名词及名词短语，描述该变量代表的数据。例如：videoID,userLevel,linkToHome,btnDown,totalPages

#### 函数：

> 首字母小写，驼峰命名法，原则上函数采用动词及动词短语，以描述该函数的行为，对象采用名词及名词词组。例如：login(),checkLogin(),showVideo(),switchTabs(),changLevel(),addClass(),loadScript(),

#### 类及命名空间：

> 首字母大写、驼峰命名法。例如：LoginManager,Dialog,LazyLoader,FlashManager

#### 文件名：

> 全小写，单词间可以不分割或用连接线“-”分隔，文件名可以加.min/.debug表示文件状态，例如：common.js(一般的文件名)、milo.min.js(压缩后的文件)、common.debug.js(未压缩、调试用的文件)。

#### 可读性：

> 在未做压缩处理的源代码中，类、变量、函数的命名应该尽量具有语义、应当避免“a”、“b”、“yy”这类无意义的命名(循环语句中的i/j/k/除外)。代码的压缩，应该采用专门的工具（如YUI Compressor、Google Closure）来进行，不要人为用无意义的命名来减少代码量。

### 变量定义和初始化

> javascript并不强调变量在使用前必须定义，但是如果没有使用var 关键字来定义变量，则这个变量就会变成全局变量，可能会造成对同名全局变量的覆盖，在多人写作开发，引入多个库或多个js文件的情况下，容易导致变量名冲突等问题。因此，对变量的定义和初始化建议参照一下规则：总是将代码包裹成一个IIFE（Immediateley-Invoked Function Expression）,用一创建独立隔绝的定义域。这一举措可以防止全局命名空间被污染。IIFE还可以确保你的代码不会轻易被其他全局命名空间的代码所修改。

> 不推荐

```javascript
var x = 10,
    y = 100;

// Declaring variables in the global scope is resulting in global scope pollution. All variables declared like this
// will be stored in the window object. This is very unclean and needs to be avoided.
console.log(window.x + ' ' + window.y);
```

> 推荐

```javascript
// We declare a IIFE and pass parameters into the function that we will use from the global space
(function(log, w, undefined){
  'use strict';

  var x = 10,
      y = 100;

  // Will output 'true true'
  log((w.x === undefined) + ' ' + (w.y === undefined));

}(window.console.log, window));
```

> 虽然Javascript是一门弱类型语言，变量的数据类型可以随时自由转换，但是在实际使用中，依然建议大家避免用同一个变量存储不同类型的数据。 在定义变量的同时对其初始化是很好的编程实践，这可以避免后续忘记给变量赋值而直接使用它引发的"undefined"错误。

### 代码格式

#### 大括号

> 前大括号始终位于当前行末尾，后大括号新起一行并与代码块的首行保持相同缩进对齐，数组和对象的快速定义可以例外。例如 _数组和对象的快速定义:

```javascript
var arr = [1,2,3];
var obj = {a:1, b:2, c:3};
```
#### 数组初始化

```javascript
this.rows_ = [
  '"Slartibartfast" ',
  '"Zaphod Beeblebrox" ',
  '"Ford Prefect" ',
  '"Arthur Dent" ',
  '"Marvin the Paranoid Android" ',
  'the.mice@magrathea.com'
];
```

#### 函数的调用

```javascript
tvp.play('u1134234422','mod_player', {
  autoplay: '1',
  width: 600,
  height: 449,
  controls: '1'
});
];
````

#### 函数定义

```javascript
function functionName() {
    // function codes
}
```
#### 代码块

```javascript
if (condition == true) {
    // do something
} else {
    // do something else
}

for(var i = 0; i < data.length; i++) {
    // loop body
}
```

```javascript
/* 不推荐 */
if(event.target)
    return event.target;
else
    return event.srcElement;
```

```javascript
/* 推荐 */
if(event.target) {
    return event.target;
} else {
    return event.srcElement;
}
```
> 对于代码块，始终用大括号包裹，对于单行判断、while循环等可以省略大括号的，一律不省略。 ###引号 在处理字符串时，优先使用单引号，仅在必须的情况下才使用双引号。这不仅能保持代码的一致性、缩小代码文件大小，在创建包含HTML代码的字符串时，这尤其有利，例如：

```html
var msg = '<li class="msg">这是一条信息</li>';
```

####### 分号

> 所有的语句必须用分号结尾所有的代码块不得使用分号结尾

## 注释

> 对代码中的类、方法、属性、复杂的实现逻辑等，应该加上必要的注释。注释的格式参照JSDoc语法。常见的注释范例：

```javascript
/**
 * 这是一段常规注释，不包含调用参数和返回值
 */
 function doSomething() {
     alert('hello');
 }

/**
 * 这是一个有调用参数和返回值的函数
 * 注释里要用@param和@return分别标注参数和返回值
 *
 * @param {number} idx 每次执行时当前元素在数组中的索引
 * @param {object} dom 当前循环到的元素
 * @return {string} 每次循环时返回当前元素的id
 */
 $.each = function(idx, dom) {
     if(dom = this[idx]) {
         return dom.id;
     } else {
         return '';
     }
 };
````
### 技巧和实践

###### eval函数（魔鬼）

> eval()不但混淆语境还很危险，总会有比他更好，更清晰，更安全的另一种方案来写你的代码，因此尽量不要使用eval()函数。

###### this关键字

> 只在对象构造器，方法和设定的闭包中使用`this`关键字。`this`的语义在此有些误导。它时而指向全局对象（大多数时），时而指向调用者的定义域（在eval()中），时而指向DOM树中的某一个节点，（当用事件处理绑定到 HTML 属性上时），时而指向一个新创建的对象（在构造器中），还时而指向其它的一些对象（如果函数被 call() 和 apply() 执行和调用时）。

> 正因为它是如此的容易被搞错，请限制它的使用场景

* 在构造函数中
* 在对象的方法中（包括由此创建出的闭包内）

###### True和False:布尔值表达式

> 以下用作布尔表达式时均为False:

```
null
undefinded
''//空字符串
0// 数字0
```

> 以下用作布尔表达式时均为Ture

```
'0'//字符串‘0’
[] //空数组
{} //空对象
```

> 基于以上结论，我们可以把下面的代码

```javascript
if(x != null)
```
> 精简为：
```javascript
if(x)
```
> 同样，如果你想判断一个变量既不为null，也不是空字符串的话，不必用：

```javascript
if (x != null && x != '')
```

>只需要：

```javascript
if (x)
```

> 即可。 注意，有一些很容易搞错的布尔表达式。以下列举出一部分：

Boolean('0') == true
'0' != true
0 != null
0 == [] //特别注意，0 == false, [] == true, 但是 0 == []
0 == false
Boolean(null) == false // 这个也要特别注意
null != true
null != false
Boolean(undefined) == false
undefined != true
undefined != false
Boolean([]) == true
[] != true
[] == false
Boolean({}) == true
{} != true
{} != false
NaN != true
NaN != false
Boolean(NaN) == false

> 这里很容易混淆，最好自己多实践一下。能用if(x)来判断的，不一定能用if(x == true)来判断。 ###三目运算符 对于下面这种简单的true返回a,false返回b的判断：

```javascript
if(condition) {
    return a;
} else {
    return b;
}
```
> 可以采用三目运算符简写为：

```javascript
return (condition) ? a : b;
```

> 在生成HTML时，这种表达方式尤其有用：

```javascript
var cls = isFocused ? 'class="chk-focus"' : '';
var checkbox = '<input type="checkbox" />'
```

###### 逻辑运算符

> 由逻辑与(&&)和逻辑或(||)运算符连接的表达式会从左到右依次执行，直到遇到满足条件为止，因此逻辑或(||)运算符也可以当作默认值运算符来用。比如：

```javascript
function doSomething(jQuery) {
    var $;
    if (jQuery) {
        $ = jQuery;
    } else {
        $ = window.jQuery;
    }
    // other code
}
```
> 可以简写为：
```javascript
function doSomething(jQuery) {
    var $ = jQuery || window.jQuery;
}
```
> 逻辑与(&&)也可以做类似的使用（当满足左边条件时执行右边的语句）。比如
```javascript
if('function' == typeof pgvMain) {
    pgvMain();
}
```
> 可以简写为：
```javascript
'function' == typeof pgvMain && pgvMain();
```
####### 节点遍历操作

> 我们经常有类似这样的操作：获取一组节点，然后对这个节点数组（节点列表）进行遍历。通常代码是这样的：

```javascript
var divs = document.getElementsByTagName('div');
for (var i = 0; i < divs.length; i++) {
  doSomething(divs[i]);
}
```

> 这样的操作，假如获取节点长度(divs.length)的复杂度是O(n)，获取某个子节点的复杂度也是O(n)，则由于每次要计算节点长度，因而遍历一遍所有节点，这个算法的时间复杂度就为O(n^2)。用以下方法可降低时间复杂度：
```javascript
var divs = document.getElementsByTagName('div');
var size = divs.length;
for (var i = 0; i < size; i++) {
    doSomething(divs[i]);
}
```
> 这里先把节点长度存到一个局部变量中，以后每次循环不再计算节点长度，因此总的时间复杂度变为了O(n) + 1; 还可以用另一种方法

```javascript
var divs = document.getElementsByTagName('div');
for (var i = 0, div; div = divs[i]; i++) {
    doSomething(div);
}
```
> 这种算法由于完全不检查节点长度，只是每次循环的时候取出一个子节点，因此时间复杂度降低到了O(n)。
