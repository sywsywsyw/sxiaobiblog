---
title: hexo疑难问题
date: 2017-08-14 13:43:45
tags:
categories: HEXO
---

# 解决hexo d命令提交部署博客发生的TaskCanceledException异常

## 起因

今天使用hexo d命令部署博客的时候发生了下面的异常：

```bash
    Fatal: TaskCanceledException encountered.
   ▒▒ȡ▒▒һ▒▒▒▒▒▒
bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': Invalid argument
FATAL Something's wrong. Maybe you can find the solution here: http://hexo.io/docs/troubleshooting.html
Error: Fatal: TaskCanceledException encountered.
   ��ȡ��һ��������
bash: /dev/tty: No such device or address
error: failed to execute prompt script (exit code 1)
fatal: could not read Username for 'https://github.com': Invalid argument

    at ChildProcess.<anonymous> (E:\gitRep\hellofriday.github.com\node_modules\hexo-util\lib\spawn.js:37:17)
    at emitTwo (events.js:87:13)
    at ChildProcess.emit (events.js:172:7)
    at ChildProcess.cp.emit (E:\gitRep\hellofriday.github.com\node_modules\cross-spawn\lib\enoent.js:40:29)
    at maybeClose (internal/child_process.js:818:16)
    at Process.ChildProcess._handle.onexit (internal/child_process.js:211:5)
```
## 解决 

重新安装上传插件

为了能够使Hexo部署到GitHub上，需要安装一个插件：

```bash
$ npm install hexo-deployer-git --save
```
然后，执行下列指令即可完成部署：
```bash
$ hexo generate
$ hexo deploy
```
