---
title: oneThink的搭建
date: 2017-08-30 14:36:19
tags:
categories: 网站搭建
---
------

<!-- more -->

# oneThink简单而强大的内容管理框架,让WEB开发更快速!

## 准备开发

  下载官方软件v1.0正式版 http://www.onethink.cn/
  下载本地服务器wampserver http://www.wampserver.com/

## 开发步骤

* 解压v1.0安装包将`www`文件目录的所有文件copy到`C:\wamp64\www`或`C:\wamp32\www`目录中
* 启动wampserver等待指示灯有红变绿 黄色不行
* 进入http://localhost/phpmyadmin/index.php?token=6de2f4e9ae5b49d31d01b84dd98ed44d 账号root 密码为空 新建一个数据库后面需要用到
* 启动浏览器输入localhost执行安装步骤
> 如果一直无法进入下一步说明cookie出错了，打开`C:\wamp64\www\Application\Install\Controller\InstallController.class.php`注释掉92行和103行代码，如果还是不行请删除`C:\wamp64\www\Runtime`所有文件夹，如果不行 重复此步骤或者去百度。
> 执行第三步之后出现`"Access denied for user 'admin'@'localhost' (using password: YES)"`说明数据库用户名不对，wampserver默认用户名 root 密码不用填

## 部署阿里云

开发步骤与上面相同，数据库账号密码以及数据库名称统一更换为阿里云的账户名称。
