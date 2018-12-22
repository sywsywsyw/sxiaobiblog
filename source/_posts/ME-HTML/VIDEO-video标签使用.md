---
title: VIDEO-video标签使用
date: 2017-01-14
tags: [html,audio,video]
categories: VIDEO
---
------

<!-- more -->
"controls": true， //是否显示控制条
"autoplay": true， //是否自动播放(iOS不支持自动播放)

/*预加载选项*/
"preload": "auto",
/*
'auto'预加载视频（需要浏览器允许）;
'metadata'仅预加载视频meta信息;
'none'不预加载;
*/

"poster": "myPoster.jpg", //视频播放前显示的图片
"loop": true, //是否循环播放
"width": 640, //设置播放器宽度
"height": 480, //设置播放器高度

"techOrder": ["flash", "html5"], //优先使用的播放模式
"streamTimeoutTime": 30 * 1000, //拉流超时时间，默认30s
