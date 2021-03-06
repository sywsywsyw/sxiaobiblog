---
title: Sublime Text使用技巧
date: 0000-00-00
tags: sublime
categories: 工具
---

--------------------------------------------------------------------------------

# Sublime插件：Markdown篇

<!-- more -->

 ![](http://upload-images.jianshu.io/upload_images/26219-29e0b5a286d79092.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

Sublime Text

如何安装插件详见：<https://packagecontrol.io/installation>

1. [MarkDown Editing](https://github.com/SublimeText-Markdown/MarkdownEditing)：支持Markdown语法高亮；支持Github Favored Markdown语法；自带3个主题。

  ![](http://upload-images.jianshu.io/upload_images/26219-acb1458822ef63e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  MarkDown Editing 界面

  ![](http://upload-images.jianshu.io/upload_images/26219-88170fc627d3078c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  主题选择

  **注：**如果你安装完之后，遇到了如下的[错误](https://github.com/SublimeText-Markdown/MarkdownEditing/issues/115)，那么你安装的时候可能开着一个Markdown文件，所以卸载完之后在不打开Markdown的情况下再次安装就可以解决了。

  ![](http://upload-images.jianshu.io/upload_images/26219-546efb46c571f42d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  Markdown.tmLanguage错误

# 这个自己用到了哦

1. [MarkdownPreview](https://github.com/revolunet/sublimetext-markdown-preview)：按`CTRL + B`生成网页HTML；在最前面添加`[TOC]`自动生成目录；

  ![](http://upload-images.jianshu.io/upload_images/26219-ba148bf2ae66a82b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  Markdown 生成HTML预览

2. [Markdown Extended](https://github.com/jonschlinkert/sublime-markdown-extended) + [Extends Monokai](https://github.com/jonschlinkert/sublime-monokai-extended)：不错的Markdown主题，支持对多种语言的高亮

  ![](http://upload-images.jianshu.io/upload_images/26219-1c131c4be3d76855.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  C语言语法高亮

3. [OmniMarkupPreviwer](http://theo.im/OmniMarkupPreviewer/)：**实时**在浏览器中预，而`MarkdownPreview`是需要手动生成的和F5的。览如果双屏的话，应该具有不错的体验。快捷键如下：

  - `Ctrl+Alt+O`: Preview Markup in Browser.
  - `Ctrl+Alt+X`: Export Markup as HTML.
  - `Ctrl+Alt+C`: Copy Markup as HTML.

    ![](http://upload-images.jianshu.io/upload_images/26219-9a865e2acb4843cc.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

    实时在浏览器中显示编辑的文档

4. [TableEditor](https://github.com/vkocubinsky/SublimeTableEditor)：Markdown中的表格书写体验真心不咋样，所有有人为这个开发了一个插件，具有较好的自适应性，会自动对齐，强迫症患者喜欢。 首先需要用`ctrl + shift + p`打开这个功能（Table Editor: Enable for current syntax or Table Editor: Enable for current view or "Table Editor: Set table syntax ... for current view"），然后就可以狂用`tab`来自动完成了~~~

  ![](http://upload-images.jianshu.io/upload_images/26219-256230846b591b50.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  用`tab`来自动完成表格间的切换和下一行表格的生成

5. [Markdown TOC](https://github.com/naokazuterada/MarkdownTOC)：编辑MD文件的时候可以查看自动生成，并且可以控制生产目录的层次，不过不会自动跳转。编辑的时候可以看看，如果需要生成的HTML具有超链接跳转的功能，还是用**MarkdownPreview**吧。

  ![](http://upload-images.jianshu.io/upload_images/26219-3fbd3982920df18a.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240/format/jpg)

  修改目录深度实时在MD文件中预览，不过这个用`CTRL+R`就可以产看，个人觉得不太实用

6. [SmartMarkdown](https://github.com/demon386/SmartMarkdown)：貌似是为Emacs用户打造的。



# [《转》12个Sublime Text使用技巧](http://www.cnblogs.com/hongmaju/p/6823583.html)

> 文为您提供Sublime Text编辑器的12个技巧和诀窍，深入挖掘这个看似简洁的代码编辑器，背后所隐藏的实现各种高级功能的无限可能。 

<!-- more -->

 _1) 选择 以下是一些Sublime Text选择文本的快捷键： Command + D 选中一个单词 Command + L 选中一行 Command + A 全选 Ctrl + Command + M 选中括号内所有内容 (编写CSS或JS时非常实用)Sublime Text还支持一次选中多行的操作，它可以显著提高您的工作效率。有几种方法来执行此功能：Command 按住Command键再点击想选中的行Command + Ctrl + G (选中部分文本时) 按此键选中所有相同文本Command + D (选中部分文本时) 直接选中下一次出现的该文本_

![](http://img.blog.csdn.net/20160513172312142?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

2) CSS排序

CSS属性的顺序一般不重要，因为无论何种顺序浏览器都能正确渲染。但排序所有的属性还是有助于代码的整洁。在Sublime Text中，选中CSS属性后按F5就可以按字母顺序排序。

![](http://img.blog.csdn.net/20160513172445658?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

也可以使用 CSSComb 等第三方插件，更详细的控制排序的方法。

3) 命令面板（Command Palette）

▼ 重命名文件

![](http://img.blog.csdn.net/20160513172558065?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

▼ 设置文件为HTML语法

![](http://img.blog.csdn.net/20160513172715364?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

▼ 插入代码片段

![](http://img.blog.csdn.net/20160513172809487?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

4) 切换标签页与工程

在同时打开多个标签页时，可以用以下的热键切换： Command + T 列出所有的标签页 Command + Shift + ] 下一标签页<br>
Command + Shift + [ 上一标签页 Command + Ctrl + P 切换侧边栏显示的工程

5) 跨文件编辑

同一个编辑操作可以在多个文件中同时重复。举个例子，多个文件中有同一段代码时，可用以下的步骤快速编辑： 1.按Command + Shift + F在Find框中输入待查找的代码。可按Command + E快速使用选择中的代码段。 2.在Where框中指定需要查找的文件范围，或填写表示查找目前打开的文件。 3.在Replace框中输入要替换成的代码，按Replace按钮批量替换。

![](http://img.blog.csdn.net/20160513172853804?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

6) 文件爬虫

按Command + R可以列出文档中所有的CSS选择器。可以选择并立刻跳转查看。这个操作比使用一般的"查找"功能快得多。

![](http://img.blog.csdn.net/20160513172936566?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

7) 拼写检查

如果你经常使用Sublime Text从事英文创作，那么启用拼写检查就非常有用处了。选择Preferences > Settings – User菜单，添加以下代码： "spell_check": true,

8) 增强侧边栏

SideBarEnhancements插件有效地改进了Sublime Text的侧边栏。安装插件后在侧边栏上点击右键，可以找到一下新功能：在资源管理器中打开、新建文件、新建文件夹、以...打开、在浏览器中打开。

![](http://img.blog.csdn.net/20160513173021832?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

9) 更换主题

Sublime Text的外观主题可以更换。Soda Theme就是一个不错的主题，可以在包管理器中安装。

![](http://img.blog.csdn.net/20160513173112932?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

如果要安装的主题并不在在线软件仓库中，也可以手动安装： 1.下载并解压缩主题包 2.点击菜单 Preferences > Browse Packages... 3.把主题文件夹复制到Packages文件夹中. 4.点击菜单 Preferences > Settings – Users 并加入以下代码："theme": "Soda Light.sublime-theme"

10) 更换Sublime Text程序图标

不仅主题可以更换，图标也可以。在Dribbble上有大量重新设计的Sublime Text精美图标。更换方法： 下载一个图标，有.icns格式的最好。如果没有，用iConvert转换之。 终端执行：open /Applications/Sublime\ Text.app/Contents/Resources/ 替换Sublime Text 3.icns或Sublime Text 2.icns文件。

11) 同步选项

如果在多台计算机上工作，同步选项设置应该是一个好主意。我们借用Dropbox完成这一任务。 首先在终端中运行以下命令上传设置文件：

1. mkdir $HOME/Dropbox/sublime-text-3/ mv "$HOME/Library/Application Support/Sublime Text 3/Packages" "$HOME/Dropbox/sublime-text-3/" mv "$HOME/Library/Application Support/Sublime Text 3/Installed Packages" "$HOME/Dropbox/sublime-text-3/"

然后在所有需要同步的计算机上运行以下命令下载设置：

1. DSTPATH="$HOME/Library/Application Support/Sublime Text 3"DROPBOX_PATH="$HOME/Dropbox/sublime-text-3" rm -rf "$DSTPATH/Installed Packages" rm -rf "$DSTPATH/Packages" mkdir -p "$DSTPATH" ln -s "$DROPBOX_PATH/Packages" "$DSTPATH/Packages" ln -s "$DROPBOX_PATH/Installed Packages" "$DSTPATH/Installed Packages"

12) 可点击的URL

使用小插件ClickableURLs可以让文件中的URL能够点击。
