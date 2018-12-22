---
title: sublime快速生成html标签(emmet语法)
date: 2018-04-03
tags: 工具
categories: 
---

> sublime快速生成html标签、Vscode快速生成html标签、Atom快速生成标签、

> 安装完`emmet插件`的编辑器都可以用不光是`sublime`,`Vscode`、`Atom`、`···`都可以用。

--------------------------------------------------------------------------------

<!-- more -->

# html 

```
所有`输入`输完之后都需要按下`tab`触发。
```

## 1.创建标准页面

创建标准xhtml页面。

```
输入： html:xxs
```
![Alt text](/images/快速生成标签/1522718211956.png)
![Alt text](/images/快速生成标签/1522718277472.png)

创建标准html5页面

```
输入：! / html:5
```
![Alt text](/images/快速生成标签/1522718296457.png)
![Alt text](/images/快速生成标签/1522718931054.png)
![Alt text](/images/快速生成标签/1522718299058.png)

## 2.创建html标记

输入任何标记、双标记按下tab出现正常标签对

```
输入：style
```
![Alt text](/images/快速生成标签/1522718319279.png)
![Alt text](/images/快速生成标签/1522718321952.png)

## 3.创建html标签含Id、多个类名的标记

创建格式和css选择器命名方式一致

```
例如：id #id class .class
```
## 4.创建html示例

> 创建Id名为box的div标记

```
输入： div#box
```

![Alt text](/images/快速生成标签/1522718327988.png)
![Alt text](/images/快速生成标签/1522718330783.png)

> 创建类名为box的div标记

```
输入： div.box
```
![Alt text](/images/快速生成标签/1522718336462.png)
![Alt text](/images/快速生成标签/1522718339055.png)

同时创建两个div标记 Id为box 类名为box2

```
输入：div#box+div.box2
```
![Alt text](/images/快速生成标签/1522718347125.png)
![Alt text](/images/快速生成标签/1522718349049.png)

> 创建两个div标记 Id为box 包含 类名为box

```
输入：div#box>div.box
```

![Alt text](/images/快速生成标签/1522718353408.png)
![Alt text](/images/快速生成标签/1522718355668.png)

> 创建Id为box的标记包含两个类名为box2的标记

```
输入：div#box>div.box2
```

![Alt text](/images/快速生成标签/1522718398561.png)
![Alt text](/images/快速生成标签/1522718372306.png)

> 同时创建2个div并且给它包含2个类名 aa bb，它里面有两个类名为box的div。

```
输入：div.aa.bb*2>div.box2*2
```
![Alt text](/images/快速生成标签/1522718545113.png)
![Alt text](/images/快速生成标签/1522718549390.png)

> 同时创建2个div并且给它2个类名 aa bb，它里面包含box2、box3两个div标记。
```
输入：div.aa.bb*2>div.box2+div.box3
```
![Alt text](/images/快速生成标签/1522718553338.png)
![Alt text](/images/快速生成标签/1522718557137.png)

> 创建5个div类名为box、内容为1-5
```
输入：div.box{$}5
```
![Alt text](/images/快速生成标签/1522718560420.png)
![Alt text](/images/快速生成标签/1522719127477.png)

> 创建5个div类名为box1-5
```
输入：div.box$*5  
```
![Alt text](/images/快速生成标签/1522718567612.png)
![Alt text](/images/快速生成标签/1522718570030.png)

> 创建1个div类名为box，内容为'Hellow world!'
```
输入：div.box{Hellow world!}
```
![Alt text](/images/快速生成标签/1522718574598.png)
![Alt text](/images/快速生成标签/1522718576450.png)
