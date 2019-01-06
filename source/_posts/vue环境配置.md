---
title: vue环境
date: 2018-03-07 21.58
tags: 笔记
categories: Vue
---

为什么要用vue?

渐进式、轻量、声明式、高效、易用、响应式

什么是渐进式？
可以部分使用vue,也可以使用vue的一部分.
声明式渲染 - 组件系统 - 客户端路由 - 大规模状态管理 - 构建工具

<!-- more -->


## 环境安装

* 必须拥有node 和 npm  -v查看版本号

全局安装 vue-cli

$ npm install -g vue-cli 

$ vue init webpack vuecliTest

$ npm install

$ npm run dev 启用一个server


http://www.runoob.com/vue2/vue-install.html


1）安装淘宝cnpm镜像
$ npm install -g cnpm –registry=http://registry.npm.taobao.org

2）安装vue-cli
$ cnpm install -g vue-cli
测试安装：
$ vue -V
2.9.3

```
$ vue init webpack test   初始化第一个项目（webpack方式） (项目名称不能包含大写字母)

$ cd test
$ cnpm install    生成node-modules: 因为各个模板间都是相互依赖的，所以要安装依赖，在命令行输入cnpm install ,你会发现在已经创建的项目结构里面会多出一个node_modules的文件夹，里面就是刚才安装的所有依赖。
$ cnpm run dev    运行第一个程序:运行成功后会在浏览器中直接打开
 DONE  Compiled successfully in 4388ms

> Listening at http://localhost:8080
```

```
? Project name (test) 0327
? Project name 0327
? Project description (A Vue.js project)
? Project description A Vue.js project
? Author (sywsywsyw <347363545@qq.com>)
? Author sywsywsyw <347363545@qq.com>
? Vue build standalone
? Install vue-router? (Y/n) y   路由
? Install vue-router? Yes   
? Use ESLint to lint your code? (Y/n) no   ESlint规范  
? Use ESLint to lint your code? no 
? Pick an ESLint preset (Use arrow keys)  no
? Pick an ESLint preset Standard
? Set up unit tests (Y/n) no
? Set up unit tests no
? Pick a test runner (Use arrow keys)
? Pick a test runner jest
? Setup e2e tests with Nightwatch? (Y/n) no   单元测试
? Setup e2e tests with Nightwatch? no
? Should we run `npm install` for you after the project has been created? (reco
? Should we run `npm install` for you after the project has been created? (reco
mmended) npm
Running eslint --fix to comply with chosen preset rules...
# ========================

> 0327@1.0.0 lint F:\vue0326\test
> eslint --ext .js,.vue src test/unit test/e2e/specs "--fix"

# Project initialization finished!
# ========================

To get started:

  cd test
  npm run dev

Documentation can be found at https://vuejs-templates.github.io/webpack


？项目名称（测试）0327
？项目名称0327
？项目描述（一vue.js项目）
？项目描述一vue.js项目
？作者（sywsywsyw＜347363545 @ QQ。COM >）
？作者sywsywsyw 347363545@qq.com > <
？Vue公司建立独立
？安装Vue路由器？（y／n）y
？安装Vue路由器？是的
？使用ESLint皮棉代码？（y／n）y
？使用ESLint皮棉代码？是的
？选择一个ESLint预设（使用箭头键）
？选择预先设定的标准
？设置单元测试（y / n）y
？设置单元测试是
？选择测试运行器（使用箭头键）
？选择一个测试跑步者的笑话
？Nightwatch建立端到端的测试？（y／n）y
？Nightwatch建立端到端的测试？是的
？我们应该运行` NPM安装`您后，项目被创建？（Reco
？我们应该运行` NPM安装`您后，项目被创建？（Reco
新公共管理的介绍）
```

build 文件夹   webpack配置文件
config 文件夹   项目开发配置
node_modules 文件夹 npm包管理
src 文件夹   源代码
static 文件夹  静态文件目录 

.
|-- build                            // 项目构建(webpack)相关代码
|   |-- build.js                     // 生产环境构建代码
|   |-- check-version.js             // 检查node、npm等版本
|   |-- dev-client.js                // 热重载相关
|   |-- dev-server.js                // 构建本地服务器
|   |-- utils.js                     // 构建工具相关
|   |-- webpack.base.conf.js         // webpack基础配置
|   |-- webpack.dev.conf.js          // webpack开发环境配置
|   |-- webpack.prod.conf.js         // webpack生产环境配置
|-- config                           // 项目开发环境配置
|   |-- dev.env.js                   // 开发环境变量
|   |-- index.js                     // 项目一些配置变量
|   |-- prod.env.js                  // 生产环境变量
|   |-- test.env.js                  // 测试环境变量
|-- src                              // 源码目录
|   |-- components                     // vue公共组件
|   |-- store                          // vuex的状态管理
|   |-- App.vue                        // 页面入口文件
|   |-- main.js                        // 程序入口文件，加载各种公共组件
|-- static                           // 静态文件，比如一些图片，json数据等
|   |-- data                           // 群聊分析得到的数据用于数据可视化
|-- .babelrc                         // ES6语法编译配置
|-- .editorconfig                    // 定义代码格式
|-- .gitignore                       // git上传需要忽略的文件格式
|-- README.md                        // 项目说明
|-- favicon.ico 
|-- index.html                       // 入口页面
|-- package.json                     // 项目基本信息
.


出现报错
```
> onevue@1.0.0 dev C:\Users\SUI\Desktop\vue0307\onevue
> webpack-dev-server --inline --progress --config build/webpack.dev.conf.js

'webpack-dev-server' ▒▒▒▒▒ڲ▒▒▒▒ⲿ▒▒▒Ҳ▒▒▒ǿ▒▒▒▒еĳ▒▒▒
▒▒▒▒▒▒▒▒▒ļ▒▒▒
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! onevue@1.0.0 dev: `webpack-dev-server --inline --progress --config build/webpack.dev.conf.js`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the onevue@1.0.0 dev script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\SUI\AppData\Roaming\npm-cache\_logs\2018-03-07T12_22_01_319Z-debug.log
```

你这是由于8080端口被占用了。你可以通过如下方式解决。
1 按下Windows键。输出cmd。点击cmd.exe.打开该程序。
2 输入 netstat   -ano|findstr  8080 ，找到占用进程的pid.
3 输入命令taskkill  /pid  4708  /f  ，结束该进程。//假如 4708是查询到的pid

报错 eslint 检查出错  

> 在vue项目中关闭ESLint方法：找到build文件夹--->webpack.base.conf.js---->module

```bash
Failed to load the ESLint library for the document c:\Users\SUI\Desktop\vue0307\qqmiuscvue\menu\src\main.js

To use ESLint please install eslint by running 'npm install eslint' in the workspace folder menu
or globally using 'npm install -g eslint'. You need to reopen the workspace after installing eslint.

If you are using yarn instead of npm set the setting `"eslint.packageManager": "yarn"`

Alternatively you can disable ESLint for the workspace folder menu by executing the 'Disable ESLint' command.
```

http://blog.csdn.net/wdy_2099/article/details/76997888?locationNum=5&fps=1