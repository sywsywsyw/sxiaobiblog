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
* 响应式设计和数据绑定
`React`不建议你直接操作`DOM`元素,而是要通过数据进行驱动，改变界面中的效果。React会根据数据的变化，自动的帮助你完成界面的改变。所以在写React代码时，你无需关注DOM相关的操作，只需要关注数据的操作就可以了（这也是React如此受欢迎的主要原因，大大加快了我们的开发速度）。
现在的需求是增加小姐姐的服务项，就需要先定义数据。数据定义在`Like`组件中的构造函数里`constructor`。
```js
// js的构造函数，由于其他任何函数执行
    constructor(props){
        super(props)
        this.state = {
           inputValue: '123', // input的值
           list:[]
        }
    }
```
```js
/* eslint-disable react/no-direct-mutation-state */
import React, { Component,Fragment } from 'react';

class Like extends Component{
    // js的构造函数，由于其他任何函数执行
    constructor(props){
        super(props)
        this.state = {
           inputValue: '123', // input的值
           list:[
             '喝饮料','吃饭','宅家'
           ]
        }
    }
    inputChange(e) {
        console.log(e);
        this.setState({
            inputValue: e.target.value
        })
    }
    addItem(e){
       this.setState({
           list: [...this.state.list,this.state.inputValue],
           inputValue:'',
       })
    }
    deleteItem(index){
        let newList = this.state.list;
        newList.splice(index,1);
        this.setState({
            list: newList
        })
    }

    render() {
        return(
            <Fragment>
            <div className="likewrap">
                <h4>子小的爱好</h4>
                <div className="lw-contentwrap">
                        <input type="text" className="lwc-input" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
                    <button className="lwc-button" onClick={this.addItem.bind(this)}>增加</button>
                </div>
                <ul className="lw-list">
                    {
                        this.state.list.map((item, index)=>{
                            return <li className="lw-item" key={index + item} onClick={this.deleteItem.bind(this, index)}>{item}</li>
                        })
                    }
                </ul>
            </div>
            </Fragment>
        )
    }
}
export default Like;
```
###  JSX防踩坑的地方
###### 关于注释
* `{/*第一次注释*/}`
```js
<Fragment>
     {/* 第一次注释 */}
     <div className="likewrap"></div>
</Fragment>
```
###### 关于`class` 必须使用 `className `
```html
<button className="lwc-button">增加</button>
```
####### 关于`html标签`解析的问题
```js
<li className="lw-item" key={index + item} onClick={this.deleteItem.bind(this, index)} dahngerouslySetInnerHTML={{__html:item}}></li>
```
###### 关于laber 的`for`必须使用`htmlFor`
因为会和js中的`for`冲突 所以更换了名称
```js
<label htmlFor="likeinput"></label>
<input id="likeinput" type="text" className="lwc-input" value={this.state.inputValue} onChange={this.inputChange.bind(this)} />
```
### Simple React Snippets插件的使用
Vscode插件搜索Simple React Snippets，点击安装，即可使用，常用快捷键如下：

| Snippet | Renders                          |
| ------- | -------------------------------- |
| `imr`   | Import React                     |
| `imrc`  | Import React / Component         |
| `impt`  | Import PropTypes                 |
| `impc`  | Import React / PureComponent     |
| `cc`    | Class Component                  |
| `ccc`   | Class Component With Constructor |
| `sfc`   | Stateless Function Component     |
| `cdm`   | componentDidMount                |
| `cwm`   | componentWillMount               |
| `cwrp`  | componentWillReceiveProps        |
| `gds`   | getDerivedStateFromProps         |
| `scu`   | shouldComponentUpdate            |
| `cwu`   | componentWillUpdate              |
| `cdu`   | componentDidUpdate               |
| `cwu`   | componentWillUpdate              |
| `cdc`   | componentDidCatch                |
| `gsbu`  | getSnapshotBeforeUpdate          |
| `ss`    | setState                         |
| `ssf`   | Functional setState              |
| `ren`   | render                           |
| `rprop` | Render Prop                      |
| `hoc`   | Higher Order Component           |
```js
// Simple React Snippets 插件

// imr
import React from 'react';

// imrc
import React, { Component } from 'react';

// impt
import PropTypes from 'prop-types';

// impc
import React, { PureComponent } from 'react';

// cc
class  extends Component {
    state = {  }
    render() { 
        return (  );
    }
}
 
export default ;

// ccc
    constructor(props) {
        super(props);
        this.state = {  }
    }
    render() { 
        return (  );
    }
}
 
export default ;

// sfc
const  = () => {
    return (  );
}
 
export default ;

// cdm
componentDidMount = () => {
  
};

// cwm
componentWillMount = () => {
  
};

// cwrp
componentWillReceiveProps(nextProps) {
    
}

// gds
static getDerivedStateFromProps(nextProps, prevState) {
    
}

// scu
shouldComponentUpdate(nextProps, nextState) {
    
}

// cwu
componentWillUpdate() {
    
}

// cdu
componentDidUpdate(prevProps, prevState) {
    
}

// cwun 
componentWillUnmount = () => {
  
};

// cdc
componentDidCatch(error, info) {
    
}

// gsbu
getSnapshotBeforeUpdate(prevProps, prevState) {
    
}

// ss
this.setState({ :  });

// ssf
this.setState((state, props) => { return {  }})

// ren
render() {
  return (
    <div>
      
    </div>
  )
};

// rprop
class  extends Component {
    state = { :  }
    render() { 
        return this.props.render({
            : this.state.
        });
    }
}
 
export default ;

// hoc
import React from 'react';
import PropTypes from 'prop-types';

export default (WrappedComponent) => {
  const hocComponent = ({ ...props }) => <WrappedComponent {...props} />

  hocComponent.propTypes = {
  };

  return hocComponent
};
```
#### component组件拆分
新建`likeItem.js`组件
```js
import React, { Component } from 'react';

export default class componentName extends Component {
  render() {
    return (
      <div> LikeItem 我是LikeItem组件 </div>
    );
  }
}

```
在`likeItem.js`组件引入
```js
import LikeItem from './LikeItem'
<LikeItem></LikeItem>
```