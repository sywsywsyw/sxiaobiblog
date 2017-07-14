---
title: HTML标签学习
date: 2016-04-27 11:30:40
tags:
categories: HTML
---

###  <a href="http://www.w3school.com.cn/tags/tag_a.asp">HTML a 标签的属性</a>

* <a href="http://www.w3school.com.cn/tags/att_a_href.asp">HTML a 标签的 href 属性</a>

* <a href="http://www.w3school.com.cn/tags/att_a_type.asp">HTML a 标签的 type 属性</a>

* <a href="http://www.w3school.com.cn/tags/att_a_download.asp">HTML a 标签的 download 属性</a>
 > 只有 Firefox 和 Chrome 支持 download 属性。
 > download里面的属性值为用户想要下载图片的名字 可以留空

```html
 <a href="/images/myw3schoolimage.jpg" download="w3logo">
```

* <a href="http://www.w3school.com.cn/tags/att_a_target.asp">HTML a 标签的 target 属性</a>
```
_blank	在新窗口中打开被链接文档。
_self	默认。在相同的框架中打开被链接文档。
_parent	在父框架集中打开被链接文档。
_top	在整个窗口中打开被链接文档。
framename	在指定的框架中打开被链接文档。
```
* <a href="http://www.w3school.com.cn/tags/att_a_name.asp">HTML a 标签的 name 属性</a>
  
  > name 属性用于指定锚（anchor）的名称。

```html
<ul>	
<li><a href="#C1">第一章</a></li>
<li><a href="#C2">第二章</a></li>
</ul>
```

<h2><a name="C1">第一章</a></h2>
<p>本章讲解的内容是 ... ...</p>

<h2><a name="C2">第二章</a></h2>
<p>本章讲解的内容是 ... ...</p>

```  

* <a href="http://www.w3school.com.cn/tags/att_a_charset.asp">HTML a 标签的 charset 属性</a>
 
 > a 标签的 charset 属性用于指定作为链接目标的文档中所使用的字符编码。charset 属性的值必须是标准字符集的名称，例如 "UTF-8"，默认值是 "ISO-8859-1"。
 
 > 主流的浏览器几乎都不支持 charset 属性。

```html
<a charset="gb2312" href="">charset</a>
```

* <a href="http://www.w3school.com.cn/tags/att_a_hreflang.asp">HTML a 标签的 hreflang 属性</a>

```html
<a href="http://www.w3school.com.cn" hreflang="zh">W3School</a>
```
* <a href="http://www.w3school.com.cn/tags/att_a_coords.asp">HTML a 标签的 coords 属性</a>

 > coords 属性与 shape 属性配合，可以规定 object 或 img 元素中链接的尺寸、形状和位置。注释：左上角的坐标是 0,0。

 > 只有 Firefox 和 Opera 支持 coords 属性。

```html
<object data="planets.gif" alt="Planets" type="image/gif" usemap="#Map1">
	<map name="Map1">
		<a href="sun.htm" shape="rect" coords="0,0,110,260">Sun</a>
		<a href="mercur.htm" shape="circle" coords="129,161,10">Mercury</a>
		<a href="venus.htm" shape="circle" coords="180,139,14">Venus</a>
	</map>
</object>
```
* <a href="http://www.w3school.com.cn/tags/att_a_shape.asp">HTML a 标签的 shape 属性</a>

* <a href="http://www.w3school.com.cn/tags/att_a_media.asp">HTML a 标签的 media 属性</a>

 >  media 属性规定目标 URL 是为什么类型的媒介/设备进行优化的。
 > 该属性用于规定目标 URL 是为特殊设备（比如 iPhone）、语音或打印媒介设计的。
 > 该属性可接受多个值。
 > 只能在 href 属性存在时使用。

```html
<a href="att_a_media.asp?output=print" media="print and (resolution:300dpi)">打开用于打印的 media 属性页面</a>
```

* <a href="http://www.w3school.com.cn/tags/att_a_rel.asp">HTML a 标签的 rel 属性</a>

 > a 标签的 rel 属性用于指定当前文档与被链接文档的关系。
 > 从源到目标的关系是移动到下一个文档，而从目标到源的关系则是返回前一个文档。

```html
<a rel="friend" href="http://www.w3c.com/">w3c</a>
```

* <a href="http://www.w3school.com.cn/tags/att_a_rev.asp">HTML a 标签的 rev 属性</a>

 > a 标签的 rev 属性用于指定当前文档与被链接文档的关系。
 > 从源到目标的关系是移动到下一个文档，而从目标到源的关系则是返回前一个文档。

```html
<a rev="friend" href="http://www.w3c.com/">w3c</a>
```


### <a href="http://www.w3school.com.cn/tiy/t.asp?f=html_abbr">HTML abbr 简称 缩写 标签</a>
  > <abbr> 标签指示简称或缩写，比如 "WWW" 或 "NATO",通过对缩写进行标记，您能够为浏览器、拼写检查和搜索引擎提供有用的信息。
  > 提示：可以在 <abbr> 标签中使用全局的 title 属性，这样就能够在鼠标指针移动到 <abbr> 元素上时显示出简称/缩写的完整版本。

```html
The <abbr title="People's Republic of China">PRC</abbr> was founded in 1949.
```
### <a href="http://www.w3school.com.cn/tags/tag_acronym.asp">HTML acronym 首字母缩略 标签(html5不支持)</a>
 > HTML5 中不支持 <acronym> 标签。请使用 <abbr> 标签代替。

```html
<acronym title="World Wide Web">WWW</acronym>
```

### <a href="http://www.w3school.com.cn/tags/tag_address.asp">HTML address 地址 标签</a>

<address> 标签定义文档或文章的作者/拥有者的联系信息。
如果 <address> 元素位于 <body> 元素内，则它表示文档联系信息。
如果 <address> 元素位于 <article> 元素内，则它表示文章的联系信息。
<address> 元素中的文本通常呈现为斜体。大多数浏览器会在 address 元素前后添加折行。


### <a href="http://www.w3school.com.cn/tags/tag_area.asp">HTML applet 小程序 标签(html5不支持)</a>

<area> 标签定义图像映射中的区域（注：图像映射指得是带有可点击区域的图像）。
area 元素总是嵌套在 <map> 标签中。
注释：<img> 标签中的 usemap 属性与 map 元素 name 属性相关联，创建图像与映射之间的联系。

HTML 与 XHTML 之间的差异
在 HTML 中，<area> 没有结束标签。
在 XHTML 中，<area> 必须正确地关闭。

### <a href="http://www.w3school.com.cn/tags/tag_article.asp">HTML article 文章 标签</a>

<article> 标签规定独立的自包含内容。
一篇文章应有其自身的意义，应该有可能独立于站点的其余部分对其进行分发。
<article> 元素的潜在来源：
论坛帖子
报纸文章
博客条目
用户评论

```html
<article>
  <h1>Internet Explorer 9</h1>
  <p>Windows Internet Explorer 9（简称 IE9）于 2011 年 3 月 14 日发布.....</p>
</article>
```

### <a href="http://www.w3school.com.cn/tags/tag_aside.asp">HTML aside 侧栏 标签</a>

<aside> 的内容可用作文章的侧栏。

### <a href="http://www.w3school.com.cn/tags/tag_audio.asp">HTML audio 音频 标签</a>

<audio> 标签定义声音，比如音乐或其他音频流。
可以在开始标签和结束标签之间放置文本内容，这样老的浏览器就可以显示出不支持该标签的信息。

<audio src="someaudio.wav">
您的浏览器不支持 audio 标签。
</audio>

### <a href="http://www.w3school.com.cn/tags/tag_b.asp">HTML b 粗体文本 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_base.asp">HTML base 规定页面所有的链接 在页面header头部放一个 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_basefont.asp">HTML basefont 规定页面上的默认字体颜色和字号：只有 Internet Explorer 支持 basefont 标签。应该避免使用该标签。 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_bdi.asp">HTML bdi 标签 把用户名从周围的文本方向设置中隔离出来： </a>
 > bdi 指的是 bidi 隔离。
  bdi 标签允许您设置一段文本，使其脱离其父元素的文本方向设置。
  在发布用户评论或其他您无法完全控制的内容时，该标签很有用。

### <a href="http://www.w3school.com.cn/tags/tag_bdo.asp">HTML bdo 标签 bdo 元素可覆盖默认的文本方向。 dir	ltr rtl</a>  

### <a href="http://www.w3school.com.cn/tags/tag_big.asp">HTML big 标签   big 标签呈现大号字体效果。</a>

### <a href="http://www.w3school.com.cn/tags/tag_blockquote.asp">HTML blockquote 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_body.asp">HTML body 标签 body 元素定义文档的主体。</a>

### <a href="http://www.w3school.com.cn/tags/tag_br.asp">换行</a>

### <a href="http://www.w3school.com.cn/tags/tag_button.asp">HTML button 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_canvas.asp">HTML canvas 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_phrase_elements.asp">HTML em strong dfn code samp kbd var cite 标签</a>
 > <em>	把文本定义为强调的内容。
 > <strong>	把文本定义为语气更强的强调的内容。

### <a href="http://www.w3school.com.cn/tags/tag_col.asp">HTML col 标签 col 元素为表格中的三个列规定了不同的对齐方式：</a>

### <a href="http://www.w3school.com.cn/tags/tag_datalist.asp">HTML datalist 标签 下面是一个 input 元素，datalist 中描述了其可能的值：所有主流浏览器都支持 <datalist> 标签，除了 Internet Explorer 和 Safari。</a>

### <a href="http://www.w3school.com.cn/tags/tag_dl.asp">HTML dl 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_dt.asp">HTML dt 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_dd.asp">HTML dd 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_embed.asp">HTML embed 标签 embed 标签定义嵌入的内容，比如插件。</a>

### <a href="http://www.w3school.com.cn/tags/tag_figcaption.asp">HTML figcaption 标签 用作文档中插图的图像，带有一个标题</a>

### <a href="http://www.w3school.com.cn/tags/tag_figure.asp">HTML figure 标签 用作文档中插图的图像：</a>

### <a href="http://www.w3school.com.cn/tags/tag_footer.asp">HTML 页脚 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_form.asp">HTML form 标签 表单提交</a>

### <a href="http://www.w3school.com.cn/tags/tag_frame.asp">TML frame 标签 引入一个框架</a>

### <a href="http://www.w3school.com.cn/tags/tag_frameset.asp">TML frameset 标签 框架集</a>

### <a href="http://www.w3school.com.cn/tags/tag_hn.asp">TML h1-h6 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_head.asp">TML head 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_header.asp">TML header 标签 对主页的描述 h5新标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_hr.asp">HTML hr 标签 被水平线分隔的标题和段落：</a>

### <a href="http://www.w3school.com.cn/tags/tag_i.asp">HTML i 标签 斜体</a>

### <a href="http://www.w3school.com.cn/tags/tag_iframe.asp">HTML iframe 标签</a>

### <a href="http://www.w3school.com.cn/tags/tag_img.asp">HTML img 标签</a>
