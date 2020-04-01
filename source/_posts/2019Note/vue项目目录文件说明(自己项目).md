---
title: vue项目目录文件说明(自己项目)
date: 2019-04-01
tags: note
categories: 2019Note
---

https://www.jianshu.com/p/dcde5ab4cfd9

> 使用dos的tree命令输出文件夹树 http://www.cnblogs.com/dkplus/p/8487330.html
用dos的tree命令就可以实现文件夹树状图的输出，不过目前仅能输出为.txt文件

> 方法如下：
开始->运行 输入cmd打开命令控制台
切换到你要显示的列表文件夹 比如 输入 d: 切换到d盘
输入 tree >c:\dirlist.txt就可以生成文件夹的树型列表
tree /f >c:\dirlist.txt 可以生成文件夹和文件的树型列表
这个时候就可以在c盘生成你要的文本了

<!-- more -->

```

目录文件说明   
├─dist                                     生产环境打包目录`npm run buil`
├─test                                     预发布环境（测试）打包目录`npm run test`
├─public                                   项目根目录      vuecli3构建基础模块--public
       favicon.ico
       index.html                              入口页面
├─src                                      项目源码目录    vuecli3构建基础模块--src
   │  App.vue                                  根组件 
   │  main.js                                  入口js
   │  
   ├─assets                                    项目公用资源目录（图片，ico）
   ├─config                                    项目公用配置目录
   │      api.js                                   接口文档合集
   │      axios.js                                 axios请求配置
   │      mock.js                                  mock数据
   │      reg.js                                   项目正则整理
   │      storage.js                               cookie.storage方法整理
   ├─router                                    项目路由目录
   │  │  index.js                                 路由主入口文件
   │  │  
   │  └─modules                                   路由模块
   │          artist.js                               艺术家路由.js
   │          artwork.js                              艺术品路由.js
   │          loginres.js                             登录注册路由.js
   │          
   ├─store                                      项目vuex目录
   │      index.js                                  vuex主文件
   │      
   └─views                                      项目页面模块目录
       ├─common                                     公用组件模块
       │  │  404.vue                                    公用组件404页面
       │  │  DywASearch.vue
       │  │  DywPage.vue                           
       │  │  Footer.vue                                 公用组件页面尾部
       │  │  Header.vue                                 公用组件页面头部
       │  │  
       │  └─images                                      公用组件图片存放
       │  
       ├─index                                      页面主模块
       │      Index.vue                                 index.vue       
       │  
       ├─home                                    首页模块
       │  
       └─模块name                                模块
       │  ├─comments                                模块组件
       │  ├─css                                      模块样式     
       │  ├─js                                           模块逻辑js
       │  └─images                                  模块图片
       │  
└─ 
├ .editorconfig                                  
├ .env                                    配置生产环境   
├ .env.test                               配置测试环境
├  .gitignore
├ babel.config.js                         babel 
├ package-lock.json        
├ package.json                            npm包配置文件，里面定义了项目的npm脚本，依赖包等信息
├ README.md
├ vue.config.js                           本地跨域代理
```

