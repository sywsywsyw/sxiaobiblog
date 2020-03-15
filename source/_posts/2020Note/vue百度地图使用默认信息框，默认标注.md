---
title: vue百度地图使用默认信息框，默认标注
date: 2020年3月15日 21点35分
tags: note
categories: 2020Note
---

### 项目需求：
点击marker会默认弹出一个窗口，我想不点击直接弹出，怎么搞？企业联系我们地址，百度地图页面一打开默认显示标注提示框如图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200315212323555.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)

<!-- more -->

##### 1. 首先去出vue项目本身引入的vue Baidu Map 的插件
##### 2. 在vue-cli 根目录项目中 `public>index.html`引入百度地图插件
```js
<!-- 百度地图 -->
<script type="text/javascript" src="https://api.map.baidu.com/api?v=3.0&ak=你的百度地图密钥"></script>
<!-- 百度地图搜索插件js -->
<script type="text/javascript" src="//api.map.baidu.com/library/SearchInfoWindow/1.5/src/SearchInfoWindow_min.js"></script>
<!-- 百度地图搜索插件css -->
<link rel="stylesheet" href="//api.map.baidu.com/library/SearchInfoWindow/1.5/src/SearchInfoWindow_min.css" />
```
##### 3. 页面中
```js
<!--  -->
<template>
  <section class="">
    <div
      class="bdcontainer"
      id="container"
      style="width:100%;height:100%;"
    ></div>
  </section>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';

export default {
  //import引入的组件需要注入到对象中才能使用
  components: {},
  data() {
    //这里存放数据
    return {
      realcenter: { lng: 121.56887, lat: 31.164583 } // 地图坐标
    };
  },
  //监听属性 类似于data概念
  computed: {},
  //监控data中的数据变化
  watch: {},
  //方法集合
  methods: {
    baiduMap() {
      let map = new BMap.Map("container"); //创建地图实例
      let point = new BMap.Point(this.realcenter.lng, this.realcenter.lat); //创建点坐标
      map.centerAndZoom(point, 17); // 初始化地图，设置中心点坐标和地图级别
      map.enableScrollWheelZoom(true); // 滚轮缩放
      let marker = new BMap.Marker(point); // 创建标注 点
      // map.addOverlay(marker); // 将标注添加到地图中
      // map.addControl(new BMap.NavigationControl(BMAP_ANCHOR_TOP_LEFT)); //控件左上角
      //信息窗口内容
      let sscontent =
        '<div style="font-size: 12px; padding: 5px 0px; overflow: hidden;"><div class="panoInfoBox" id="panoInfoBox" title="BHC中环中心外景"><img filter="pano_thumnail_img" class="pano_thumnail_img" width="323" height="101" border="0" alt="BHC中环中心外景" src="https://gss0.bdstatic.com/5LUZemba_QUU8t7mm9GUKT-xh_/pr/?qt=poiprv&amp;uid=a797d5e32f8007a9a80dd8ee&amp;width=323&amp;height=101&amp;quality=80&amp;fovx=200" id="pano_a797d5e32f8007a9a80dd8ee"><div filter="panoInfoBoxTitleBg" class="panoInfoBoxTitleBg"></div><a href="javascript:void(0)" filter="panoInfoBoxTitleContent" class="panoInfoBoxTitleContent">进入全景&gt;&gt;</a></div><p style="padding: 0px; margin: 0px; line-height: 18px; font-size: 12px; color: rgb(77, 77, 77);">地址：沪南路2218号</p><p style="padding: 0px; margin: 0px; line-height: 18px; font-size: 12px; color: rgb(127, 127, 127);">标签：房地产 写字楼</p></div>'; // 这的内容需要你自己F12调试打开你想要的那个提示框，拿出来信息
      let ssinfoOptions = {
        title:
          '<div class="BMap_bubble_title" style="margin:0 -5px;background:#fff;padding: 0 5px;overflow: hidden; height: auto; line-height: 30px; white-space: nowrap; width: auto;"><div style="height:26px;" id="detailDiv"><a filter="detailInfo" href="http://api.map.baidu.com/place/detail?uid=a797d5e32f8007a9a80dd8ee&amp;output=html&amp;source=jsapi&amp;operate=mapclick&amp;clicktype=tile" target="_blank" style="font-size:14px;color:#4d4d4d;font-weight:bold;text-decoration:none;" onmouseover="this.style.textDecoration=&quot;underline&quot;;this.style.color=&quot;#3d6dcc&quot;" onmouseout="this.style.textDecoration=&quot;none&quot;;this.style.color=&quot;#4d4d4d&quot;">BHC中环中心</a><a filter="detailLink" href="http://api.map.baidu.com/place/detail?uid=a797d5e32f8007a9a80dd8ee&amp;output=html&amp;source=jsapi&amp;operate=mapclick&amp;clicktype=tile" target="_blank" style="font-size:12px;color:#3d6dcc;margin-left:5px;text-decoration:none;" onmouseover="this.style.textDecoration=&quot;underline&quot;" onmouseout="this.style.textDecoration=&quot;none&quot;">详情»</a></div></div>', //标题
        width: 322, //宽度
        height: 150, //高度
        panel: "panel", //检索结果面板
        offset: {
          width: 0,
          height: -25
        },
        enableAutoPan: true, //自动平移
        enableSendToPhone: false, //  是否在信息显示短信发送按钮
        searchTypes: [
          BMAPLIB_TAB_TO_HERE, //到这里去
          BMAPLIB_TAB_FROM_HERE, //从这里出发
          BMAPLIB_TAB_SEARCH //周边检索
        ]
      };
      // var infoWindow = new BMap.InfoWindow(content, infoOptions);  // 创建信息窗口对象
      // map.openInfoWindow(infoWindow, point);      // 打开信息窗口
      // //点击红点弹出信息窗口
      // marker.addEventListener("click", function(e){
      // 	 map.openInfoWindow(infoWindow, point);      // 打开信息窗口
      // })
      var searchInfoWindow = new BMapLib.SearchInfoWindow(
        map,
        sscontent,
        ssinfoOptions
      ); // 创建带搜索得信息窗口对象
      searchInfoWindow.open(marker); // 打开带搜索得信息窗口
      map.addEventListener("click", function(e) {
        searchInfoWindow.hide(marker);
      });
      //点击红点弹出信息窗口
      marker.addEventListener("click", function(e) {
        setTimeout(() => {
          searchInfoWindow.open(marker);
        }, 100);
      });
    }
  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {
    this.baiduMap();
  },
  beforeCreate() {}, //生命周期 - 创建之前
  beforeMount() {}, //生命周期 - 挂载之前
  beforeUpdate() {}, //生命周期 - 更新之前
  updated() {}, //生命周期 - 更新之后
  beforeDestroy() {}, //生命周期 - 销毁之前
  destroyed() {}, //生命周期 - 销毁完成
  activated() {}, //如果页面有keep-alive缓存功能，这个函数会触发
  deactivated() {} //keep-alive缓存离开之后触发
};
</script>
<style lang="less" scoped>
//@import url(); 引入公共css类
</style>
```
### 成品
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020031521222871.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
