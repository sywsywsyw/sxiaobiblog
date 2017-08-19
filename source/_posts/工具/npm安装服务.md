---
title: npm安装服务
date: 2017-08-15 08:45:47
tags:
categories: 工具
---
------

<!-- more -->
## git

* 验证
```bash
git --version
```

## node

* 验证
```bash
node -v 得到版本号
npm -v  得到版本号
```

## 安装服务(如果npm无法使用可以用cnpm代理)

### http-server
```bash
npm install -g http-server
```

### cnpm
```bash
npm install -g cnpm
```
* 验证
```bash
cnpm -v
```
### sass
> CSS 的预处理程序 世界上最成熟、最稳定、最强大的专业级CSS扩展语言！
> 。CSS预处理器为CSS增加一些编程的特性，无需考虑浏览器的兼容性问题，例如你可以在CSS中使用变量、简单的逻辑程序、函数等等在编程语言中的一些基本特性，可以让你的CSS更加简洁、适应性更强、可读性更佳，更易于代码的维护等诸多好处。著作权归作者所有。
商业转载请联系作者获得授权,非商业转载请注明出处。

```bash
cnpm install -g node-sass
```
* 验证
```bash
node-sass -v
```
* 使用
```bash
node-sass -w index.scss index.css --output-style expanded
node-sass -w  index.scss index.css --output--style expanded  --source-map  map  //最后的map是自定义的文件
```
sass官方 https://www.sass.hk/
sass文档 http://sass.bootcss.com/docs/sass-reference/
sass学习 http://www.w3cplus.com/sassguide/

### bower

> 是一个客户端技术的软件包管理器,它可用于搜索、安装和卸载如JavaScript、HTML、CSS之类的网络资源


```bash
npm install -g bower
```
* 验证
```bash
bower -v
```

```bash
npm install -g bower
```
* 验证
```bash
bower -v
```
* 使用
```html
<!-- bower:css -->
<!-- endbower -->
</head>
<body>
<!-- bower:js -->
<!-- endbower -->
```

```bash
bower init
name     jd  项目名字
description   jd index for weixin
main file index.html  主要文件
keywords mobile.jingdong
authors 作者
license wiT
homcapge
scl currcntly installed componcnts as dcpcndcncies  NO   如果项目中有了 就yes
y
n
y

bower install jquery  --save
bower install bootstrap  --save
bower install touch --save
npm install wiredep  --save


node
出来一个> require('wiredep')({ src: 'index.html' });
拿到别人的index.html  bower.json
运行bower install
bower install 在官网注册的库(jqery)  --save
安装一个库，把库作为依赖项写入bower.json
http://www.wangzhi.com   --save
引入一个bower库中没有的别的地方的库
```
bower文档 https://bower.io/

### wiredep

> 执行grunt wiredep命令 在index.html文件会把默认dependencies依赖中的组件自动注入到下面标签中去。

```bash
npm install wiredep  --save
```

wiredep文档 http://blog.csdn.net/itpinpai/article/details/48269825

### gulp-cli
```bash
npm install -g gulp-cli
```
* 验证
```bash
gulp -v
```

### grunt-cli
```bash
npm install -g gulp-cli
```

### gulp-cli
```bash
npm install -g gulp-cli
```
* 验证
```bash
gulp -v
```

### yo
```bash
npm install -g yo
```
* 验证
```bash
yo -v
```

### yo
```bash
npm install -g yo
```
* 验证
```bash
yo -v
```

### generator-webapp
```bash
npm install -g generator-webapp
```

### ffmpeg

* 使用
> 用cmd切换到qqmuic/musics
> node test.js
> 歌曲 名字不能有空格
> ffprobe -v quiet -print_format json -show_format 1.mp3
