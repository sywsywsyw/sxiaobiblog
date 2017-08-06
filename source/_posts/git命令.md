---
title: git学习
date: 2016-07-17
tags:
categories: GIT
---

------

摘抄自 [廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137402760310626208b4f695940a49e5348b689d095fc000)

Git是什么？
* Git是目前世界上最先进的分布式版本控制系统（没有之一），一个可以自动帮你记录每次文件的改动，还可以让同事协作编辑的神器。

Git的特点
* 1、速度：Git在本地上保存着所有当前项目的版本和更新，并且Git中的绝大多数操作都在本地，无需连网，所以处理起来速度。
* 2、简单的设计：Git的实现与项目复杂度无关，它永远可以在几毫秒的时间内完成分支的创建和切换。
* 3、完全分布式模式：每个人电脑上都有一个完整的版本库，而且它支持离线工作（大部分操作都是本地执行），本地提交可以稍后提交到服务器上。
* 4、对非线性开发模式的强力支持：允许上千个并行开发的分支。



## 1、配置git

```bash
$ git config --global user.name "your name"
$ git config --global user.email "email@example.com"
```
注意git config命令的--global参数，顾名思义，用了这个参数，表示你这台电脑上所有的Git仓库都会使用这个配置(这个应该很好理解)，当然你也可以对某个仓库指定不同的uer.name和user.email。当然如果大家没有配置该信息的话，  一般情况下在git提交时会使用机器名，这样肯定不方便了。所以笔者建议大家都配置明确的user.name 和 user.email信息。

配置好了后，大家可以使用git config -l来查看当前的git配置列表。

## 2、远程仓库及其与本地仓库交互

### 2.1、创建GitHub账号及获取SSH秘钥对

首先你必须有github帐号，账号请大家自行注册。由于你的本地Git仓库和远程GitHub仓库之间的传输是通过SSH协议加密的，因此需要进行一些设置。

#### 2.1.1、检查电脑是否已经有SSH keys。

``` bash
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

默认情况下，public keys的文件名是以下的格式之一：id_dsa.pub、id_ecdsa.pub、id_ed25519.pub、id_rsa.pub。因此，如果列出的文件有public和private钥匙对（例如id_ras.pub和id_rsa），证明已存在SSH keys。

#### 2.1.2、如果没有SSH key，则生成新的SSH key。
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
```
之后一路回车即可（如果你用的着设置密码，请自行设置）。

#### 2.1.3、在GitHub添加SSH key。
首先，拷贝key：
```bash
clip < ~/.ssh/id_rsa.pub
# Copies the contents of the id_rsa.pub file to your cllipboard
```
然后，在GitHub右上方点击头像，选择"Settings"，在右边的"Personal settings"侧边栏选择"SSH Keys"。接着粘贴key，点击"Add key"按钮。最后，测试链接：
```bash
$ ssh -T git@github.com
# Attempts to ssh to GitHub
```
如果你看到：
```bash
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
```
就键入：yes。之后将会看到如下信息：
```bash
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```
###  2.2、创建远程仓库

有了GitBub账号，登录后找到右上角的“Create new...”，点击New repository(即创建一个新的仓库)，然后在Repository name中输入mygit（仓库名），点击Create repository即可。[新建远程仓库](https://github.com/new)



###  2.3、将本地仓库推送至远程仓库
现在这个远程的mygit仓库还是空的，下面我们把上面创建的本地mygit仓库推送到这个远程仓库中。首先要把一个已有的本地仓库与之关联，然后把本地仓库的内容推送到GitHub仓库。

依次执行下面几步

```bash
$ git init  #创建本地仓库
$ git add index.html
$ git status (可以查看本地更新了什么，一般不用)
$ git commit -m "2017072157" 
<!-- $ git remote rm origin -->
$ git remote add origin git@github.com:username/repository.git #将本地仓库和远程仓库关联，并命名为origin(可以随意修改) (记得将username命名成自己的github的名字)
$ git push -u origin master
#使用git push -u origin master第一次推送master分支的所有内容
#以后每次本地提交后，就只需敲入命令git push origin master推送最新修改到远程即可。
```

可能出现的报错

1. 
```bash
$ git push origin master
To github.com:sywsywsyw/Card-Verify.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:sywsywsyw/Card-Verify.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
原因： 
GitHub远程仓库中的README.md文件不在本地仓库中。 因为我手动在github创建了一个README.md文件

解决方案：

```bash
$ git pull --rebase origin master
```


### 2.4、从远程仓库clone至本地

只需执行一条命令
```bash
$ git clone git@github.com:username/repository.git
```
## 3、工作区<-->暂存区<-->版本库 和 git status
工作区(Working area)：就是咱们创建的本地文件夹。
暂存区(Staging area)：对文件操作(也就是需要提交的文件修改)的地方就叫暂存区。--注意：这里的修改包括对文件的增删改。
版本库(Repository)：就是你所看到的的那个隐藏的“.git”目录，它就是咱们的版本(仓)库。

### 3.1、git status命令可以让咱们随时了解当前版本库的状态
下面我们目录下新建一个index.txt，然后咱们用git status来查看该文件的状态：利用 cat index.txt 可以查看文档内容

```bash
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        index.txt（红色字体）

nothing added to commit but untracked files present (use "git add" to track)
```
红色告诉我们该本件的状态仍处于工作区。

接着咱们通过git add hellogit.txt命令将该本件添加到暂存区：

```bash
$ git add index.txt
```
执行上面命令后，没有任何显示，就说明添加成功,用git status 查看一下
```bash
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   index.txt
```
说明已经添加进了暂存区

## 4、分支管理

### 4.1、创建一个gh-pages分支，然后切换到gh-pages分支上

```bash
$ git branch gh-pages
$ git checkout gh-pages
```
可以用git branch 来查看当前分支

### 4.2、 推送本地项目的子文件到gh-pages

```bash
$ git branch gh-pages
$ git checkout gh-pages
$ git add "dist"
$ git commit -m "first commit"
$ git subtree push --prefix=dist origin gh-pages
# dist为本地项目的子文件名
```
### 4.3、合并分支
合并分支命令很简单，但请注意：合并分支一定要切换至主分支，并且要合并的分支必须commit了：

```bash
git merge gh-pages
```
合并分支只是合并内容，并不会删除分支
### 4.4、删除分支
```bash
git branch -d gh-pages
```
好了，咱又只剩master分支了，可以看到无论是创建、合并还是删除分支，速度都是非常迅速的，这也是Git一个非常重要的特点，而且工作中常用分支来完成咱们的工作。

### 新建代码库

	//在当前目录新建一个git代码库
	$ git init

	//克隆一个项目
	$ git clone https://github.com/gxhpersonal/blog.git

### 配置
Git的设置文件为`.gitconfig`，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

	// 设置提交代码时的用户信息
	git config --global user.name "gxhpersonal"
	git config --global user.email "991158744@qq.com"


### 增加/删除文件

	//添加当前目录的所有文件到暂存区
	$ git add .
	
	//添加每个变化前，都会要求确认
	//对于同一个文件的多处变化，可以实现分次提交
	$ git add -p

	//删除工作区文件，并且将这次删除放入暂存区
	$ git rm [file1] [file2] ...

	//改名文件，并且将这个改名放入暂存区
	$ git mv [file-original] [file-renamed]

### 代码提交

	//提交暂存区到仓库区
    $ git commit -m "改的内容标题"

	//提交工作区自上次commit之后的变化，直接到仓库区
	$ git commit -a

### 新建的分支push到远程服务器上
    $ git push -u origin [分支名]

### 远程代码取到本地

	$ git pull

### 本地代码提交到远程仓库

    $ git push

### 分支

	 //列出所有本地分支
	$ git branch

	//列出所有远程分支
	$ git branch -r

	//列出所有本地分支和远程分支
	$ git branch -a

	//新建一个分支，但依然停留在当前分支
	$ git branch [branch-name]

	//新建一个分支，并切换到该分支
	$ git checkout -b [branch]

	//切换到指定分支，并更新工作区
	$ git checkout [branch-name]

	//切换到上一个分支
	$ git checkout -

	//合并指定分支到当前分支
	$ git merge [branch]

	//选择一个commit，合并进当前分支
	$ git cherry-pick [commit]

	//删除分支
	$ git branch -d [branch-name]

### 指定某个commit到指定的分支
1.执行git log -3 --graph test，查看test分支下的commit:
 
注：commit 后面的hash值代表某个commit，这里把”2e1ada53819d46557b24ee7376dc61d37a06939d“这个commit提交到master。
2.执行git checkout master，切换到master分支。

3.执行 git cherry-pick 2e1ada53819d46557b24ee7376dc61d37a06939d，该commit便被提交到了master分支。
 
到此，”2e1ada53819d46557b24ee7376dc61d37a06939d“这个commit便被提交到了master分支。