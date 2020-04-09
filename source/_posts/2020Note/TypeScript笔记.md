---
title: TypeScript笔记
date: 2020年4月3日 21点21分
tags: note
categories: 2020Note
---



typescript 是javascript的超集，是一种编程语言

### 1. typescript和javascript的区别
* 更适合大型应用程序
* js的超集，类似于less,sass,  最终会转为javascript
* 跨平台（浏览器，操作系统linux,mac）且开源
* 开始于js,终止于js.上手成本低，易于学习
* 重用js,可以引入js流行的库  echarts
* typescript 类、接口、模块，更易于组件的编写和维护
* ts是强类型，js是弱类型。

为什么要学习typescript?

> vue、React、ng、都推荐使用typescript。

### 2. 开发环境的安装
```bash
npm -v
node -v
npm install typescript -g
tsc --version
npm init -y   //-y代表全部默认
tsc --init   // 生成ts配置
npm install @type/node --dev-save
```
新建helloTs.ts
```js
var message:string = 'helloTypeScript';
console.log(message);
```
命令：helloTs.ts转为helloTs.js
```bash
tsc helloTs
```
使用node命令执行helloTs.js
```bash
node helloTs.js   
// helloTypeScript
```
### 3. 变量类型
弱类型   数据类型可以被忽略的语言。与强类型语言相反, 一个变量可以赋不同数据类型的值,允许将一块内存看做多种类型,比如直接将整型变量与字符变量相加
强类型   使之强制数据类型定义的语言。没有强制类型转化前,不允许两种不同类型的变量相互操作。
 
* undefined：undefined类型
* number：数值类型
* string: 字符串类型
* Boolean: 布尔类型
* enum：枚举类型   一般用于大写声明， 一个类的对象是有限且固定的,这种情况下我们使用枚举类就比* 较方便
* any：任意类型   万能类型、刚开始是数字类型，后来变成了字符串，然后又变成了，true,如果使用any类型就不会报错了。
* void: 空类型
* Array: 数组类型
* Tuple: 元祖类型
* Null: 空类型

```js
// 变量类型  ts属于强类型，声明的时候必须告诉程序，这是个什么类型，js属于弱类型。

// undefined
let undeFined:any;
console.log(undeFined);

// string
let stringVariable:string = '我是string variable';
console.log(stringVariable);

// number
let numberVariable:number = 8888;
console.log(numberVariable);

// Boolean
let booleanVariable:Boolean = true;
console.log(booleanVariable);

// enum 枚举类型，用于一个类的对象是有限且固定的，比如男人，女人，中性人，一般使用大写命名
enum PEOPLE{man='男人',woman='女人',genderBender='中性人'};
console.log(PEOPLE.man);

// any 任意类型  我们js习惯了弱类型语言，这个类型就是允许你随意改变变量的类型
let anyVariable:any = 888;
anyVariable = true;
anyVariable = 'anyVariable从数字888变为布尔true最后变成了字符串类型,';
console.log(anyVariable);

// Array
let arrayVariable = [1,2,3,4,5];
console.log(arrayVariable);

// null 
let nullVariable = null;
console.log(nullVariable);


// undefined
// 我是string variable
// 8888
// true
// 男人
// anyVariable从数字888变为布尔true最后变成了字
// 符串类型,
// [ 1, 2, 3, 4, 5 ]
// null
```

### 4.函数

形参：函数方法中声明的参数
实参：函数调用时候传递进去的值

#### 定义一个函数
```js
// 定义函数
function searchSmallSister(age:number):string{
    return 'sxiaobi找了一个'+age+'岁的小姐姐'
}
let result:string = searchSmallSister(28);
console.log(result,'我是基本定义函数 parasm:number');
// sxiaobi找了一个28岁的小姐姐 我是基本定义函数 parasm:number
```

##### 有可选参数的函数
params?:string
```js
// 可选参数的函数
function searchSmallGirl(age:number,stature?:number):string{
    return 'sxiaobi找了一个' + age + '岁' + stature+'cm的小姐姐'
}
let girlResult:string = searchSmallGirl(20,178);
console.log(girlResult,'我是可选参数身高 params?:number的小姐姐');
// sxiaobi找了一个20岁178cm的小姐姐 我是可选参数身高 params?:number的小姐姐
```
##### 有默认值的函数
params:string='小姐姐'
```js
function searchYoungLaday(age: number = 20, stature: number = 170,thorax:string='34D'):string{
    return `sxiaobi找了一个${age}岁${stature}cm${thorax}的小姐姐`;
}
let youngLaday:string = searchYoungLaday();
console.log(youngLaday,'我是默认参数 params:string="34D"的小姐姐');
// sxiaobi找了一个20岁170cm34D的小姐姐 我是默认参数 params:string="34D"的小姐姐
```
##### 有剩余参数的函数
...params:string[]
```js
// 有剩余参数的函数
function searchSmallWoman(...age:string[]):string{
    let yy:string = '找了一个';
    for(let index in age){
        let indexT: any = index;
        yy = yy + age[indexT];
        if ( indexT < age.length-1){
            yy = yy+ '、'; 
      }
    }
    return `sxiaobi${yy}的小姐姐`;
}
let smallWoman:string = searchSmallWoman('20岁','175cm','34D','上海陆家嘴');
console.log(smallWoman,'我是有剩余参数的 ...params:string[]')
// sxiaobi找了一个20岁、175cm、34D、上海陆家嘴的小姐姐 我是有剩余参数的 ...params:string[]
```

#### 三种函数的定义方法

##### 函数声明法
```js
function add(one: number, two: number): number {
    return one + two;
}
console.log(add(1, 2));
```
##### 函数表达式法
```js
var plus = function (one: number, two: number): number {
    return one + two;
}
console.log(plus(1, 2));
```
##### 箭头函数
```js
var sum = (one: number, two: number): number => {
    return one + two;
}
console.log(sum(1, 2));
```

#### 引用类型 Array String Date RegExp

##### 数组
```js
// 数组
// 字面量赋值法
let arr1:number[] = [1,2,3];
let arr2:Array<string> = ['a','b','c'];

// 构造函数赋值法 new
let arr3:number[] = new Array(1,2,3,4);
console.log(arr1,arr2,arr3);
// [ 1, 2, 3 ] [ 'a', 'b', 'c' ] [ 1, 2, 3, 4 ]
```
##### 字符串
```js
// 字符串
let string1:string = 'sxiaobi';
let string2:String = new String('sxiaobi');
console.log(string1, string2);
// sxiaobi [String: 'sxiaobi']
```
##### 
```js
// 日期
// 不传递参数
let date:Date = new Date();
// 传递一个数字
let dateNumber:Date = new Date(1000);
let dateString:Date = new Date('2019/09/07 05:06:30');
console.log(date, dateNumber, dateString);
// 2020-04-09T09:41:10.681Z 1970-01-01T00:00:01.000Z 2019-09-06T21:06:30.000Z
```








