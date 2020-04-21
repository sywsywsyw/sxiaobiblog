---
title: ES6笔记
date: 2020-04-21
tags: note
categories: 2020Note
---


### React三大体系
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200413114354587.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
### React搭建
* 安装node
* Node中文网址：[http://nodejs.cn/]() (建议你在这里下载，速度会快很多)
* 安装`create-react-app`
```bash
npm install -g create-react-app
```
* `create-react-app`新建demo1  
```bash
create-react-app demo1
```
```bash
Inside that directory, you can run several commands:
  npm start
    Starts the development server.
  npm run build
    Bundles the app into static files for production.
  npm test
    Starts the test runner.
  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!
We suggest that you begin by typing:
  cd demo1
  npm start
Happy hacking!
```
### 目录基本介绍
* index.js 入口文件
```js
import * as serviceWorker from './serviceWorker'; // 用于PWA
```
* public  > manifest.js 用于PWA

### HellowWorld和组件
* 进入src新建index.js入口文件
```js
import React from 'react';  
import ReactDom from 'react-dom';
import App from './app';

ReactDom.render(<App />,document.getElementById('root'));
```
* 编写App组件 进入src新建 app.js
```js
import React,{Component} from 'react'; // {Component} 解构赋值 等同于  const Component = React.Component

class App extends Component{
    render(){
        return(
            <div>Hello 子小</div>
        )
    }
}
export default App;
```
### JSX语法简单介绍
JSX就是 Javascript 和 XML 的组合 是react定义的，可以方便的利用HTML语法来创建虚拟DOM，，可以方便的利用HTML语法来创建虚拟DOM，
通俗理解为 遇到 `<` 解析 为html，遇到`{`解析为js
```js
import React,{Component} from 'react'; // {Component} 解构赋值 等同于  const Component = React.Component

class App extends Component{
    render(){
        return(
            <ul className="list">
                <li className="item">我是子小</li>
                <li className="item">我喜欢前端</li>
                <li className="item">不喜欢产品</li>
            </ul>
        )
    }
}
export default App;
```
==jsx的class必须写成className==

reacts使用js创建html标签
```js
import React,{Component} from 'react'; // {Component} 解构赋值 等同于  const Component = React.Component

class App extends Component{
    render(){
        var item1 = React.createElement('li', null, '我是子小');
        var item2 = React.createElement('li', null, '我喜欢前端');
        var list = React.createElement('ul', { className: 'list' }, [item1, item2]);
        return[list]
    }
}
export default App;
```
### 子小爱好菜单
新建一个 `Like.js`
```js
import React, { Component,Fragment } from 'react';

class Like extends Component{
    render() {
        return(
            <Fragment>
            <div className="likewrap">
                <h4>子小的爱好</h4>
                <div className="lw-contentwrap">
                    <input type="text" className="lwc-input"/>
                    <button className="lwc-button">增加</button>
                </div>
                <ul className="lw-list">
                    <li className="lw-item">吃饭</li>
                    <li className="lw-item">喝饮料</li>
                    <li className="lw-item">玩游戏</li>
                    <li className="lw-item">宅家</li>
                </ul>
            </div>
            </Fragment>
        )
    }
}
export default Like;
```
==`Fragment`标签用来包裹元素，类似于vue的template标签==
> 加上最外层的DIV，组件就是完全正常的，但是你的布局就偏不需要这个最外层的标签怎么办?比如我们在作Flex布局的时候,外层还真的不能有包裹元素。这种矛盾其实React16已经有所考虑了，为我们准备了<Fragment>标签。

### input的赋值绑定
