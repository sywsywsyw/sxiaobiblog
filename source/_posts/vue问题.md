---
title: vue问题
date: 2018-03-07 21.58
tags: 笔记
categories: vue
---

--------------------------------------------------------------------------------

<!-- more -->

## 常用插件

axios // axios的http请求模块
https://www.npmjs.com/package/axios
vue-scroller //滚动组件（下拉加载）
https://www.npmjs.com/package/vue-scroller
vue-awesome-swiper // 轮播图
安装地址　https://www.npmjs.com/package/vue-awesome-swiper
演示地址　https://surmon-china.github.io/vue-awesome-swiper/
博客　https://segmentfault.com/a/1190000010142118
npm install less less-loader --save-dev
https://www.cnblogs.com/zhuzhenwei918/p/6870340.html?utm_source=itdadao&utm_medium=referral
http://www.jb51.net/article/112143.htm
# vue问题

这个傻逼问题的出现是什么呢？

```
vue.esm.js?efeb:591 [Vue warn]: Unknown custom element: <m> - did you register the component correctly? For recursive components, make sure to provide the "name" option.

found in

---> <Ranklist> at src\components\Ranklist.vue
       <App> at src\App.vue
         <Root>
```
![Alt text](./1522940794079.png)
看这 不规范的html标签直接报错！！！！！ 还是要规范写代码啊
![Alt text](./1522940849546.png)
  