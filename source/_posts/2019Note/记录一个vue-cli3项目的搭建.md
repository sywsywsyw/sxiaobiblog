---
title: 记录一个vue-cli3项目的搭建
date: 2019-04-01
tags: note
categories: 2019Note
---

### vue-cli3快速创建项目 https://www.jianshu.com/p/5e13bc2eb97c

##### 1. 安装axios请求处理  
> vue中Axios的封装与API接口的管理详解 https://www.jb51.net/article/145341.htm
```git
 npm install axios
```
<!-- more -->

##### 2. vue-cli里面`.`和`@`的区别
 https://segmentfault.com/q/1010000009800289
https://blog.csdn.net/qq_35366269/article/details/85232899


##### 3. vue-cli3 安装sass
```git
npm install node-sass --save-dev
npm install sass-loader --save-dev
```
==安装完 切记 重新开启 npm run serve 服务==


##### 4. vue-cli 3 关闭 eslint
https://blog.51cto.com/zhuxianzhong/2311226?source=dra


##### 5. 安装 babel-polyfill
```git
npm install --save babel-polyfill
```
##### 6. 基于vue仿淘宝滑动验证码
https://www.jianshu.com/p/f5bf9ba0b27e

#####  7. Vue-cli3.0怎么配置在打包时候去掉console打印的信息
https://forum.vuejs.org/t/vue-cli3-0-console/43788
https://www.npmjs.com/package/babel-plugin-transform-remove-console

```git
npm install babel-plugin-transform-remove-console --save
```
```js
const plugins = []
if (process.env.NODE_ENV === 'production') {
  plugins.push('transform-remove-console')
}

module.exports = {
  presets: [
    '@vue/app'
  ],
  plugins
}
```

##### 8. 如何自如地使用npm在项目中安装、删除模块包
https://blog.csdn.net/xum222222/article/details/81560809


##### 9.  vue-waterfall2 图片布局自适应插件
https://links.jianshu.com/go?to=https%3A%2F%2Fgithub.com%2FRise-Devin%2Fvue-waterfall2

##### 10. vue在data引入本地图片的两种方法
https://blog.csdn.net/Ajaxguan/article/details/81948829
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190426145718966.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)

##### 11. css3 动画
http://www.w3school.com.cn/cssref/pr_keyframes.asp
```css
@keyframes mymove
{
from {top:0px;}
to {top:200px;}
}

@-moz-keyframes mymove /* Firefox */
{
from {top:0px;}
to {top:200px;}
}

@-webkit-keyframes mymove /* Safari 和 Chrome */
{
from {top:0px;}
to {top:200px;}
}

@-o-keyframes mymove /* Opera */
{
from {top:0px;}
to {top:200px;}
}
```

#### 12. js判断是否存在当前元素得classname
```js
  if( obj.className.includes('active') ){
        //  存在
       }else{
        //  不存在
        obj.classList.add('active');
        setTimeout(()=>{
          obj.classList.remove('active');
        },1500)
}
 ```
##### 13. vue router-link返回上一页
https://router.vuejs.org/zh/guide/#javascript
```
<span  @click="this.$router.go(-1)">返回</span>
<span  @click="goBack()">返回</span>
goBack () {
      window.history.length > 1
        ? this.$router.go(-1)
        : this.$router.push('/')
}
```
> 上面的代码其实就可以满足我们返回上一页面的需求，但是如果我们是从别的地方打开此链接的时候事实上是没有上一页的，为了提升用户的体验，我们可以使用js来控制当我们点击返回按钮时所进行的操作，
https://www.cnblogs.com/daikefeng/p/6946517.html
```
// 退出
    goBack () {
      if (document.referrer === '') {
         this.$router.push('/')
      }else{
       this.$router.go(-1)
      }
    },
```
> 上面的意思是当我们点击的时候进行判断，如果document.referrer为空字符串，它就会返回首页,这样对用户的体验来说也比较好。
referrer:referrer 属性可返回载入当前文档的文档的 URL，其实就是上一个页面。

##### 14. mock模拟数据
https://www.cnblogs.com/jasonwang2y60/p/7302449.html
https://linjinze999.github.io/vue-llplatform/login.html#%E5%90%8E%E5%8F%B0%E6%8E%A5%E5%8F%A3
```npm
npm install mockjs --save-dev
```

##### 15. input写法
必须使用padding width 100%;不许使用margin
> 错误
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190429114039156.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
> 正确![在这里插入图片描述](https://img-blog.csdnimg.cn/20190429114109968.png)
// 兼容 1600*900 1368*768版本尺寸
@media screen and (max-height: 900px) {

##### 16. 安装qrcode
https://github.com/scopewu/qrcode.vue/blob/HEAD/README-zh_cn.md


##### 17. 路由懒加载写法
普通写法
```code
import ArtWorkInfo from '@/views/artwork/ArtWorkInfo.vue'
component: ArtWorkClassIfy,
```
懒加载写法
```code
component:()=>import(/* webpackChunkName:'打包文件得名字' */ '@/views/artwork/ArtWorkClassIfy'),
```