---
title: hexo功能优化
date: 2016-08-16 13:16:24
tags:
categories: HEXOS
---

## 给博客设置个人域名

### 获取ip

如果你手上恰好有一个为自己购买的域名，那正适合你刚刚搭建好的博客。
我的域名是在[aliyun.com](https://netcn.console.aliyun.com/core/domain/list)上购买的，在我搭建这个博客时候就想，我应该有一个自己的域名，换了很多组合选了一个还算满意的。当你看到这里的时候，如果也有冲动，那赶紧去看看吧，说不定过两天就没有了呢

首先，需要知道你的博客所在的服务器地址

```bash
$ ping arobot.github.io
```
得到我的博客在`151.101.73.147`上面，记下这个ip，会在后面用到。

### 设置域名解析

进入阿里云的云解析，可以为你购买的域名添加解析。

![](/images/hexo网站解析.png)

域名解析

| 选项 | 描述 |
| --- | --- |
| 记录类型 | 选择`A` |
| 主机记录 | 配置两项。一项填写`@`;另一项填写`www` |

其他的选择默认就行，配置好的结果如下

![](https://raw.githubusercontent.com/arobot/arobot.github.io/master/images/hexo_2/dns_result.jpg)

配置结果

完成了域名的解析工作之后，在博客的`source`文件下新建文件名为`CNAME`的文件，将你的域名不加协议填写进去。例如`sxiaobi.com`。

个性化域名的配置就完成了，将博客部署上去就能够通过自己的域名链接过来。

或者可以在项目文件夹中添加自己的网址

![](/images/hexo自定义域名.png)

### 部署博客

静态网页可以部署在多种服务器上，Hexo官方提供了多种[部署](https://hexo.io/zh-cn/docs/deployment.html)方式，详细的部署方式参见官网。
我是部署在`Github pages`上。
在`_config.yml`文件中配置`deploy`

<code>deploy:
  type: git
  repo: https://github.com/sywsywsyw/sywsywsyw.github.io
  branch: master</code>


## hexo新增搜索功能
NexT主题支持集成 Swiftype、 微搜索、Local Search 和 Algolia,Swiftype和Algolia都只有一段时间的试用期，可以采用Hexo提供的Local Search,原理是通过hexo-generator-search插件在本地生成一个search.xml文件，搜索的时候从这个文件中根据关键字检索出相应的链接。
<a id="more"></a>

### 安装步骤

#### 安装 hexo-generator-search

在站点的根目录下执行以下命令：

$ npm install hexo-generator-search --save |

##### 安装 hexo-generator-searchdb

在站点的根目录下执行以下命令：

$ npm install hexo-generator-searchdb --save |

#### 启用搜索

编辑 站点配置文件，新增以下内容到任意位置：

search:
path: search.xml
field: post
format: html
limit: 10000

### 介绍其他两个插件

#### 给博客添加feed

安装hexo-generator-feed

$ npm install hexo-generator-feed --save |

配置到站点配置文件_config.yml

#### Plugins: http://hexo.io/plugins/

#### RSS订阅
plugin:
- hexo-generator-feed

##### Feed Atom
feed:
type: atom
path: atom.xml
limit: 20 |

最后，在你next主题下的_config.yml下，添加RSS订阅链接即可：

rss: /atom.xml |

#### 给博客生成一个站点地图

安装hexo-generator-seo-friendly-sitemap

$ npm install hexo-generator-seo-friendly-sitemap --save |

在站点配置文件_config.yml 中添加

sitemap:
path: sitemap.xml
