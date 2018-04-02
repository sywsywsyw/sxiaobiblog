---
title: vue环境
date: 2018-03-07 21.58
tags: 笔记
categories: vue
---

--------------------------------------------------------------------------------

<!-- more -->

## 环境安装

* 必须拥有node 和 npm  -v查看版本号

全局安装 vue-cli

$ npm install -g(--global) vue-cli

$ vue init webpack vueapp

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
? Install vue-router? (Y/n) y
? Install vue-router? Yes
? Use ESLint to lint your code? (Y/n) y
? Use ESLint to lint your code? Yes
? Pick an ESLint preset (Use arrow keys)
? Pick an ESLint preset Standard
? Set up unit tests (Y/n) y
? Set up unit tests Yes
? Pick a test runner (Use arrow keys)
? Pick a test runner jest
? Setup e2e tests with Nightwatch? (Y/n) y
? Setup e2e tests with Nightwatch? Yes
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