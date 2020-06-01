---
title: 禁止页面缩放提示，ie浏览器提示
date: 2020-05-02
tags: note
categories: 2020Note
---
使用了新技术总会有兼容性问题，一般公司不考虑兼容性问题，但是还是出现诸如样式错乱、无法支持ie、缩放浏览器或屏幕设置比率非100%下的网页错位，作为开发者需要给出友好的提示，提高用户体验。

### 演示地址：[https://sywsywsyw.github.io/noie-nozoom/](https://sywsywsyw.github.io/noie-nozoom/)
### 源码：[https://github.com/sywsywsyw/noie-nozoom](https://github.com/sywsywsyw/noie-nozoom)

==兼容ie8、不支持以下版本==
==兼容ie需要再服务器环境下打开== （可以使用http-server,live-server热更新服务）
==因为缩放之后所有内容也会缩放，所以需要把样式改为图片然后同步缩放图片==
==缩放图片规则为：最初尺寸除以当前比例 例如放大0.2倍就是 477/1.02==

<!-- more -->

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<title>不许ie,不许缩放</title>
	<style>
		.suiiewrap {
			/* position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			display: none;
			z-index: 99999; */
		}

		.suiiebg {
			position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			opacity: .5;
			background: #000;
		}

		.suiiemain {
			position: fixed;
			width: 480px;
			min-height: 360px;
			padding-bottom: 20px;
			top: 50%;
			left: 50%;
			margin-left: -240px;
			margin-top: -220px;
			background: #fff;
			overflow: hidden;
			text-align: center;
			z-index: 99999;
		}

		.spmhead {
			width: 100%;
			height: 50px;
			background: #4878bd;
			color: #fff;
			position: relative;
		}

		.spmhclose {
			width: 50px;
			height: 50px;
			line-height: 50px;
			text-align: center;
			position: absolute;
			right: 0;
			top: 0;
			cursor: pointer;
		}

		.spmhcloseimg {
			width: 25px;
			height: 25px;
			margin: 12.5px;
		}

		.spmcontent {
			padding: 0 10%;
			text-align: center;
		}

		.spmctitle {
			text-align: center;
			font-weight: bold;
			margin-bottom: 8px;
			font-size: 18px;
		}

		.spmctitledesc {
			text-align: center;
			font-weight: bold;
			font-size: 16px;
		}

		.spmctips {
			color: #8c8c8c;
			font-size: 14px;
			text-align: justify;
			padding: 10px 0;
		}

		.spmctsp {
			margin: 0;
			padding: 0;
			margin-bottom: 10px;
		}

		.spmctsblue {
			color: #4878bd;
			margin: 0 6px;
		}

		.spmcimg {
			width: 40%;
			margin: 20px;
		}

		.spmfnotips {
			width: 200px;
			height: 40px;
			line-height: 40px;
			text-align: center;
			margin: 0 auto;
			background: #4878bd;
			font-size: 16px;
			color: #fff;
			cursor: pointer;
		}


		/* 缩放 */
		.suizoomwrap {
			/* position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			display: none;
			z-index: 99999; */
		}

		.suizoombg {
			position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			opacity: .5;
			background: #000;
		}

		.suizoomcontent {
			position: fixed;
			width: 477px;
			height: 412px;
			top: 50%;
			left: 50%;
			margin-left: -237px;
			margin-top: -206px;
			background: #fff;
			border-radius: 0;
			overflow: hidden;
			text-align: center;
			z-index: 99999;
			box-shadow: 0px 0px 13px 0px rgba(6, 193, 174, 0.15);
			/* box-shadow: 1px 8px 25px 0px rgba(65, 115, 178, 0.1); */
		}

		.szcimg {
			width: 100%;
			height: 100%;
		}

		.szcclose {
			width: 10.5%;
			height: 12%;
			text-align: center;
			position: absolute;
			right: 0;
			top: 0;
			cursor: pointer;
			background: #000;
			opacity: 0;
		}

		.szctips {
			width: 42%;
			height: 9.8%;
			text-align: center;
			margin: 0 auto;
			background: #4878bd;
			font-size: 16px;
			color: #fff;
			cursor: pointer;
			position: absolute;
			left: 29%;
			bottom: 4.4%;
			background: #000;
			opacity: 0;
		}
	</style>
</head>

<body>
	<!-- ie 提示 -->
	<div class="suiiewrap">
		<!-- <div class="suiiebg"></div> -->
		<div class="suiiemain">
			<div class="spmhead">
				<div class="spmhtitle"></div>
				<div class="spmhclose">
					<img src="./close.png" alt="关闭" class="spmhcloseimg">
				</div>
			</div>
			<div class="spmcontent">
				<img src="./warn.png" alt="警告图片" class="spmcimg">
				<div class="spmctitle">暂不支持IE类型浏览器</div>
				<div class="spmctips">
					<p class="spmctsp">1. IE浏览器下会出现样式错位等现象</p>
					<p class="spmctsp">2. 请尝试更换其他浏览器，如360浏览器、QQ浏览器、谷歌浏览器......</p>
					<p class="spmctsp">3. 双核浏览器请切换成极速内核</p>
				</div>
			</div>
			<!-- <div class="spmcontent">
				<img src="./warn.png" alt="" class="spmcimg">
				<div class="spmctitle">页面缩放比例不正确</div>
				<div class="spmctitledesc">可能会影响某些功能的正常使用</div>
				<div class="spmctips">
					<p class="spmctsp">1. 请尝试调整浏览器缩放比例为<span class="spmctsblue">100%</span>(快捷键 ctrl+0）</p>
					<p class="spmctsp">2. 请尝试调整系统显示比例为<span class="spmctsblue">100%</span>(控制面板&nbsp;\&nbsp;显示 设置)</p>
				</div>
			</div> -->
			<div class="spmfooter">
				<div class="spmfnotips">不再提醒</div>
			</div>
		</div>
	</div>

	<!-- zoom 缩放 提示 -->
	<div class="suizoomwrap">
		<!-- <div class="suizoombg"></div> -->
		<div class="suizoomcontent">
			<img src="./zoomtips.png" alt="" class="szcimg">
			<div class="szcclose">关闭</div>
			<div class="szctips">不在提醒</div>
		</div>
	</div>
	<script>
		// 解决ie8 以下不支持 getElementsByClassName
		function getElementsByClassName(className, root, tagName) { //root：父节点，tagName：该节点的标签名。 这两个参数均可有可无
			if (root) {
				root = typeof root == "string" ? document.getElementById(root) : root;
			} else {
				root = document.body;
			}
			tagName = tagName || "*";
			if (document.getElementsByClassName) { //如果浏览器支持getElementsByClassName，就直接的用
				return root.getElementsByClassName(className);
			} else {
				var tag = root.getElementsByTagName(tagName); //获取指定元素
				var tagAll = []; //用于存储符合条件的元素
				for (var i = 0; i < tag.length; i++) {
					//遍历获得的元素 
					for (var j = 0, n = tag[i].className.split(' '); j < n.length; j++) {
						//遍历此元素中所有class的值，如果包含指定的类名，就赋值给tagnameAll
						if (n[j] == className) {
							tagAll.push(tag[i]);
							break;
						}
					}
				}
				return tagAll;
			}
		}
	</script>
	<script>
        var u = navigator.userAgent || "";
		var isMobAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; //android终端
		var isMobiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
		console.log(isMobAndroid,isMobiOS)
		// 弹框元素
		var suiWrapObj = getElementsByClassName('suiiewrap')[0];
		// 关闭按钮元素
		var spmhCloseObj = getElementsByClassName('spmhclose')[0];
		// 不再提醒元素
		var noTipsObj = getElementsByClassName('spmfnotips')[0];
		// 不在提醒 sessionStorage
		var isNoIEVal = sessionStorage.getItem('isNoIE');

		function suiWrapShow() {
			// 如果点击过不在提醒
			if (isNoIEVal != 'noietips') {
				suiWrapObj.style.display = "block";
			}
		}

		function suiWrapHide() {
			suiWrapObj.style.display = "none";
		}
        // 判断是否是ie内核
        var isIE = window.ActiveXObject || "ActiveXObject" in window;
		function isIeFn() {
			if (isIE) {
				suiWrapShow();
			} else {
				suiWrapHide();
			}
		}
		if( !isMobAndroid && !isMobiOS ){
		  isIeFn();
		}
		// 关闭提示
		spmhCloseObj.onclick = function () {
			suiWrapHide();
		}
		// 不再提醒
		noTipsObj.onclick = function () {
			sessionStorage.setItem('isNoIE', 'noietips');
			suiWrapHide();
		}

		// 判断缩放比例 小于100 大于100 都为缩放
		function detectZoom() {
			var ratio = 0,
				screen = window.screen,
				ua = navigator.userAgent.toLowerCase();

			if (window.devicePixelRatio !== undefined) {
				ratio = window.devicePixelRatio;
			} else if (~ua.indexOf('msie')) {
				if (screen.deviceXDPI && screen.logicalXDPI) {
					ratio = screen.deviceXDPI / screen.logicalXDPI;
				}
			} else if (window.outerWidth !== undefined && window.innerWidth !== undefined) {
				ratio = window.outerWidth / window.innerWidth;
			}

			if (ratio) {
				ratio = Math.round(ratio * 100);
			}

			return ratio;
		};
		// 缩放比例
		var zoomVal = 100;
		// 缩小比例
		var zoomSmallVal = 0;
		// 放大比例
		var zoomBigVal = 0;
		// 缩放弹框
		var zoomWrapObj = getElementsByClassName('suizoomwrap')[0];
		// 缩放关闭按钮
		var zoomCloseObj = getElementsByClassName('szcclose')[0];
		// 缩放不再提醒
		var zoomTipsObj = getElementsByClassName('szctips')[0];
		// 缩放内容
		var zoomContentObj = getElementsByClassName('suizoomcontent')[0];
		// 缩放内容css
		var zoomCotentVal = {
			width: 477,
			height: 412,
			marginLeft: 237,
			marginTop: 206
		}
		// 不在提醒 sessionStorage
		var isNoZoomVal = sessionStorage.getItem('isNoZoom');
		zoomVal = detectZoom();
		noZoomShowOrHide();
		if (!isIE) {
			window.addEventListener('resize', function () {
				zoomVal = detectZoom();
				noZoomShowOrHide();
			})
		}
		// 控制nozoom弹框显示隐藏
		function noZoomShowOrHide() {
			var u = navigator.userAgent || "";
			var isMobAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; //android终端
			var isMobiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
			if( isMobAndroid || isMobiOS ){
			  suiWrapHide();
			  zoomWrapObj.style.display = "none";
			  return;
			}
			if (isIE) {
			  zoomWrapObj.style.display = "none";
			  return;
			}
			console.log(zoomVal)
			var zoom100Val = zoomVal / 100;
			zoomCotentVal = {
				width: 477 / zoom100Val,
				height: 412 / zoom100Val,
				marginLeft: 237 / zoom100Val,
				marginTop: 206 / zoom100Val,
			}
			console.log(zoomBigVal, zoomSmallVal, zoom100Val)
			console.log(zoomCotentVal)
			if (zoomVal != 100) {
				if (isNoZoomVal != 'nozoomtips') {
					zoomWrapObj.style.display = "block";
				}
			} else {
				zoomWrapObj.style.display = "none";
			}

			zoomContentObj.style.cssText = "width: " + zoomCotentVal.width + "px;height:" + zoomCotentVal.height +
				"px;margin-left:-" + zoomCotentVal.marginLeft + "px;margin-top:-" + zoomCotentVal.marginTop + "px;"
		}
		zoomCloseObj.onclick = function () {
			zoomWrapObj.style.display = "none";
		}
		zoomTipsObj.onclick = function () {
			sessionStorage.setItem('isNoZoom', 'nozoomtips');
			zoomWrapObj.style.display = "none";
		}
	</script>
</body>

</html>
```<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<title>不许ie,不许缩放</title>
	<style>
		.suiiewrap {
			/* position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			display: none;
			z-index: 99999; */
		}

		.suiiebg {
			position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			opacity: .5;
			background: #000;
		}

		.suiiemain {
			position: fixed;
			width: 480px;
			min-height: 360px;
			padding-bottom: 20px;
			top: 50%;
			left: 50%;
			margin-left: -240px;
			margin-top: -220px;
			background: #fff;
			overflow: hidden;
			text-align: center;
			z-index: 99999;
		}

		.spmhead {
			width: 100%;
			height: 50px;
			background: #4878bd;
			color: #fff;
			position: relative;
		}

		.spmhclose {
			width: 50px;
			height: 50px;
			line-height: 50px;
			text-align: center;
			position: absolute;
			right: 0;
			top: 0;
			cursor: pointer;
		}

		.spmhcloseimg {
			width: 25px;
			height: 25px;
			margin: 12.5px;
		}

		.spmcontent {
			padding: 0 10%;
			text-align: center;
		}

		.spmctitle {
			text-align: center;
			font-weight: bold;
			margin-bottom: 8px;
			font-size: 18px;
		}

		.spmctitledesc {
			text-align: center;
			font-weight: bold;
			font-size: 16px;
		}

		.spmctips {
			color: #8c8c8c;
			font-size: 14px;
			text-align: justify;
			padding: 10px 0;
		}

		.spmctsp {
			margin: 0;
			padding: 0;
			margin-bottom: 10px;
		}

		.spmctsblue {
			color: #4878bd;
			margin: 0 6px;
		}

		.spmcimg {
			width: 40%;
			margin: 20px;
		}

		.spmfnotips {
			width: 200px;
			height: 40px;
			line-height: 40px;
			text-align: center;
			margin: 0 auto;
			background: #4878bd;
			font-size: 16px;
			color: #fff;
			cursor: pointer;
		}


		/* 缩放 */
		.suizoomwrap {
			/* position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			display: none;
			z-index: 99999; */
		}

		.suizoombg {
			position: fixed;
			left: 0;
			top: 0;
			width: 100%;
			height: 100%;
			opacity: .5;
			background: #000;
		}

		.suizoomcontent {
			position: fixed;
			width: 477px;
			height: 412px;
			top: 50%;
			left: 50%;
			margin-left: -237px;
			margin-top: -206px;
			background: #fff;
			border-radius: 0;
			overflow: hidden;
			text-align: center;
			z-index: 99999;
			box-shadow: 0px 0px 13px 0px rgba(6, 193, 174, 0.15);
			/* box-shadow: 1px 8px 25px 0px rgba(65, 115, 178, 0.1); */
		}

		.szcimg {
			width: 100%;
			height: 100%;
		}

		.szcclose {
			width: 10.5%;
			height: 12%;
			text-align: center;
			position: absolute;
			right: 0;
			top: 0;
			cursor: pointer;
			background: #000;
			opacity: 0;
		}

		.szctips {
			width: 42%;
			height: 9.8%;
			text-align: center;
			margin: 0 auto;
			background: #4878bd;
			font-size: 16px;
			color: #fff;
			cursor: pointer;
			position: absolute;
			left: 29%;
			bottom: 4.4%;
			background: #000;
			opacity: 0;
		}
	</style>
</head>

<body>
	<!-- ie 提示 -->
	<div class="suiiewrap">
		<!-- <div class="suiiebg"></div> -->
		<div class="suiiemain">
			<div class="spmhead">
				<div class="spmhtitle"></div>
				<div class="spmhclose">
					<img src="./close.png" alt="关闭" class="spmhcloseimg">
				</div>
			</div>
			<div class="spmcontent">
				<img src="./warn.png" alt="警告图片" class="spmcimg">
				<div class="spmctitle">暂不支持IE类型浏览器</div>
				<div class="spmctips">
					<p class="spmctsp">1. IE浏览器下会出现样式错位等现象</p>
					<p class="spmctsp">2. 请尝试更换其他浏览器，如360浏览器、QQ浏览器、谷歌浏览器......</p>
					<p class="spmctsp">3. 双核浏览器请切换成极速内核</p>
				</div>
			</div>
			<!-- <div class="spmcontent">
				<img src="./warn.png" alt="" class="spmcimg">
				<div class="spmctitle">页面缩放比例不正确</div>
				<div class="spmctitledesc">可能会影响某些功能的正常使用</div>
				<div class="spmctips">
					<p class="spmctsp">1. 请尝试调整浏览器缩放比例为<span class="spmctsblue">100%</span>(快捷键 ctrl+0）</p>
					<p class="spmctsp">2. 请尝试调整系统显示比例为<span class="spmctsblue">100%</span>(控制面板&nbsp;\&nbsp;显示 设置)</p>
				</div>
			</div> -->
			<div class="spmfooter">
				<div class="spmfnotips">不再提醒</div>
			</div>
		</div>
	</div>

	<!-- zoom 缩放 提示 -->
	<div class="suizoomwrap">
		<!-- <div class="suizoombg"></div> -->
		<div class="suizoomcontent">
			<img src="./zoomtips.png" alt="" class="szcimg">
			<div class="szcclose">关闭</div>
			<div class="szctips">不在提醒</div>
		</div>
	</div>
	<script>
		// 解决ie8 以下不支持 getElementsByClassName
		function getElementsByClassName(className, root, tagName) { //root：父节点，tagName：该节点的标签名。 这两个参数均可有可无
			if (root) {
				root = typeof root == "string" ? document.getElementById(root) : root;
			} else {
				root = document.body;
			}
			tagName = tagName || "*";
			if (document.getElementsByClassName) { //如果浏览器支持getElementsByClassName，就直接的用
				return root.getElementsByClassName(className);
			} else {
				var tag = root.getElementsByTagName(tagName); //获取指定元素
				var tagAll = []; //用于存储符合条件的元素
				for (var i = 0; i < tag.length; i++) {
					//遍历获得的元素 
					for (var j = 0, n = tag[i].className.split(' '); j < n.length; j++) {
						//遍历此元素中所有class的值，如果包含指定的类名，就赋值给tagnameAll
						if (n[j] == className) {
							tagAll.push(tag[i]);
							break;
						}
					}
				}
				return tagAll;
			}
		}
	</script>
	<script>
        var u = navigator.userAgent || "";
		var isMobAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; //android终端
		var isMobiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
		console.log(isMobAndroid,isMobiOS)
		// 弹框元素
		var suiWrapObj = getElementsByClassName('suiiewrap')[0];
		// 关闭按钮元素
		var spmhCloseObj = getElementsByClassName('spmhclose')[0];
		// 不再提醒元素
		var noTipsObj = getElementsByClassName('spmfnotips')[0];
		// 不在提醒 sessionStorage
		var isNoIEVal = sessionStorage.getItem('isNoIE');

		function suiWrapShow() {
			// 如果点击过不在提醒
			if (isNoIEVal != 'noietips') {
				suiWrapObj.style.display = "block";
			}
		}

		function suiWrapHide() {
			suiWrapObj.style.display = "none";
		}
        // 判断是否是ie内核
        var isIE = window.ActiveXObject || "ActiveXObject" in window;
		function isIeFn() {
			if (isIE) {
				suiWrapShow();
			} else {
				suiWrapHide();
			}
		}
		if( !isMobAndroid && !isMobiOS ){
		  isIeFn();
		}
		// 关闭提示
		spmhCloseObj.onclick = function () {
			suiWrapHide();
		}
		// 不再提醒
		noTipsObj.onclick = function () {
			sessionStorage.setItem('isNoIE', 'noietips');
			suiWrapHide();
		}

		// 判断缩放比例 小于100 大于100 都为缩放
		function detectZoom() {
			var ratio = 0,
				screen = window.screen,
				ua = navigator.userAgent.toLowerCase();

			if (window.devicePixelRatio !== undefined) {
				ratio = window.devicePixelRatio;
			} else if (~ua.indexOf('msie')) {
				if (screen.deviceXDPI && screen.logicalXDPI) {
					ratio = screen.deviceXDPI / screen.logicalXDPI;
				}
			} else if (window.outerWidth !== undefined && window.innerWidth !== undefined) {
				ratio = window.outerWidth / window.innerWidth;
			}

			if (ratio) {
				ratio = Math.round(ratio * 100);
			}

			return ratio;
		};
		// 缩放比例
		var zoomVal = 100;
		// 缩小比例
		var zoomSmallVal = 0;
		// 放大比例
		var zoomBigVal = 0;
		// 缩放弹框
		var zoomWrapObj = getElementsByClassName('suizoomwrap')[0];
		// 缩放关闭按钮
		var zoomCloseObj = getElementsByClassName('szcclose')[0];
		// 缩放不再提醒
		var zoomTipsObj = getElementsByClassName('szctips')[0];
		// 缩放内容
		var zoomContentObj = getElementsByClassName('suizoomcontent')[0];
		// 缩放内容css
		var zoomCotentVal = {
			width: 477,
			height: 412,
			marginLeft: 237,
			marginTop: 206
		}
		// 不在提醒 sessionStorage
		var isNoZoomVal = sessionStorage.getItem('isNoZoom');
		zoomVal = detectZoom();
		noZoomShowOrHide();
		if (!isIE) {
			window.addEventListener('resize', function () {
				zoomVal = detectZoom();
				noZoomShowOrHide();
			})
		}
		// 控制nozoom弹框显示隐藏
		function noZoomShowOrHide() {
			var u = navigator.userAgent || "";
			var isMobAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; //android终端
			var isMobiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
			if( isMobAndroid || isMobiOS ){
			  suiWrapHide();
			  zoomWrapObj.style.display = "none";
			  return;
			}
			if (isIE) {
			  zoomWrapObj.style.display = "none";
			  return;
			}
			console.log(zoomVal)
			var zoom100Val = zoomVal / 100;
			zoomCotentVal = {
				width: 477 / zoom100Val,
				height: 412 / zoom100Val,
				marginLeft: 237 / zoom100Val,
				marginTop: 206 / zoom100Val
			}
			console.log(zoomBigVal, zoomSmallVal, zoom100Val)
			console.log(zoomCotentVal)
			if (zoomVal != 100) {
				if (isNoZoomVal != 'nozoomtips') {
					zoomWrapObj.style.display = "block";
				}
			} else {
				zoomWrapObj.style.display = "none";
			}

			zoomContentObj.style.cssText = "width: " + zoomCotentVal.width + "px;height:" + zoomCotentVal.height +
				"px;margin-left:-" + zoomCotentVal.marginLeft + "px;margin-top:-" + zoomCotentVal.marginTop + "px;"
		}
		zoomCloseObj.onclick = function () {
			zoomWrapObj.style.display = "none";
		}
		zoomTipsObj.onclick = function () {
			sessionStorage.setItem('isNoZoom', 'nozoomtips');
			zoomWrapObj.style.display = "none";
		}
	</script>
</body>
</html>
```
图一是透明关闭按钮自己找一下昂就这句话后面呢![关闭按钮](https://img-blog.csdnimg.cn/20200514150050423.png)
图二![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514150107859.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)
图三![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514150159405.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1MjM4OTc5,size_16,color_FFFFFF,t_70)