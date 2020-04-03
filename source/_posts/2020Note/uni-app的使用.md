---
title: uni-app的使用
date: 2020年3月26日 18点24分
tags: note
categories: 2020Note
---

### 安装 
[https://www.dcloud.io/](https://www.dcloud.io/)

### [开始介绍 ](https://uniapp.dcloud.io/quickstart?id=%e8%bf%90%e8%a1%8cuni-app)

<!-- more -->

### 问题：无法运行到微信开发者工具
> 点击微信开发者工具的`设置->安全->服务端口`设置为`开启`

### 问题：怎么把现有项目迁移为uni-app项目
>[https://uniapp.dcloud.io/translate]()
>vue h5项目转换uni-app指南：[https://ask.dcloud.net.cn/article/36174]()
>微信小程序转换uni-app指南及转换器：[https://ask.dcloud.net.cn/article/35786]()
>wepy转uni-app转换器：[https://github.com/zhangdaren/wepy-to-uniapp]()
>mpvue 项目（组件）迁移指南、示例及资源汇总： [https://ask.dcloud.net.cn/article/34945]()

### 问题：注册全局组件
> 在mian.js 
```js
// 引入全局head导航组件
import publicHead from './pages/public/Head.vue';
let objHead = Vue.component('objhead',publicHead);

const app = new Vue({
    ...App
})
app.$mount()
// 追加全局组件
document.body.appendChild(new objHead().$mount().$el);
```
### 问题：怎么安装npm
> [https://uniapp.dcloud.io/frame?id=npm%e6%94%af%e6%8c%81]()
