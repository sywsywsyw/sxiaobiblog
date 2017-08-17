---
title: jq插件
date: 2017-08-15 08:54:15
tags:
categories:
---
------

<!-- more -->
<link href="//cdn.bootcss.com/fullPage.js/2.7.9/jquery.fullPage.css" rel="stylesheet">
//表示根据你的协议编写

swiper 移动端广泛应用的插件

cdn 内容分发网络（content dliver network)
如果百度使用了cdn中的jquery。js 用户打开过百度
下载过这个js文件 我们使用的和他同一个cdn中的jquery。js
用户打开我们的网页时使用浏览器缓存中jquery.js

(function($){
   var lunbo = function(){
	 console.log(1)
	 }
	 $.fn.extend({
	 lunbo:lunbo;
	 })
})(jQuery)
$(document).lunbo();


## jquery 插件
(function($){
	var lunbo=function(config){
		var _config={
			interval:1500,
			step:$.noop
		}
		$.extend(_config,config)
        var ul=this.find('ul'),
            li=ul.find('li'),
            index=1,
            off=li.outerWidth(true);
           setInterval(function(){
           	ul.animate({'marginLeft':-index*off},500);
           	index+=1;
           	_config.step(index);
           	if(index===li.length){
           		index=0;
           	}
           },_config.interval)
           return this;
	}
	$.fn.extend({lunbo:lunbo});
}(jQuery))

$('.lunbo').lunbo({
		interval:2500,
        step:function(i){
            $('.pu').fadeToggle(2500)
        }
	});
	$('.xiaolunbo').lunbo();


拓展一个数组去重方法
<!-- $.quchong([1,1,1,2,3])

reverseString -->

<!-- $.quchong(function(x){
	x.each(function(i,v){

	})
})


$.extend(reverseString:function(obj){
	return obj.slipt('').reverse().join('')
})
$.rs('123') -->

@keyframes diaoluo{
   0%{
     transform: translateY(0);
   }
   100%{
     transform:translateY(300px);
   }
}
#section1{
  h1{
    position: absolute;
    top:0;
    color: white;
    width: 100%;
    text-align: center;
  }
}
#section1.active{
  h1{
    animation:diaoluo .8s ease both infinite alternate 1s;
  }
}

#section2{
    position: relative;
    %fk{
      width: 200px;
      height: 200px;
      background: pink;
    }
    .zuo,.you{
      @extend %fk;
      position: absolute;
      top: 50%;
      transition: all 5s ease;
    }
    .zuo{
      left: 0;
    }
    .you{
      right:0;
    }
}
#section2.active{
  .zuo{
    transform: translateX(200px);
  }
  .you{
    transform: translateX(-200px);
  }
}



<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<script src="jquery-1.12.0.js"></script>
<body>
	<script>
	// $.extend({
	// 	reverseString:function(s){
	// 		for( var i =s.length-1,r='';i>=0;i--){
 //               r+= s[i]
	// 		}
	// 		return r;
	// 	}
	// })
	// $.extend({
	// 	reverseString:function(s){
	// 		return r.split('').reverse().join('')  //先变成数组然后调用数组的反的方法在转回去
	// 	}
	// })

	// $.extend({
	// 	reverseString:function(s){
	// 		for( var i =s.length-1,r='';i>=0;i--){
 //               r+= s[i]
	// 		}
	// 		return r;
	// 	},
	// 	quchong:function(arr){
	// 		var r =[];
	// 		// $.each(arr,function(i,v){
	// 		// 	if( $.inArray(v,r) === -1){
	// 		// 	       r.push(v)
	// 		// 	}
	// 		// })
	// 		// return r;
	// 		var dict = {};
	// 		for(var i=0;i<arr.length;i++){
	// 			var v = arr[i]
	// 			if(!dict[v]){
	// 				dict[v] = true;
	// 				r.push(v);
	// 			}
	// 		}
	// 		return r;
	// 	}
	// })

    
 
    // $.extend({
     // quchong:function(arr){
    	// var r = [];
    	// $.each(arr,function(i,v){
     //        if( $.inArray(v,r) === -1 ){
     //        	r.push(v)
     //        }
    	// })
     //    return r;
     //  }
     // quchong:function(arr){
     // 	var dict = {};
     // 	var r = [];
     // 	for(var i=0;i<arr.length;i++){
     // 		var v = arr[i]
     // 		if(!dict[v]){
     // 			dict[v]=true;
     // 			r.push(v);
     // 		}
     // 	}
     // 	return r;
     // }   
     // reverseString:function(s){
     //      return s.split('').reverse().join()
     // }
     // reverseString:function(s){
     // 	var r='';
     // 	for( var i=s.length-1;i>=0;i--){
     // 		r += s[i]
     // 	}
     // 	return r;
     // }    	
    // })
    // var a = $.quchong([1,2,3,2,4,5,2,2,1,1])
    // console.log(a)
    // var a = $.reverseString('abc')
    // console.log(a)

    // $.extend({
    // 	fanlai:function(v){
    //        return v.split('').reverse().join('')
    // 	}
    // })
    // var a = $.fanlai('abc')
    // console.log(a)


    // $.fn.extend({
    // 	bianlan:function(){
    // 		this.css('color','red')
    // 		return this;
    // 	}
    // })
	</script>
</body>
</html>