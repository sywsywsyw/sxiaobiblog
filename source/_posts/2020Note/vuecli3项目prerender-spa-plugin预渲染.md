---
title: vuecli3项目prerender-spa-plugin预渲染
date: 2020年3月27日 12点56分
tags: note
categories: 2020Note
---

==页面预渲染只支持静态内容较多的页面、如果接口多的页面建议使用ssr服务器渲染，例如nuxt==

### 安装
```bash
npm install prerender-spa-plugin --save
```

### vue.config.js
```js
// 预渲染配置：在webpack.prod.conf文件中加入
const PrerenderSPAPlugin = require('prerender-spa-plugin')
const Renderer = PrerenderSPAPlugin.PuppeteerRenderer
const path = require("path");

module.exports = {
  configureWebpack: config => {
    config.plugins.push(
      new PrerenderSPAPlugin({
        staticDir: path.join(__dirname, './dist'),
        // 需要进行预渲染的路由路径 我这里做的是首页
        routes: ['/', '/aboutview', '/adHome', '/finaHome', '/lawHome', '/capitalHome', '/payFaceSwip', '/payEwm', '/payPos', '/paySweepEwm', '/payCashier','/payCustom'],
        // html文件压缩
        minify: {
          minifyCSS: true, // css压缩
          removeComments: true // 移除注释
        },
        renderer: new Renderer({
          // Optional - The name of the property to add to the window object with the contents of `inject`.
          injectProperty: '__PRERENDER_INJECTED',
          // Optional - Any values you'd like your app to have access to via `window.injectProperty`.
          inject: {},
          // 在 main.js 中 new Vue({ mounted () {document.dispatchEvent(new Event('render-event'))}})，两者的事件名称要对应上。
          // renderAfterDocumentEvent: 'render-event'
          renderer: new PrerenderSPAPlugin.PuppeteerRenderer({//这样写renderAfterTime生效了
            renderAfterTime: 5000
          })
        })
      })
    )
  }
}
```

### main.js
```js
new Vue({
  router,
  store,
  render: h => h(App),
  // 添加mounted，不然不会执行预编译
  mounted() {
    document.dispatchEvent(new Event('render-event'))
  },
}).$mount('#app')
```
> 参考文档
> [https://blog.csdn.net/u012878818/article/details/90751461]()
> [https://www.jianshu.com/p/2b0e4754bb07]()
> [https://www.jianshu.com/p/8cc2f8ed5efd]()
> [https://yehuzi.com/vue-cli-3-0-shi-yong-prerender-spa-plugin-yu-xuan-ran-yu-dao-de-mo-ming-qi-miao-de-keng/]()
> [https://www.jianshu.com/p/8f82459895c9]()