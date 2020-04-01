---
title: angular
date: 2016-01-03
tags: angular
categories: 环境框架语言
---
------

<!-- more -->
# angular.js

  一个全局对象angular  
  ```
  {
     fromJson:fn,
     toJsonL:fn,
     forEach:fn,
     module:fn(str,arry)   eg:var XX = angular.module('项目名字',[])
  }
  一个模块对象的内部结构
  {
     controller:fn,
     directive:fn,
     config:fn,

     factory:fn,
     service:fn,
     constant:fn,
     value:fn,

     filter:fn,
  }
  $scope.$location,$routeProvider
  $routePramas
  ```
## 基本使用
  ```html
  html ng-app="xx"
  body ng-controller="mainctrl"
  <script>
  var xx = angular.module('xx',[])
  nw.controller('mainCtrl',['$scope',function($scope){
  }])
  </script>
  ```
## 模块
  <script src="angular-animate.js"></script>
  var xx = angular.module('xx',['ngAnimate'])
  可以自定义创建一个模块但必须遵循规则

## 控制器
   xx.controller('mainCtrl',['$scope',function($scope){
       $scope.state=true;
   }])
> 双向数据绑定  {{state}}  ng-bind
> 作用域的概念

## 装饰性指令
>  在页面的装饰性指令中可以使用angular表达式
   ng-repeat = " v in xx $index $last $first $middle $odd $even"  优先级1000 angular指令中最高的 自定义指令时切忌高过1000
   ng-bind ==={{xx.name}}   
   ng-class="{a:(state==false),b:,c:}"
   ng-if
   ng-show
   ng-hide
   ng-click
   ng-dblclick
   ng-[event]

## 组件化开发
>  angular会以ajax请求的方式去调用
   xx.directive('sywTop',[function(){
       return {
       restrict:'AECM', //E元素,A属性,C Class,M
       replace:true,  隐藏自定义标签
       template:'<div></div>'
       templageUrl:'views/tab.html',
       link:function();
       link:function($scope,elem){  先引入jQuery  永远不要在controller写dom操作和注册事件 第一个是作用域 第二个是JQ对象
         console.log($scope.shwo,elem)
         angular.elements();
          }
       }
   }])  
在weixin.html  tongxunlu.html  中只能使用一个父元素包起来 不能并排使用

## 在指令中使用jQuery
   angular 内部提供了一个jqLite;
   angular.elements() === $();
   永远不要在controller写dom操作和注册事件 第一个是作用域 第二个是JQ对象
   在指令中的link函数中不想使用Jqlite先引入jQuery 再引入angular
   angular会自动把jqLite 替换为 jQuery
   在指令的link函数中去添加事件 操作DOM

## 使用路由
   <script src="angular-route.js"></script>
   <ng-view></ng-view>
   var xx = angular.module('xx',['ngRoute']);
   xx.controller('weixinCtrl',['$scope',function($scope){}])
   xx.controller('tongxunluCtrl',['$scope',function($scope){}])
   xx.controller('faxianCtrl',['$scope',function($scope){}])
   xx.controller('meCtrl',['$scope',function($scope){}])

   	xx.config(['$routeProvider',function($routeProvider){
   	$routeProvider.when('/',{
   	controller:'indexCtrl',
   	templateUrl:'views/weixin.html'
    }).when('/weixin',{
    controller:'weixinCtrl',
    templateUrl:'views/weixin.html'
    }).when('/tongxunlu',{
    controller:'tongxunluCtrl',
    templateUrl:'views/tongxunlu.html'
    }).when('/faxian',{
    controller:'faxianCtrl',
    templateUrl:'views/faxian.html'
    }).when('/me',{
    controller:'meCtrl',
    templateUrl:'views/me.html'
    }).otherwise({
    redirectTo:'/'
    });
    }]);

##  使用动画
    <script src="angular-animate.js"></script>
    var xx = angular.moudel('xx',['ngAnimate'])  
    .ng-if   .ng-hide
    div{
    transition:all .8s ease;
    }
    div.ng-hide{
    opactiy:0;
    }
    ng-class  .add .remove
    ng-repeat .enter .enter-active
              .leave .leave-active
    ng-view   .enter .enter-active
              .leave .leave-active

##  使用内置服务
    把服务依赖注入到控制器,指令，服务，过滤器
    $scope $routeProvider


$routeProvider.when('/liaotian/:aaa',{
  controller:'liaotianCtrl',
  templateUrl:'views/liaotian.html'
})

weixin.html

li a href = "#/liaotian{{$index}}"


test.controller('liaotianCtrl',[$scope,$routeParams,function($scope,$routeParams){
    var id = $routeParams.aaa
}])


服务名字用$开头


一般推荐在自定义指令的link函数中使用jquery去操作dom元素.

在link函数中操作$scope身上的数据时一定要注意

调用$scope.$apply()方法让angular启动脏检查机制来自动刷新页面 才能实行数据的双向绑定

调用$scope.$apply()方法让angular启动脏检查机制来自动刷新页面

调用$scope.$apply()方法让angular启动脏检查机制来自动刷新页面
