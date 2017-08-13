---
title: 网页转为MD
date: 2017-03-06
tags:
categories: 工具
---
------

# 转载

<!-- more -->

# 【开源】2md：将复制的内容、网页转成 markdown

> 如果一个 Markdown 编辑器不能解决问题，那么就用两个编辑器。

作为一个作者、程序员，兼知名的 markdown 程序员，我总是要在 Markdown、HTML、PDF 各种格式之间进行转换。

因为日常工作的一些使用需要，我也创建了各种的轮子：

如 ebook-boilerplate基于 markdown 一步生成电子书: 支持PDF、Mobi、EPUB格式。

如 MDPub，用于微信公众号的 markdown 编辑器，主要是用于提供代码高亮：

![](http://img.mp.itc.cn/upload/20170418/f64c050effbc432292e5be6a1897c5be_th.jpeg)

MDPub 截图

今天，我修复一个 MDPub 的 bug 时，突然意识到我也有将一篇文章转为 Markdown 的需要。

2md

以前，当我需要将 HTML 转为 Markdown 的时候，我会使用 to-markdown 的 Demo 网页，来转换相应的 HTML 为 Markdown。可是，这意味着我需要我复制到 HTML，才能转为 Markdown。

因此，我便想着：**如果可以直接用鼠标选中，然后 Ctrl + C、Ctrl + V 的话，就更简单了。**

而，实际上，我只需要一个 WYSIWYG 编辑器，然后再将内容转为 Markdown 就可以了。

因此，就有了 2md：

![](http://img.mp.itc.cn/upload/20170418/16e62d85ab934db9a5d5553299db0982_th.jpeg)

2MD 截图

一如即往的，保持了简洁的风格。并且，它的代码也足够的简单：

1.  tinymce.init({

2.  selector: 'textarea#input',

3.  height: 500,

4.  menubar: false,

5.  statusbar: false,

6.  toolbar: ['code'],

7.  plugins: [

8.  'advlist autolink lists link image charmap print preview anchor',

9.  'searchreplace visualblocks code fullscreen',

10.  'insertdatetime media table contextmenu paste code'

11.  ],

12.  setup: function(editor) {

13.  editor.on('change', function(e) {

14.  varcontent = tinymce.get('input').getContent();

15.  varmd = toMarkdown(content);

16.  $("#output").val(md);

17.  });

18.  }

19.  });

21.  $('document').ready(function() {

22.  newClipboard('.btn');

23.  });

而，我们所做的便是从网页，或者编辑器里直接复制内容，粘贴到左侧的编辑器里：

如 MacDown

![](http://img.mp.itc.cn/upload/20170418/20ab09c3ee5e4a85afa423377a10a1cc_th.jpeg)

2MD MacDown

又或者是直接对网页进行复制：

![](http://img.mp.itc.cn/upload/20170418/ffd90d9dd6a3471a837877cd6029e7f2_th.jpeg)

2MD WebSite

说了，这么多，你要来试试吗？

GitHub: https://github.com/phodal/2md