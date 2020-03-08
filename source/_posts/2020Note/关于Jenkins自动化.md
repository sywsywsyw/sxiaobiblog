---
title: 关于Jenkins自动化
date: 2020年3月6日 21点55分
tags: note
categories: 2020Note
---

笨鸟贤妃，用了两天终于搞好了jenkins+coding的vue项目自动化打包。

#### 1.windows下的安装。
下载官网实在太慢了<https://jenkins.io/zh/download/>
通过三方链接进行下载 <https://mirrors.tuna.tsinghua.edu.cn/jenkins/windows/>

<!-- more -->

#### 2.解压安装包之后就默认打开了，请耐心等待配置
<https://www.cnblogs.com/longpizi/p/10690781.html>

>1、net start jenkins  开启服务 
>2、net stop jenkins 关闭服务 
>我们可以在Windows10系统的开始菜单上，单击鼠标右键，这时候出现的菜单中，我们选择命令提示符（管理员）
>或 http://localhost:8080/exit 会提示你是否关闭服务
> http://localhost:8080/restart重启jenkins

C:\Program Files (x86)\Jenkins\secrets\initialAdminPassword
1d9ad2e761a045b78b52a994d4df2a6d

#### 3. 插件下载过慢
<https://blog.csdn.net/u013788943/article/details/103822785>

#### 4.(修改Jenkins访问端口)
到Jenkins安装目录找到jenkins.xml 打开里面有个--httpPort=8080 直接修改它就可以了

#### 5.创建第一个管理员用户 s18334787934 sx...4s


#### 6.jenkins汉化 jenkins转换显示语言为中文简体（jenkins汉化） 
<https://blog.csdn.net/u013053075/article/details/101770152>


#### 7. 账号密码使用admin或者自己注册的账号。
如果用admin账号，初始密码在这里 cat /Users/chenpeisong/.jenkins/secrets/initialAdminPassword

#### 8. jenkins自动化部署vue

https://e.coding.net/s18334787934/jenkinsdemo.git
cd /var/jenkins_home/workspace/test #进入test项目目录
```
npm install chromedriver --chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver
npm install
npm run build
cd dist
rm -rf test.tar.gz #删除上次打包生成的压缩文件
tar -zcvf test.tar.gz * #把生成的项目打包成test方便传输到远程服务器
cd ../
```
<https://blog.csdn.net/jonsonler/article/details/81317352>
<https://blog.csdn.net/ansu2009/article/details/83584796>


#### 9.使用 Jenkins 构建 Coding 项目
<https://blog.csdn.net/zxb730916/article/details/80913579>


#### 10.本机Jenkins实现外网访问 外网访问内网Jenkins
需要下载java环境
<https://www.cnblogs.com/wisdom-projects/p/11184983.html>


