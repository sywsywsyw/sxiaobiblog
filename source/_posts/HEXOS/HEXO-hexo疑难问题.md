---
title: hexo疑难问题
date: 2016-08-15 13:43:45
tags:
categories: HEXOS
---
------

<!-- more -->

## 解决hexo d命令提交部署博客发生的TaskCanceledException异常

今天使用hexo d命令部署博客的时候发生了下面的异常：

```bash
#     Fatal: TaskCanceledException encountered.
#    ▒▒ȡ▒▒һ▒▒▒▒▒▒
# bash: /dev/tty: No such device or address
# error: failed to execute prompt script (exit code 1)
# fatal: could not read Username for 'https://github.com': Invalid argument
# FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
# Error: Fatal: TaskCanceledException encountered.
#    ��ȡ��һ��������
# bash: /dev/tty: No such device or address
# error: failed to execute prompt script (exit code 1)
# fatal: could not read Username for 'https://github.com': Invalid argument
#
#     at ChildProcess.<anonymous> (E:\gitRep\hellofriday.github.com\node_modules\hexo-util\lib\spawn.js:37:17)
#     at emitTwo (events.js:87:13)
#     at ChildProcess.emit (events.js:172:7)
#     at ChildProcess.cp.emit (E:\gitRep\hellofriday.github.com\node_modules\cross-spawn\lib\enoent.js:40:29)
#     at maybeClose (internal/child_process.js:818:16)
#     at Process.ChildProcess._handle.onexit (internal/child_process.js:211:5)
```
重新安装上传插件，为了能够使Hexo部署到GitHub上，需要安装一个插件：

```bash
$ npm install hexo-deployer-git --save
```
然后，执行下列指令即可完成部署：
```bash
$ hexo generate
$ hexo deploy
```
## 解决hexo 分类文件设置为 HEXO 出现路径报错问题

人家不然用这个文件分类那就别用，换成HEXOS不就好了啊。

## hexo目录乱码问题

今天设置目录老是乱码
错误：
![错误](/images/hexo乱码目录.png)![错误](/images/hexo乱码目录md.png)

正确:
![正确](/images/hexo目录正常.png)![正确](/images/hexo目录正常md.png)

对的 你没看错 hexo的标题不能进行跳级 比较严格

## hexo图片路径问题

我以前把图片放到`F:\github\hexo\.deploy_git\images`路径里面和网站设置的头像等等放一起，忽然有了`TaskCanceledException异常`问题，然后重新安装了上传git插件发现可能图片丢失了。

官方文档：
资源（Asset）代表 source 文件夹中除了文章以外的所有文件，例如图片、CSS、JS 文件等。比方说，如果你的Hexo项目中只有少量图片，那最简单的方法就是将它们放在 source/images 文件夹中。然后通过类似于 `![](/images/image.jpg) `的方法访问它们。
https://hexo.io/zh-cn/docs/asset-folders.html
