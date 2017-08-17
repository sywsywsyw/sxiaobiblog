---
title: npm安装服务
date: 2017-08-15 08:45:47
tags:
categories:
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
### node-sass 
```bash
cnpm install -g node-sass 
```
* 验证
```bash
node-sass -v 
```
* 使用
>（1）进入课程/css3
>（2）index.scss
>（3）打开cmd  cd  c:\users\name\desktop\课程\css3
>（4）node-sass -w index.scss index.css --output-style expanded
> node-sass -w  index.scss index.css --output--style expanded  --source-map  map  最后的map是自定义的文件
>（5）ctrl+c两次，退出

### bower
```bash
npm install -g bower
```
* 验证
```bash
bower -v
```

### bower
```bash
npm install -g bower
```
* 验证
```bash
bower -v
```
* 使用
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

<!-- bower:css -->
<!-- endbower -->
</head>
<body>
<!-- bower:js -->
<!-- endbower -->
node
出来一个> require('wiredep')({ src: 'index.html' });
拿到别人的index.html  bower.json 
运行bower install
bower install 在官网注册的库(jqery)  --save
安装一格库，把库作为依赖项写入bower.json
http://www.wangzhi.com   --save 
引入一个bower库中没有的别的地方的库
```

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

