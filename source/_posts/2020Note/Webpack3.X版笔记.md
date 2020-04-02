---
title: Webpack3.X版笔记
date: 2020-03-06
tags: note
categories: 2020Note
---

[webpack官网](https://www.webpackjs.com/)
[webpack文档](https://www.webpackjs.com/loaders/)
### 1. 认识Webpack的作用
- 打包：可以把多个javascript文件打包成一个文件，减少服务器压力和下载带宽
- 转换：把扩展语言转换成普通的javascript，让浏览器顺利运行。
- 优化：前端复杂性的提高，开始肩负起优化和提升性能的责任。

```bash
1. `win+R` 进入对话框输入`cmd`进入命令行模式。
2. 输入`f： `进入f盘
3. `mkdir webpack_demo`  生成webpack_demo文件夹
4. `cd webpack_demo` 进入当前文件夹
5. 需要安装`node`
6. `npm install -g webpack` 全局安装webpack，
   注意：全局安装是可以的，但是webpack官方是不推荐的。
   这会将您项目中的 webpack 锁定到指定版本，并且在使用不同的 webpack 版本的项目中，可能会导致构建失败。 
7. 对项目目录安装，npm初始化。`npm init`
8. `npm install --save-dev webpack`   安装到开发环境
9. `webpack -v` 检查版本号
```
### 2.配置文件
######  配置出口和入口文件
```js
const path =  require('path');
moduel.exports = {
    // 入口文件配置项
    entry:{
        './entry.js'
     },
    // 出口文件配置项
    output:{
       // 打包文件的出口路径
       path: path_resolve(__dirname,'dist'), // 获取项目的绝对路径
       // 输出文件名称
       filename: 'bundle.js'   
    },
    // 模块，用于解析css,图片转换，压缩
    module:{},
    // 插件，用于生产模板和各项功能
    plugins:[],
    // 配置webpack开发服务功能
    devServer:{}
}
```
###### 服务和热更新 webpack-dev-server
* 安装
```bash
npm install webpack-dev-server --save-dev
```
webpack.config.js中
```js
moduel.exports = {
   devServer:{
      // 设置基本目录接口
      contentBase: path_resolve(__dirname:'dist'); // 用于找到程序打包地址
      // 服务 IP 地址
      host: 'localhost',
      // 服务是否开启压缩
      compress: true,
      // 配置服务端口号
      port: 8888
   }
}
```
package.json中
```json
"script":{
   "server":"webpack-dev-server"
}
```
### 3. 模块
###### css打包
`loaders`
* 可以把`sass`、`less`文件转为css 
* 可以把`es6及以上`的代码转为大多浏览器兼容的js代码
* 可以把React的`JSX`转为javascript代码

所有的解析器都需要使用`npm`安装然后在进行使用。

建立`index.css`文件
引入到入口文件夹`main.js`中
```js
import i_css from './css/index.js'
```
CSS和引入做好后，我们就需要使用loader来解析CSS文件了，这里我们需要两个解析用的loader，分别是style-loader和css-loader。

**style-loader**
用于处理css中的`url()`, [https://www.npmjs.com/package/style-loader]()
```bash
npm install style-loader --save-dev
```
**css-loader**
用来将css插入到页面的style的标签。[https://www.npmjs.com/package/css-loader]()
```bash
npm install css-loader --save-dev
```
修改webpack.config.js中的module
```js
module.exports = {
   module:{
     rules:[
        {
          test: /\.css$/,
          use:['style-loader','css-loader'], // 第一种
          loader:['style-loader','css-loader'],  // 第二种
          use:[{                               // 第三种
            loader: 'style-loader'
          },{
            loader: 'css-loader'
          }]
         }
      ]
   }
}
```
### 4.插件配置
==需要注意的压缩需要在生产环境下配置，因为开发环境为了方便调试压缩个棒棒==
##### js压缩
`uglifyjs-webpack-plugin` 这个小瘪三插件默认集成进了webpack 所以不用安装了

**引入**
webpack.config.js引入
```js
const uglify = require('uglifyjs-webpack-plugin');
moduel.exports = {
   plugin:[
      new uglify()
   ]
}
```
##### html文件的发布
* 打包html文件
`html-webpack-plugin` 插件
```bash
const htmlPlugin = require('html-webpack-plugin');
```
引入npm 安装
```bash
npm install html-webpack-plugin --save-dev
```
webpack.config.js进行配置
```js
module.exports = {
    plugin:[
      new htmlPlugin({
            minify:{
                removeAttributeQuotes:true
            },
            hash:true,
            template:'./src/index.html'
      })
    ]
}
```
* minify：是对html文件进行压缩，removeAttrubuteQuotes是却掉属性的双引号。
* hash：为了开发中js有缓存效果，所以加入hash，这样可以有效避免缓存JS。
* template：是要打包的html模版路径和文件名称。

**总结：**
html文件的打包可以有效的区分开发目录和生产目录，在webpack的配置中也要搞清楚哪些配置用于生产环境，哪些配置用于开发环境，避免两种环境的配置冲突。
### 5. 图片迈坑
##### 图片处理
**file-loader** 解析背景图片的url，路径
**url-loader** 减少http请求，将图片转为dataUrl，但是如果图片过大，编码会消耗性能，所以有了limit参数进行配置
注意： loader使用时不需要require引用，plugins才需要使用require引入
url-loader 默认包含了 file-loader所以引入的时候只需要引入url-loader就行了

webpackconfig.js中
```js
moduel.exports = {
   module:{
      rules:[
        {
          test:/\.(png|jpg|gif)/ ,
          use: [
             loader:'url-loader',
             options:{
               limit: 500000
             }
          ]
        }
      ]
   }
}
```
* test:/.(png|jpg|gif)/是匹配图片文件后缀名称。
* use：是指定使用的loader和loader的配置参数。
* limit：是把小于500000B的文件打成Base64的格式，写入JS
##### css图片分离和图片路径处理
**css分离:extract-text-webpack-plugin**
```bash
npm install --save-dev extract-text-webpack-plugin
```
webpackconfig.js中
```js
const extractCss = require('extract-text-webpack-plugin');
module.exports = {
    module:{
       test: /\.css$/,
       use: extractTextPlugin.extract({
            fallback: "style-loader",
            use: "css-loader"
       })
    }
}
```
**图片路径问题**
利用extract-text-webpack-plugin插件很轻松的就把CSS文件分离了出来，但是CSS路径并不正确，很多小伙伴就在这里搞个几天还是没有头绪，网上也给出了很多的解决方案，我觉的最好的解决方案是使用publicPath解决，我也一直在用。
publicPath：是在webpack.config.js文件的output选项中，主要作用就是处理静态文件路径的。
在处理前，我们在webpack.config.js 上方声明一个对象，叫website。
```js
var website = {
    publicPath: "http://192.168.1.108:8888/"
}
```
然后在output选项中引用这个对象的publicPath属性。
```js
module.exports = {
    output:{
      publicPath: website.publicPath
    }
}
```
配置完成后，你再使用webpack命令进行打包，你会发现原来的相对路径改为了绝对路径，这样来讲速度更快。
总结：这节课我们实现了CSS的分离，并在分离后处理了图片路径不对的问题。处理路径的方法一定要充分理解，因为这在工作中经常用到。
##### 处理html中的图片
**html-withimg-loader** 
```bash
npm install html-withimg-loader --save 
```
```js
{
    test: /\.(htm|html)$/i,
     use:[ 'html-withimg-loader'] 
}
```
**如何把图片放到指定的文件夹下**
```js
module.exports = {
   rules:[{
     test: /\.(png|jpg|gif)/,
     use:[{
        loader:'style-loader',
        option:{
            limit:'url-loader',
            options:{
               limit:5000,
               outputPath:'images/'
            }
        }
      }]
   }]
}
```
### 6. Css进阶
##### Less文件的打包和分离
```bash
npm install --save-dev less
npm install --save-dev less-loader
```
webpack.js
```js
{
    test: /\.less$/,
    use: [{
           loader: "style-loader" // creates style nodes from JS strings
        }, {
            loader: "css-loader" // translates CSS into CommonJS
        , {
            loader: "less-loader" // compiles Less to CSS
        }]
}
```
**把Lees文件分离**
```js
{
            test: /\.less$/,
            use: extractTextPlugin.extract({
                use: [{
                    loader: "css-loader"
                }, {
                    loader: "less-loader"
                }],
                // use style-loader in development
                fallback: "style-loader"
            })
 }
```
##### Sass文件的打包和分离
```bash
npm install --save-dev node-sass
npm install --save-dev sass-loader
```
注意：在用npm安装时，这个loader很容易安装失败，最好使用cnpm来进行安装。如果你安装一直报错，最好是把node_modules文件夹删除后，再重新安装。
```js
{
                test: /\.scss$/,
                use: [{
                    loader: "style-loader" // creates style nodes from JS strings
                }, {
                    loader: "css-loader" // translates CSS into CommonJS
                }, {
                    loader: "sass-loader" // compiles Sass to CSS
                }]
}
```
**把Lees文件分离**
```js
{
            test: /\.scss$/,
            use: extractTextPlugin.extract({
                use: [{
                    loader: "css-loader"
                }, {
                    loader: "sass-loader"
                }],
                // use style-loader in development
                fallback: "style-loader"
            })
 }
```
##### css3属性前缀处理
**PostCSS** css处理平台
需要安装postcss-loader和autoprefixer
```bash
npm install --save-dev postcss-loader autoprefixer
```
postcss.config.js
postCSS推荐在项目根目录（和webpack.config.js同级），建立一个postcss.config.js文件。
```js
module.exports = {
    plugins: [
        require('autoprefixer')
    ]
}
```
**编写loader**
对postcss.config.js配置完成后，我们还需要编写我们的loader配置。
```js
module.exports = {
    module:{
      rules:[
      {
      test: /\.css$/,
      use: [
            {
              loader: "style-loader"
            }, {
              loader: "css-loader",
              options: {
                 modules: true
              }
            }, {
              loader: "postcss-loader"
            }
      ]
}]
    }
}
```
**提取CSS**
配置提取CSS的loader配置.
```js
{
    test: /\.css$/,
    use: extractTextPlugin.extract({
        fallback: 'style-loader',
        use: [
            { loader: 'css-loader', options: { importLoaders: 1 } },
            'postcss-loader'
        ]
    })

}
```
总结:postcss还有很多功能，我希望小伙伴学会自学。这里给出postcss-loader的github地址：[https://github.com/postcss/postcss-loader]()

##### 消除未使用的css
像Bootstrap这样的框架往往会带有很多CSS。在项目中通常我们只使用它的一小部分。就算我们自己写CSS，随着项目的进展，CSS也会越来越多，有时候需求更改，带来了DOM结构的更改，这时候我们可能无暇关注CSS样式，造成很多CSS的冗余。这节课就学习用webpack消除未使用的CSS。

**PurifyCSS**

使用PurifyCSS可以大大减少CSS冗余，比如我们经常使用的BootStrap(140KB)就可以减少到只有35KB大小。这在实际开发当中是非常有用的。

安装**PurifyCSS-webpack**

从名字你就可以看出这是一个插件，而不是loader。所以这个需要安装还需要引入。 PurifyCSS-webpack要以来于purify-css这个包，所以这两个都需要安装。
```bash
npmn  i -D purifycss-webpack purify-css
```
这里的-D代表的是–save-dev ,只是一个简写。

引入glob

因为我们需要同步检查html模板，所以我们需要引入node的glob对象使用。在webpack.config.js文件头部引入glob。
```js
const glob = require(glob);
const PurifyCSSPlugin = `require`("purifycss-webpack");
```
**配置plugins**
```js
plugins:[
    //new uglify() 
    new htmlPlugin({
        minify:{
            removeAttrubuteQuotes:true
        },
        hash:true,
        template:'./src/index.html'

    }),
    new extractTextPlugin("css/index.css"),
    new PurifyCSSPlugin({
        // Give paths to parse for rules. These should be absolute!
        paths: glob.sync(path.join(__dirname, 'src/*.html')),
        })

]
```
这里配置了一个paths，主要是需找html模板，purifycss根据这个配置会遍历你的文件，查找哪些css被使用了。

注意：使用这个插件必须配合extract-text-webpack-plugin这个插件，这个插件在前边的课程已经讲解过了。如果你还不会请自学一下。

配置好上边的代码，我们可以故意在css文件里写一些用不到的属性，然后用webpack打包，你会发现没用的CSS已经自动给你删除掉了。在工作中记得一定要配置这个plugins，因为这决定你代码的质量，非常有用。

### 7. webpack添加babel支持
在前端开发中都开始使用ES6的语法了，虽然说webpack3增加了一些ES6的转换支持，但是实际效果不是很好，也可能是本人技术有限，没发挥出真正的功能。所以我在开发中还是喜欢添加Babel-loader的，我也查看了一些别人的webpack配置也都增加了babel-loader，所以这节课我们学习一下如何增加Babel支持。（此节文章部分内容引用了zhangwang大神的文章内容）

Babel是什么？ Babel其实是一个编译JavaScript的平台，它的强大之处表现在可以通过便宜帮你达到以下目的：

使用下一代的javaScript代码(ES6,ES7….)，即使这些标准目前并未被当前的浏览器完全支持。

使用基于JavaScript进行了扩展的语言，比如React的JSX。

##### Babel的安装与配置
Babel其实是几个模块化的包，其核心功能位于称为babel-core的npm包中，webpack可以把其不同的包整合在一起使用，对于每一个你需要的功能或拓展，你都需要安装单独的包（用得最多的是解析ES6的babel-preset-es2015包和解析JSX的babel-preset-react包）。

我们先一次性安装这些依赖包
`Babel其实是几个模块化的包，其核心功能位于称为babel-core的npm包中，webpack可以把其不同的包整合在一起使用，对于每一个你需要的功能或拓展，你都需要安装单独的包（用得最多的是解析ES6的babel-preset-es2015包和解析JSX的babel-preset-react包）。

我们先一次性安装这些依赖包
```js
cnpm c install --save-dev babel-core babel-loader babel-preset-env babel-preset-react
```
在webpack中配置Babel的方法如下：
```js
{
    test:/\.(jsx|js)$/,
    use:{
        loader:'babel-loader',
        options:{
            presets:[
                "env","react"
            ]
        }
    },
    exclude:/node_modules/
}
```
现在你已经可以用webapck转换ES6的语法兼容各个浏览器了，我们可以修改一下entry.js的代码如下：
```js
import css from './css/index.css';
{
    let jspangString = 'Hello Webpack'
    document.getElementById('title').innerHTML=jspangString; 
}
```
上面的代码使用了ES6的let声明方法。如果你不使用Babel来进行转换，你会发现打包出来的js代码没有作兼容处理，使用了Babel转换的代码是进行处理过的。
##### .babelrc配置
虽然Babel可以直接在webpack.config.js中进行配置，但是考虑到babel具有非常多的配置选项，如果卸载webapck.config.js中会非常的雍长不可阅读，所以我们经常把配置写在.babelrc文件里。

在项目根目录新建.babelrc文件，并把配置写到文件里。
.babelrc
```js
{
    "presets":["react","es2015"]
}
```
.webpack.config.js里的loader配置
```js
{
    test:/\.(jsx|js)$/,
    use:{
        loader:'babel-loader',
    },
    exclude:/node_modules/
}
```
### 8.打包之后如何调试
作为一个程序员每天的大部分工作就是调试自己写的程序，那我们使用了webpack后，所以代码都打包到了一起，给调试带来了麻烦，但是webpack已经为我们充分考虑好了这点，它支持生产Source Maps来方便我们的调试。（敲黑板，这节可能偏理论一点。）

在使用webpack时只要通过简单的devtool配置，webapck就会自动给我们生产source maps 文件，map文件是一种对应编译文件和源文件的方法，让我们调试起来更简单。

四种选项

在配置devtool时，webpack给我们提供了四种选项。

- source-map:在一个单独文件中产生一个完整且功能完全的文件。这个文件具有最好的source map,但是它会减慢打包速度；
- cheap-module-source-map:在一个单独的文件中产生一个不带列映射的map，不带列映射提高了打包速度，但是也使得浏览器开发者工具只能对应到具体的行，不能对应到具体的列（符号）,会对调试造成不便。
- eval-source-map:使用eval打包源文件模块，在同一个文件中生产干净的完整版的sourcemap，但是对打包后输出的JS文件的执行具有性能和安全的隐患。在开发阶段这是一个非常好的选项，在生产阶段则一定要不开启这个选项。
- cheap-module-eval-source-map:这是在打包文件时最快的生产source map的方法，生产的 Source map 会和打包后的JavaScript文件同行显示，没有影射列，和eval-source-map选项具有相似的缺点。

四种打包模式，有上到下打包速度越来越快，不过同时也具有越来越多的负面作用，较快的打包速度的后果就是对执行和调试有一定的影响。

个人意见是，如果大型项目可以使用source-map，如果是中小型项目使用eval-source-map就完全可以应对，需要强调说明的是，source map只适用于开发阶段，上线前记得修改这些调试设置。

简单的配置：
```js
module.exports = {
  devtool: 'eval-source-map',
  entry:  __dirname + "/app/main.js",
  output: {
    path: __dirname + "/public",
    filename: "bundle.js"
  }
}
```
总结：调试在开发中也是必不可少的，但是一定要记得在上线前一定要修改webpack配置，在打出上线包。

### 9. 开发和生产并行设置
##### 开发生产环境依赖不同
一个项目中是有开发环境和生产环境的，这两个环境的依赖也是不同的。

* 开发依赖：在开发中用来帮助开发、简化代码或者生成兼容设置的依赖包。可以使用package.json来查看，devDependencies的下面的这些包为开发使用的依赖包。在生成环境中并无用处。
* 生产依赖：比如我们的js使用了jquery，jquery在浏览器端口起作用，也就是说我们最终的程序也需要这个包。这个生产依赖，这些包在dependencies。

##### npm安装的三种安装方式
**one**
```bash
npm install jquery
```
安装完成后，你会发现在package.json中并不存在这个包的依赖。如果你项目拷贝给别人继续开发，或者别人和你git合作，再次下载项目npm install时就会缺少这个jquery包。项目就会无法正常运行，所以这也是我们最不赞成的安装方法。
**two**
```bash
npm install jquery --save
```
安装完成后，它存在于package.json的dependencies中，也就是说它是生产环境需要依赖的包（上线时需要的依赖包）。
**three**
```bash
npm install jquery --save-dev
```
安装完成后，它存在于package.json的devDependencies中，也就是说它是开发环境中需要的，上线并不需要这个包的依赖。

##### 安装全部依赖包
```bash
npm install
```

##### 安装生产环境依赖包
```bash
npm install --production
```
##### 配置生产和开发并行
我们在以前的配置中设置了一个变量website，用于静态资源正确找到路径。那如果生产环境和开发环境不一样，而且我们需要来回切换，这时候我们需要更好的设置方法。
```js
var website={
    publicPath:"http://192.168.0.104:1717/"
}
```
**修改package.json命令**
其实就是添加一个dev设置，并通过环境变量来进行区分，下面是package.json里的值。
```js
"scripts": {
    "server": "webpack-dev-server --open",
    "dev":"set type=dev&webapck",
    "build": "set type=build&webpack"
  },
```
**修改webpack.config.js文件**
可以利用node的语法来读取type的值，然后根据type的值用if–else判断。
```js
if(process.env.type== "build"){
    var website={
        publicPath:"http://192.168.0.104:1717/"
    }
}else{
    var website={
        publicPath:"http://cdn.jspang.com/"
    }
}
```
如果你说我想看一下传过来的值到底是什么？可以用下面的输出语句。
```js
console.log( encodeURIComponent(process.env.type) );
```
### 10. webpack模块化配置
为了让大家容易看懂，我把webpack.config.js中的entry入口文件进行模块化设置，单独拿出来制作成一个模块。

首先在根目录，新建一个webpack_config文件夹，然后新建entry_webpack.js文件，代码如下：

entry_webpack.js
```js
//声明entry变量
const entry ={};  
//声明路径属性
entry.path={
    entry:'./src/entry.js'  
}
//进行模块化
module.exports =entry;
```
配置的模块化代码编写好以后，需要在webpack.config.js中引入，注意这里的引入只能使用require的方法。
```js
const entry = require("./webpack_config/entry_webpack.js")
```
webpack.config.js  入口文件中
```js
module.exports = {
      entry:entry.path
}
```
这时候你可以再次使用npm run dev 进行测试，你会发现模块化成功了。

**总结：** 模块化在实际工作中是必不可少的操作，但是现在的webpack教程还很少讲到，大家一定要重视这节，因为如果你搞不清这节的内容，可能你看别人的配置也会看不明白。记得一定要动手练习操作，否则你下面的课程也没办法学习。