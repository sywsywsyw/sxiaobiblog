---
title: 微信小程序使用Taro转H5
date: 2020-04-07
tags: note
categories: 2020Note
---

#### 1. 微信小程序转Taro，文档 
[https://nervjs.github.io/taro/docs/taroize.html]()
Taro 可以将你的原生微信小程序应用转换为 Taro 代码，进而你可以通过 `taro build` 的命令将 Taro 代码转换为对应平台的代码，或者对转换后的 Taro 代码用 React 的方式进行二次开发。
微信原生小程序转 Taro 的操作非常简单，首先必须安装使用 `npm i -g @tarojs/cli` 安装 Taro 命令行工具，其次在命令行中定位到小程序项目的根目录，根目录中运行：
```bash
$ taro convert
```
即可完成转换。转换后的代码保存在根目录下的 taroConvert 文件夹下。你需要定位到 `taroConvert`目录执行 `npm install` 命令之后就可以使用 taro build 命令编译到对应平台的代码。
预览h5
```bash
npm run dev:h5
```
==注意，转换完之后运行会提示`.temp`文件有好多报错，不要在这个里面改错误，要去`src`目录下面更改，因为`.temp`是临时文件夹，因为这个问题折腾了一下午。==
#### 2.遇到的报错
###### 2.1 An identifier or keyword cannot immediately follow a numeric literal
报错的意思是标识符以数字开头，这是因为js是弱类型的语言当发现第一个数字是就自动转化为数字类型的但是其中还含有字符所以报了错，'
报错的原因是因为我们想传的字符串，但是js却当成数字，所以需要给传的参数加引号。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200407104605631.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
```html
<Text decode="true">(最多可选择9张,文件大小\'{10}\'M)</Text>
```

###### 2.2 npm ERR! Cannot read property 'match' of undefined 错误处理
[https://blog.csdn.net/Jane_96/article/details/81451759?%3E]()


###### 2.3 转换过程中因为部分页面语法出错，导致转换报错
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200409150452838.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
将项目根目录备份一份然后注释掉app.json中其他文件，有针对性的转换当前文件，查看语法报错。修复后执行`taro convert`将生成的文件拷贝到之前转换出来的目录下。

