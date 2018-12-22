---
title: Atom编辑器安装及使用基础
date: 2016-08-23T00:00:00.000Z
tags: atom
categories: 工具
---

--------------------------------------------------------------------------------

<!-- more -->

# 为什么选择使用Atom？

> Atom是GitHub推出的一款编辑器, 被称为21世纪的黑客编辑器.作为一个现代的代码编辑器，Atom 有着各种流行编辑器都有的特性，功能上非常丰富，支持各种编程语言的代码高亮(HTML / CSS / Javascript / PHP / Python / C / C++ / Objective C / Java / JSON / Perl / CoffeeScript / Go / Sass / YAML / Markdown 等等)、 与大多数其他编辑器相比，Atom的语言支持已经算是覆盖非常全面了。另外，它的代码补全功能（也叫Snippets） 也非常好用，你只需输入几个字符即可展开成各种常用代码，可以极大提高编程效率。

<!-- more -->

 chinese 汉化 pigments 显示颜色 color-picker 快捷颜色插件 vim-mode emmet

## 安装

[打开官方主页](https://atom.io/)

网页会自动判断你的操作系统, 给出其对应的下载按钮 ![Image text](https://raw.githubusercontent.com/PeterHo/images/master/blog/editor/atom/atom_1/linux-downloads.png)

## 基本使用

### 命令面板

Atom的很多功能学习和参考了其他优秀的编辑器, 命令面板就是其一. 当你第一次看到它时, 还以为在用Sublime呢 命令面板是Atom中最常用的功能之一, 当你在编辑器中使用快捷键Ctrl+Shift+P时, 就会看到它 ![Image text](https://raw.githubusercontent.com/PeterHo/images/master/blog/editor/atom/atom_1/command-palette.png) 在控制面板中可以输入Atom中和插件中定义的所有命令, 并且支持模糊搜索 比如说当你输入cboo时, 所有包含有这4个字符的命令就都列出来了 在列出的命令后还显示了此命令对应的快捷键(如果有的话)

## 设置窗口

自带可视化的设置界面是Atom使用很方便的原因之一, 而不像传统的编辑器那样需要手动修改配置文件.

![Image text](https://raw.githubusercontent.com/PeterHo/images/master/blog/editor/atom/atom_1/settings.png)

你可以使用下面三种方法来打开设置窗口

- 主菜单Edit->Preferences
- 在命令面板中输入命令Settings View:Open. 因为命令窗口支持模糊查询, 因此只需要输入svo, 就可以了
- 使用快捷键Ctrl+,

在设置窗口中可以设置和管理各种编辑器行为, 键盘快捷键, 插件, 主题等内容

## 设置窗口界面主题和代码高亮

Atom自带了4种窗口主题和8种代码高亮方式

可以通过设置窗口中的Themes页面来配置和修改

![Image text](https://raw.githubusercontent.com/PeterHo/images/master/blog/editor/atom/atom_1/theme.png)

## 安装插件

通过设置窗口Settings界面的Install选项中，可以搜索插件或者主题进行下载安装

![Image text](http://img.blog.csdn.net/20151212191447866)

## 常用的一些插件

### 1、simplified-chinese-menu

Atom的简体中文语言包，完整汉化，兼容所有已发布的版本Atom。

### 2、linter-js-standard

用来使javascript代码格式化。

### 3、emmet

这款插件是用来支持zend-coding，Emmet的前身是大名鼎鼎的Zen coding，如果你从事Web前端开发的话，对该插件一定不会陌生。它使用仿CSS选择器的语法来生成代码，大大提高了HTML/CSS代码编写的速度

### 4、autoclose-html

html标签自动比较。

### 5、atom-ternjs

该插件能对一个对象中拥有的对外提供的属性和方法都能通过suggest的形式提示出来，能对一个对象对外提供的接口有一个选择过程，可以理解为js代码自动提示。

### 6、atom-bootstrap3

bootstrap3代码提示插件。

### 7、autocomplete-paths

文件路径自动提示。

![Image text](http://upload-images.jianshu.io/upload_images/1980884-9aa1f194f81ff3ef.gif?imageMogr2/auto-orient/strip)

### 8、jquery-snippets

jquery代码提示，安装完之后要重新启动Atom。

### 9、autoprefixer

css代码前缀自动补全。

![Image text](http://upload-images.jianshu.io/upload_images/1980884-d4c97a1b1e7c2a86.gif?imageMogr2/auto-orient/strip)

### 10、color-picker

取色器。 右键单击并选择Color Picker，或者点击CMD-SHIFT-C/ CTRL-ALT-C打开它。目前读HEX，HEXa，RGB，RGBa，HSL，HSLa，HSV，HSVa，VEC3和VEC4颜色-并能在格式之间的转换。 它还检查Sass和LESS颜色变量。只需Color Picker用光标打开一个变量，它就会查找你的定义。从那里，您可以单击定义并直接转到定义的位置。

![Image text](http://upload-images.jianshu.io/upload_images/1980884-deb030a911e29e87.gif?imageMogr2/auto-orient/strip)

### 11、activate-power-mode

编写代码特效

![Image text](http://upload-images.jianshu.io/upload_images/1980884-f92385d3975ba2a1.png?imageMogr2/auto-orient/strip)

### 12、atom-ternjs

JS代码智能提示。

新增功能：增加了对ES5，6，ES7，Node.js，jQuery的支持，和更多的可扩展插件。

### 13、snippets

按tab键自动填充代码。

### 14、atom-beautify

代码美化 打开命令选项板，键入Beautify并运行Beautify Editor。 右键或者快捷键 'ctrl-alt-b'：'atom-beautify：美化编辑器' ![命令面板](https://i.github-camo.com/894f5500758f862aea9995f174a8a17a17db0b57/68747470733a2f2f636c6f75642e67697468756275736572636f6e74656e742e636f6d2f6173736574732f313838353333332f31363534323538332f31633864393735632d343038352d313165362d383330372d6533356466373433306131302e706e67) ![美化语言的命令](https://i.github-camo.com/1b0c8e9e1bbbf4af2d88d540a4405ab2f32c4227/68747470733a2f2f636c6f75642e67697468756275736572636f6e74656e742e636f6d2f6173736574732f313838353333332f32353737353538362f66336663376563342d333237652d313165372d383537362d3435653733356538303033322e676966) (<https://atom.io/packages/atom-beautify>)

#### 2、原生Markdown书写和预览

Markdown 是一种轻量级的「标记语言」，它的优点很多，目前也被越来越多的写作爱好者，撰稿者广泛使用。看到这里请不要被「标记」、「语言」所迷惑，Markdown 的语法十分简单。常用的标记符号也不超过十个，这种相对于更为复杂的HTML标记语言来说，Markdown可谓是十分轻量的，学习成本也不需要太多，且一旦熟悉这种语法规则，会有一劳永逸的效果。

Atom原生支持Markdown的书写和预览，这相较于Sublime的需要安装第三方Markdown插件使用起来还要优秀，由于时Github自家打造，Markdown语法当然也是与github语法完全同步。

使用快捷键 Ctrl + Shift + M 则可打开Markdown的预览界面。

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201604/2016042314061974900.png)](http://www.hangge.com/blog/cache/detail_1149.html)

Atom的markdown Preview官方效果图如下：

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201604/2016042314072625097.png)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 3、原生Git支持

作为一个程序员，Git无疑是一个版本控制神器。如果你编辑了你从GitHub上Pull代码，那么在编辑器的右下角或者菜单树中能直观的看到自己编辑代码的状态，当然还有其他很多功能。这个大家可以自行去摸索。

### 三，常用快捷键

Atom设置选项 keybindings 中列举了相当长的一份关于快捷键的绑定列表，你也可以自定义快捷键的配置文件，有相同的快捷键则会覆盖掉原有的，使用你自己设定的。下面是一些常用的快捷键：

Crtl+Shift+M 开启Markdown实时预览 Command+Shift+P 打开命令窗口，可以运行各种菜单功能 Command + T 快速多文件切换 Command + F 文件内查找和替换 Command + Shift + F 多文件查找和替换 Command + [ 对选中内容向左缩进 Command + ] 对选中内容向右缩进 Command + \ 显示或隐藏目录树 Crtl + m 相应括号之间，html tag之间等跳转 Crtl + Alt + B 格式化代码（需要安装atom-beautify） Crtl + ` 调起CLI命令行界面（需要安装terminal-panel）

### 四，常用的一些插件

Atom的常用插件基本上都在 Atom Packages 首页中能找到，选择热门的、下载量较多的适合自己需要的基本上都是正确的选择，下面列举一写比较好用的插件：

#### 1、minimap

minimap是一个预览全部代码的一个插件，同时能方便的移动到指定的文件位置。

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201604/2016042314082539950.png)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 2、atom-beautify

atom-beautify是一个格式化代码的插件，支持HTML, CSS, JavaScript, PHP, Python, Ruby, Java, C, C++, C#, Objective-C,CoffeeScript, TypeScript, SQL等多种语言。

- 安装后可以使用 Crtl + Alt + B 快捷键进行格式化。
- 也可以点击菜单"Packages"->"Atom Beautify"->"Beautify"进行格式化。

#### 3、emmet

emmet是HTML,CSS快速编写的神器,具体的使用可以参看emmet官网。

#### 4、autocomplete-* 系列

autocomplete-*系列包含各个语言的代码自动补全功能，你需要什么语言的就可以下载该语言相关的插件即可。

- autocomplete-paths：填写路径的时候有Sug提示
- autocomplete-php：php代码提示补全
- autocomplete-java：java代码提示补全

  [![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](https://i.github-camo.com/be24f52ffa9df28969b5114bb46ba099f8194701/68747470733a2f2f7261772e6769746875622e636f6d2f417a616b7572342f6175746f636f6d706c6574652d7068702f6d61737465722f6173736574732f696d672f64656d6f2e676966)](http://www.hangge.com/blog/cache/detail_1149.html)

  [![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](https://i.github-camo.com/5e1071f4b0acf2074a5a0d443a9e46e3e99b236a/68747470733a2f2f7261772e6769746875622e636f6d2f6b65736b696a752f6175746f636f6d706c6574652d6a6176612f6d61737465722f73637265656e73686f742e676966)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 5、pigments

pigments是项目文件中，样式显色显示的的插件。在Atom中的下载量可是相当的高。对于前端人员来讲还是很重要的一个插件。

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201604/2016042314092387296.gif)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 6、terminal-panel

用于执行命令并显示输出。打开终端面板快捷键：Ctrl + `

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](https://i.github-camo.com/08b164c6803467b8824a34ca9f52b6f2d1d6b2e6/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f74686564616e69656c2f7465726d696e616c2d70616e656c2f6d61737465722f7465726d696e616c2d64656d6f2e676966)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 7、docblockr

可以帮助我们方便快速地写注释。

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](https://i.github-camo.com/75520d0785add27aad25b9111d5fbfe49eb85214/68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f4e696b68696c4b616c6967652f646f63626c6f636b722f6d61737465722f7265736f75726365732f66756e6374696f6e2d74656d706c6174652e676966)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 8、javascript-snippets

让我们书写js时使用各种缩写，自动补全代码。

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](https://i.github-camo.com/530eafbaf5b2bc0e6cf78666bbdb339cd65bf713/68747470733a2f2f636c6f75642e67697468756275736572636f6e74656e742e636f6d2f6173736574732f3339383839332f333532383131382f66303763323037322d303738622d313165342d393365392d6363623133333938323465362e676966)](http://www.hangge.com/blog/cache/detail_1149.html)

#### 9、file-icons

让文件前面有彩色图片，使文件类型看得更加清除舒服。(如果使用着 seti-ui 主题，则体现不了效果哦)

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201701/201701311029097574.png)](http://www.hangge.com/blog/cache/detail_1149.html)

### 五、常用主题

Atom 的主题是分为UI主题和语法主题，默认情况下软件已经提供了好几套主题（有暗色调、也有亮色调）供我们使用。

- 在菜单"Atom"->"Preferences"->"Themes" 页面中可以分别切换 UI Theme 和 Syntax Theme
- 在菜单"Atom"->"Preferences"->"Install" 页面中可以搜索安装各种主题。

除了默认自带的主题，下面推荐几个优秀的Theme，大家可以自行安装。

## #

1，seti-ui + seti-syntax

每个文件前的icons是最大亮点

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201701/2017013111414287284.png)](http://www.hangge.com/blog/cache/detail_1149.html)

### 2，atom-material-ui + atom-material-syntax

颜色正

（1）暗色调

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201701/2017013111455655669.png)](http://www.hangge.com/blog/cache/detail_1149.html)

（2）亮色调

[![原文:Atom - 介绍和使用方法（好用的文本编辑器，代码提示高亮、Markdown）](http://www.hangge.com/blog_uploads/201701/2017013111460736360.png)](http://www.hangge.com/blog/cache/detail_1149.html)

原文出自：[www.hangge.com](http://www.hangge.com/) 转载请保留原文链接：<http://www.hangge.com/blog/cache/detail_1149.html>
