---
title: Atom编辑器安装及使用基础
date: 2018-01-01T00:00:00.000Z
tags: WebStrom
categories: 工具
---

--------------------------------------------------------------------------------

1、登录官网，认准https://www.jetbrains.com/webstorm/，其他的百度出来的什么鬼下载地址可能存在捆绑，一律不鸟；

2、点击下载，选择适合的系统版本（window、linux、mac）；

3、双击运行（基本就是无脑next），完毕。

webstorm激活

webstorm更新很快，各版本的破解需要时间，同时只适合对应的版本，这里下载的webstorm是2017.1.1，采用JetBrains 授权服务器作为激活方式，详情参考此网址http://idea.imsxm.com/，激活时选择License server,填入http://idea.imsxm.com/，点击Active则激活完成（在线激活有一个过期时间，这个时间一过就必须再次联网授权服务器请求激活）。

webstorm汉化

汉化找的也是webstorm的2017.1.1版，网址为数码资源网：http://www.smzy.com/smzy/down318439.html#a2，打开网址拉到最下才是正确的下载地址，直接讲汉化包里面的resources_cn.jar复制到.\Webstorm\lib目录则汉化完成（大部分汉化，但不影响使用）。

1、在本站下载安装Webstorm 2017汉化包.

2、将.\Webstorm 2017.1\lib目录下的resources_en.jar文件复制出来，并更名为resources_cn.jar。

3、双击打开resources_cn.jar(注意是打开而不是解压出来)，将下载的汉化包zh_CN目录下的所有文件拖到刚才打开的resources_cn.jar文件内的messages目录中，并保存。

4、将resources_cn.jar文件复制回.\Webstorm\lib目录。或是直接讲汉化包里面的resources_cn.jar复制到.\Webstorm\lib目录即可.

5、汉化完毕，重新打开Webstorm就可以显示中文。

Webstorm汉化补丁注意事项：

如果打开后显示乱码，请先删除resources_cn.jar，然后打开Webstorm，在菜单上依次选择

File -> Settings -> Appearance&Behavior -> Appearance -> 选中Override default fonts by(not recommended)

Name: Microsoft YaHei (选择任意中文字体)

然后将resources_cn.jar 复制到 .\lib 目录，重新打开Webstorm 就能正常显示中文了

## 网站HTML模版突然变成写一行代码就空一行

> 最近使用ftp上传 老出现诡异的代码 https://zhidao.baidu.com/question/362896057092145932.html

这个以前遇到过，跟上传到服务器的时候选择的 上传模式有关系。
上传ftp的时候可以在工具上选择
传输模式设置为二进制(图象)

