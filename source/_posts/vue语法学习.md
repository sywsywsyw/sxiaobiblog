---
title: vue语法
date: 2018-03-07 21.58
tags: 笔记
categories: Vue
---

--------------------------------------------------------------------------------

<!-- more -->

## 为什么要用vue?

渐进式、轻量、声明式、高效、易用、响应式

什么是渐进式？
可以部分使用vue,也可以使用vue的一部分.
声明式渲染 - 组件系统 - 客户端路由 - 大规模状态管理 - 构建工具

## vue实例常用选项

var vm = new Vue({
  // 1. 实例挂载目标
  el: '#app',
  // 2. 设置数据对象
  data: {},
  // 3. 计算属性
  computed: {},
  // 4. 过滤器
  filters:{},
  // 5. 方法
  methods:{},
  // 6. 监听器
  watch:{},
  // 7. 局部注册组件(子组件)
  components:{}
})

## 文件说明
dev-server.js 里面 的 port变量 就是可以修改的端口号
assets 文件中 放 css 图片素材
components
main.js 当前文件的逻辑入口
app.vue 根组件 里面有 <template> <script> <style> 三个部分和小程序很像

## 逻辑语法
```
export default {   给外部使用
  name: 'test' 当前组件的名字
  data(){
    return {
      title : 'Hellow Vue.js!'
    }
  }

}

import test form './components/test'  引入

<style lang="css" scoped>  设置 scoped 只会影响当前内容的属性
</style>
```


## 获取数据的方法

```
模板绑定 <p>{{title}}</p>
指令获取 <p v-text="titile"></p>
```

## 模板语法

```
v-if
v-else
v-for="item in items" 前面是变量  后面是数组
```

## 事件绑定

```
v-on 包含很多个事件  js有的 都可以
v-on:click=""
v-on:keyup v-on:keyup.enter
computed 计算属性
```



