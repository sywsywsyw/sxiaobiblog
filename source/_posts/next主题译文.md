---
title: next主题译文
date: 2017-09-09 10:41:41
tags:
categories:
---
------

<!-- more -->

＃------------------------------------------------- --------------
＃站点信息设置
＃------------------------------------------------- --------------

＃将你的favicon.ico放入`hexo-site / source /`目录。
favicon：/favicon.ico

＃设置默认关键字（使用逗号分隔）
关键字：“Hexo，NexT”

＃将rss设置为false以禁用Feed链接。
＃将rss设为空，以使用网站的Feed链接。
＃将rss设置为特定值，如果已经烧好了您的Feed。
RSS：

＃指定站点设置的日期
#since：2015

年份与作者之间的＃图标@Footer
authoricon：心

＃脚注`动力`和`主题信息'版权
版权：true


＃------------------------------------------------- --------------
＃SEO设置
＃------------------------------------------------- --------------

＃Canonical，在你的hexo中设置一个规范的链接标签，你可以使用它来做你的SEO的博客。
＃请参阅：https：//support.google.com/webmasters/answer/139066
＃提示：在打开此标记之前，请记住在hexo _config.yml（例如url：http://yourdomain.com）中设置您的URL
规范：真实

＃更改站点字幕上的标题层次结构（将是主要站点描述）以及所有Post /页面标题，以实现更好的SEO优化。
seo：虚假

＃如果为true，将添加site-subtitle到索引页面，添加到主hexo配置中。
＃subtitle：Subtitle
index_with_subtitle：false


＃------------------------------------------------- --------------
＃菜单设置
＃------------------------------------------------- --------------

＃在子目录（例如domain.tld / blog）中运行站点时，从链接值（/归档 - >归档）中删除主斜杠。
＃用法：`key：/ link / || icon`
＃键是菜单项的名称。如果这个菜单的翻译将用语言找到 - 这个翻译将被加载;如果没有 - 将使用密钥名称。关键是病例敏感。
＃在`||`之前的值是目标链接。
＃||`delimeter之后的值是FontAwesome图标的名称。如果未指定图标（有或没有分米），将加载问题图标。
菜单：
  家：/ ||家
  about：/ about / ||用户
  标签：/ tags / ||标签
  类别：/ categories / ||日
  档案：/档案/ ||档案
  时间表：/ schedule / ||日历
  sitemap：/sitemap.xml ||网站地图
  公共：/ 404 / ||心跳

＃启用/禁用菜单图标。
menu_icons：
  启用：true
  家：回家
  关于：用户
  类别：th
  标签：标签
  档案：档案
  公益：心跳

＃------------------------------------------------- --------------
＃方案设置
＃------------------------------------------------- --------------

＃方案
＃scheme：Muse
＃scheme：Gemini
方案：雾
＃scheme：双鱼座


＃------------------------------------------------- --------------
＃边栏设置
＃------------------------------------------------- --------------

＃社交链接。
＃用法：`键：永久链接|| icon`
＃Key是向最终用户显示的链接标签。
＃“``之前的值是DELTA的目标永久链接。
＃||`delimeter之后的值是FontAwesome图标的名称。如果未指定图标（有或没有分米），则会加载地球图标。
#social：
  #GitHub：https://github.com/yourname || github上
  ＃电子邮件：mailto：yourname@gmail.com ||信封
  #Google：https：//plus.google.com/yourname ||谷歌
  #Twitter：https://twitter.com/yourname ||推特
  #FB页面：https://www.facebook.com/yourname || Facebook的
  #VK组：https://vk.com/yourname || VK
  #StackOverflow：https://stackoverflow.com/yourname ||堆栈溢出
  #YouTube：https：//youtube.com/yourname || YouTube的
  #Instagram：https://instagram.com/yourname || Instagram的
  #Skype：skype：yourname？call | chat || Skype的

social_icons：
  启用：true
  icons_only：false
  转换：假

＃博客卷
#links_title：链接
#links_layout：block
#links_layout：inline
＃链接：
  #Title：http://example.com/

＃Sidebar头像
＃在主题目录（源/图像）：/images/avatar.gif
＃在网站目录（来源/上传）：/uploads/avatar.gif
#avatar：/images/avatar.gif

＃侧栏中的目录
TOC：
  启用：true

  ＃自动将列表号添加到toc。
  数字：真

  ＃如果为true，则如果标题宽度长于边栏宽度，则所有字都将放在下一行。
  包装：假

知识共享4.0国际许可证。
＃http://creativecommons.org/
＃可用：by | by-nc | by-nc-nd | by-nc-sa | by-nd | by-sa |零
#creative_commons：by-nc-sa
＃创作共用：

边栏：
  ＃侧栏位置，可用值：左|对
  位置：左
  #position：对

  ＃侧栏显示，可用值：
  ＃ - 自动发布帖子。默认。
  ＃ - 始终自动展开所有页面
  ＃ - 仅在点击侧边栏切换图标时隐藏展开。
  ＃ - 删除完全删除侧边栏，包括边栏切换。
  显示：帖子
  #display：永远
  #display：hide
  #display：remove

  ＃边栏从顶部菜单栏偏移像素。
  偏移量：12
  offset_float：12

  ＃侧栏中的顶部
  b2t：假

  ＃滚动b2中的百分比标签

＃滚动b2t按钮中的百分比标签
  scrollpercent：false

  ＃在窄视图下启用边栏
  onmobile：假


＃------------------------------------------------- --------------
＃帖子设置
＃------------------------------------------------- --------------

＃自动将页面滚动到<！ - more - >标记下的部分。
scroll_to_more：true

＃自动保存Cookie中每个帖子/页面上的滚动位置。
save_scroll：false

＃将主页中的说明自动摘录为序言文字。
excerpt_description：true

＃自动截图不推荐
＃请在帖子中使用<！ - more - >来准确控制摘录。
auto_excerpt：
  启用：false
  长度：150

＃发布元显示设置
post_meta：
  item_text：true
  created_at：true
  updated_at：false
  类别：真

＃发布字数显示设置
＃依赖关系：https：//github.com/willin/hexo-wordcount
post_wordcount：
  item_text：true
  字数：虚假
  min2read：false
  总计：假
  isolated_meta：true

＃Wechat订阅者
#wechat_subscriber：
  #enabled：true
  #qcode：/ path / to / your / wechatqcode ex。 /uploads/wechat-qcode.jpg
  #description：ex。订阅我的博客扫描我的公共微博帐号

＃ 奖励
#reward_comment：在此处发表评论
#wechatpay：/images/wechatpay.jpg
#alipay：/images/alipay.jpg
#bitcoin：/images/bitcoin.png

＃宣布职位上的执照
post_copyright：
  启用：false
  许可证：CC BY-NC-SA 3.0
  license_url：https://creativecommons.org/licenses/by-nc-sa/3.0/


＃------------------------------------------------- --------------
＃其他主题设置
＃------------------------------------------------- --------------

＃减少宽度窄的设备上的填充/边距缩进。
mobile_layout_economy：false

＃Android Chrome标头面板颜色（$ black-deep）。
android_chrome_color：“＃222”

＃自定义徽标。
＃!!目前只适用于默认计划。
＃选项：
＃enabled：[true / false] - 替换为特定图像
＃image：url of the image - 图片的网址
custom_logo：
  启用：false
  图片：

＃代码高亮主题
＃可用值：
＃normal |晚上|八十年代晚晚蓝色|夜晚明亮
＃https://github.com/chriskempson/tomorrow-theme
highlight_theme：正常


＃------------------------------------------------- --------------
＃字体设置
＃ - 在Google字体上查找字体（https://www.google.com/fonts）
＃ - 此处设置的所有字体将具有以下样式：
＃浅，浅斜体，正常，正常斜体，粗体，粗体斜体
＃ - 请注意，设置太多字体会导致网站运行缓慢
＃ - 介绍5.0.1
＃------------------------------------------------- --------------
字体：
  启用：true

  ＃Uri的字体主机。例如。 //fonts.googleapis.com（默认）
  主办：

  ＃在<body>元素上使用的全局字体设置。
  全球：
    ＃external：true将从主机加载该字体系列。
    外部：真
    家庭：Lato

  ＃标题的字体设置（h1，h2，h3，h4，h5，h6）
  ＃回退到`global`字体设置。
  标题：
    外部：真
    家庭：

  ＃帖子的字体设置
  ＃回退到`global`字体设置。
  帖子：
    外部：真
    家庭：

  ＃徽标的字体设置
  ＃回退到`global`字体设置。
  ＃“size”选项使用“px”作为单位
  商标：
    外部：真
    家庭：
    尺寸：

  ＃<code>和代码块的字体设置。
  代码：
    外部：真
    家庭：
    尺寸：


＃------------------------------------------------- --------------
＃第三方服务设置
＃------------------------------------------------- --------------

＃MathJax支持
mathjax：
  启用：false
  per_page：false
  cdn：//cdn.bootcss.com/mathjax/2.7.1/latest.js?config=TeX-AMS-MML_HTML或MML

＃韩支持文档：https：//hanzi.pro/
韩：虚假

＃Swiftype搜索API密钥
#swiftype_key：

＃百度分析ID
#baidu_analytics：

＃Duoshuo ShortName
#duoshuo_shortname：

＃Disqus
disqus：
  启用：false
  简称：
  计数：真

＃hypercomments
#hypercomments_id：

＃changyan
昌言：
  启用：false
  APPID：
  的AppKey：


＃缬氨酸
＃你可以从https://leancloud.cn获取你的appid和appkey
＃更多信息请打开https://github.com/xCss/Valine
缬氨酸：
  启用：false
  appid：＃你的leancloud应用程序appid
  appkey：＃你的leancloud应用程序appkey
  通知：false＃邮件通知器，https://github.com/xCss/Valine/wiki
  验证：false＃验证码
  占位符：注释输入占位符

＃支持youyan评论系统。
＃你可以从http://www.uyan.cc得到你的uid
#youyan_uid：你的uid

＃支持LiveRe评论系统。
＃你可以从https://livere.com/insight/myCode（一般网站）获取你的uid
#livere_uid：你的uid

＃百度分享
＃可用值：
＃按钮|滑动
＃警告：百度分享不支持https。
#baidushare：
## type：button

＃分享
＃这个插件在中国比较有用，确保你知道如何使用它。
＃您可以在官方网站：http://www.jiathis.com/找到使用指南。
＃警告：姬
