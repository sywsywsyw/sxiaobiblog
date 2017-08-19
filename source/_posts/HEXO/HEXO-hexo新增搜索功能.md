---
title: hexo新增搜索功能
date: 2017-04-24
tags:
categories: HEXO
---
------

<!-- more -->

NexT主题支持集成 Swiftype、 微搜索、Local Search 和 Algolia,Swiftype和Algolia都只有一段时间的试用期，可以采用Hexo提供的Local Search,原理是通过hexo-generator-search插件在本地生成一个search.xml文件，搜索的时候从这个文件中根据关键字检索出相应的链接。
<a id="more"></a>

## 安装步骤

### 安装 hexo-generator-search

在站点的根目录下执行以下命令：

| 1 | $ npm install hexo-generator-search --save |

### 安装 hexo-generator-searchdb

在站点的根目录下执行以下命令：

| 1 | $ npm install hexo-generator-searchdb --save |

### 启用搜索

编辑 站点配置文件，新增以下内容到任意位置：

| 1
2
3
4
5 | search:
 path: search.xml
 field: post
 format: html
 limit: 10000 |

## 介绍其他两个插件

### 给博客添加feed

安装hexo-generator-feed

| 1 | $ npm install hexo-generator-feed --save |

配置到站点配置文件_config.yml

| 1
2
3
4
5
6
7
8
9
10 | # Extensions
## Plugins: http://hexo.io/plugins/
#RSS订阅
plugin:
- hexo-generator-feed
#Feed Atom
feed:
type: atom
path: atom.xml
limit: 20 |

最后，在你next主题下的_config.yml下，添加RSS订阅链接即可：

| 1 | rss: /atom.xml |

### 给博客生成一个站点地图

安装hexo-generator-seo-friendly-sitemap

| 1 | $ npm install hexo-generator-seo-friendly-sitemap --save |

在站点配置文件_config.yml 中添加

| 1
2 | sitemap:
 path: sitemap.xml |
