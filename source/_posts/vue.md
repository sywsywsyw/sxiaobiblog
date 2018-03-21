---
title: vue
date: 2018-03-07 21.58
tags: 笔记
categories: vue
---

--------------------------------------------------------------------------------

<!-- more -->

http://blog.csdn.net/wdy_2099/article/details/76997888?locationNum=5&fps=1

$ vue init webpack name

$ node -v

1）安装淘宝cnpm
$ npm install -g cnpm –registry=http://registry.npm.taobao.org

2）安装vue-cli
$ cnpm install -g vue-cli
测试安装：
$ vue -V
2.9.3

3）初始化第一个项目（webpack方式）
vue init webpack my-firstvue-pro(项目名称不能包含大写字母)


生成node-modules: 因为各个模板间都是相互依赖的，所以要安装依赖，在命令行输入cnpm install ,你会发现在已经创建的项目结构里面会多出一个node_modules的文件夹，里面就是刚才安装的所有依赖。

cnpm install


5）运行第一个程序:运行成功后会在浏览器中直接打开

cnpm run dev

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
