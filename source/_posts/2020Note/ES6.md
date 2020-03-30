---
title: ES6笔记
date: 2020年3月18日 21点21分
tags: note
categories: 2020Note
---


### 1. var、const、let的区别
- var 全局变量
- let  局部变量
- const 常量 一般用于属性名，用于从常量命名开始的那一刻就不想让改变的属性名。

### 2. 变量的解构赋值
1. `数组解构`
- 左右两边需要解构相同
```js
let [a,b,c] = [1,2,3];
console.log(a,b,c)
// 1,2,3
let [a,[b,c],d]=[1,2,4];
console.log(a,b,c,d)
// 报错 Uncaught TypeError: [1,2,4] is not iterable at <anonymous>:1:17
```
- 默认赋值的写法
```js
let [a=2,b=3,c=5] = [1];
console.log(a,b,c)
// 1,3,5
```
2. `对象解构`
- 根据属性名进行解构
```js
let {a,b,c} = {a:'sxiaobi',b:25};
console.log(a,b,c)
// sxiaobi 25 undefined
```
- 默认赋值写法
```js
let {a,b,c=10} = {a:'sxiaobi',b:25};
console.log(a,b,c)
// sxiaobi 25 10
```
- 如果变量先声明，再赋值需要使用`()`包裹起来
```js
// success 
let aa;
({aa} = {aa:11});
console.log(aa)
// 11
// error
let aa;
{aa} = {aa:11};
console.log(aa)
// Uncaught SyntaxError: Unexpected token =
```
- `字符串解构`
```js
let [a,b,c,d,e,f,g] = 'sxiaobi';
console.log(a,b,c,d,e,f,g)
// s x i a o b i
```

> 何时用单引号，何时用双引号??？
> 虽然在JavaScript当中，双引号和单引号都可以表示字符串, 为了避免混乱，我们建议在HTML中使用双引号，在JavaScript中使用单引号，但为了兼容各个浏览器，也为了解析时不会出错，定义JSON对象时，最好使用双引号

#### 3. 字符串
- 字符串模板 `${txt}`
```js
let tt = 123;
let aa = `sxiaobi${tt}`;
console.log(aa);
// sxiaobi123
```
`支持嵌套html标签、支持简单运算`

- 字符串查找 `includesOf`  
```js
let findStr = 'sx';
let string = 'sxiaobi'
console.log(string.includes(findStr))
// true
// es5
console.log(string.indexOf(findStr)>-1)
```
- 查找字符串首 有没有  `startsWith`
```js
let findStr = 'sx';
let string = 'sxiaobi'
console.log(string.startsWith(findStr))
// true
```
- 判断字符串尾部是否存在 `endsWith`
```js
let findStr = 'bi';
let string = 'sxiaobi'
console.log(string.endsWith(findStr))
// true
```
- 字符串复制 ``repeat`
```js
let str = '1';
let strRepeat = str.repeat(5);
console.log(strRepeat);
// 11111
```
#### 4. 扩展运算符与剩余运算符
> 可以很好的为我们解决参数和对象数组未知情况下的编程
- 扩展运算符号 `...`
```js
function sxiaobi(...arg){
  console.log(arg[0])
  console.log(arg[1])
  console.log(arg[2])
}
sxiaobi(1,2,3)
// 1,2,3
```
>扩展运算符的用处：
我们先用一个例子说明，我们声明两个数组arr1和arr2，然后我们把arr1赋值给arr2，然后我们改变arr2的值，你会发现arr1的值也改变了，因为我们这是对内存堆栈的引用，而不是真正的赋值。
```js
let arr1 = [1,2,3];
let arr2 = arr1;
arr2.push(4)
console.log(arr1)
// 1,2,3,4
```
```js
let arr1 = [1,2,3];
let arr2 = [...arr1];
arr2.push(4)
console.log(arr1)
// 1,2,3
```
- `rest`运算符 
```js
function sxiaobi(first,...arg){
    console.log(arg.length);
}
sxiaobi(0,1,2,3,4,5,6,7);
// 1,2,3,4,5,6,7
```
#### 5. 数字的操作
- 判断是否是NaN `isNaN`
```js
console.log(Number.isNaN(1))
// false
console.log(Number.isNaN(NaN))
// true
```
- 判断是否是整数 `isInteger`
```js
console.log(Number.isInteger('a')) 
// false
console.log(Number.isInteger(1.1))
// false
console.log(Number.isInteger(1))
// true
```
- 整数转换 `parseInt` 和 浮点型转换 `parseFloat`
```js
let a='9.18';
console.log(Number.parseInt(a)); 
console.log(Number.parseFloat(a));
// 9
// 9.18
```
- 整数取值范围 `2的53次方`
```js
let a = Math.pow(2,53)-1;
console.log(a)
// 9007199254740991
```
- 最大安全整数 `MAX_SAFE_INTEGER`
```js
console.log(Number.MAX_SAFE_INTEGER)
// 9007199254740991
```
- 最小安全整数 `MIN_SAFE_INTEGE`
```js
console.log(Number.MIN_SAFE_INTEGER)
// -9007199254740991
```
- 安全整数判断 `isSafeInteger( )`
```js
console.log(Number.isSafeInteger(11110))
// true
```
#### 6. 数组的方法
- `Array.from()` JOSN对象转数组
```js
let obj = {
   '0':'sun',
   '1':'xiao',
   '2':'bi',
   length:3
}
console.log(Array.from(obj))
// ['sun','xiao','bi']
```
- `Array.of()` 类数组对象转为数据，支持数字、字符串 
```js
console.log(Array.of(1,2,3,4))
// [1,2,3,4]
let str = 'sun,xiao,bi';
console.log(Array.of(str));
// ['sun','xiao','bi']
```
实例方法
- arr.`find() `  从数组中查找一个值
```js
// 查找一个大于2的值
let arr = [1,2,3];
console.log(arr.find((val,startIndex,endIndex)=>{
   return val>2;
}))
// 3 
```
- `for of` 循环数组
```js
// 常规写法
let arr = [1,2,3,4];
for(let val of arr){
  console.log(val)
}
// 1 2 3 4
// 获取下标
let arr = [1,2,3,4];
for(let val of arr.keys()){
  console.log(val)
}
// 0 1 2 3
// 同时输出内容和下标
let arr = [1,2,3,4];
for(let [index,val] of arr.entries()){
  console.log(index,val)
}
// 0 1 、1 2 、2 3 、3 4
// 一般直接使用`for in`,`forEach`
let arr = [1,2,3,4];
arr.forEach((index,val)=>{
  console.log(index,val)
})
let arr = [1,2,3,4];
for(let i in arr){
  console.log(i,arr[i])
  // 这的i的类型是字符串
}
```
- 数组的`去重`
==filter - 无法识别NaN== 
```js
var arr=[1,2,1,'1',null,null,undefined,undefined,NaN,NaN]
var arr2 = arr.filter((x,index,self)=>self.indexOf(x)===index);
console.log(arr2) // [1, 2, "1", null, undefined]
```
```js
var arr=[1,2,1,'1',null,null,undefined,undefined,NaN,NaN]
var res=Array.from(new Set(arr));//{1,2,"1",null,undefined,NaN}
console.log(res)  // [1, 2, "1", null, undefined,NaN]
var newarr=[...new Set(arr)]
console.log(newarr) // [1, 2, "1", null, undefined,NaN]
```
- 数组对象的去重 `reduce`
> reduce() 方法接收一个函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。
reduce() 可以作为一个高阶函数，用于函数的 compose。
注意: reduce() 对于空数组是不会执行回调函数的。
```js
let person = [
     {id: 0, name: "小明"},
     {id: 1, name: "小张"},
     {id: 2, name: "小李"},
     {id: 3, name: "小孙"},
     {id: 1, name: "小周"},
     {id: 2, name: "小陈"},  
];
let obj = {};
let peon = person.reduce((cur,next)=>{
   obj[next.id]? "":obj[next.id] = true&& cur.push(next);
   return cur;
},[]) // 设置cur的默认类型为初始值空的数组
console.log(peon)
```
#### 7. 箭头函数和扩展
- `默认值`
```js
function add(a,b=1){
    return a+b; 
}
add(1)
// 2
```
- 主动抛出异常  `throw new Error()`
```js
function add(a,b=1){
    if( a == 1){
       throw new Error('主动抛出了异常错误') 
    }
    return a+b; 
}
add(1)
// Uncaught Error: 主动抛出了异常错误
//    at add (<anonymous>:3:14)
//    at <anonymous>:7:1
```
- 严格模式可以在函数体内使用 `use strict`
> es5 中严格模式必须声明在页面头部
```js
function add(a,b){
   `use strict`
   return a+b;
}
console.log(add(1,2));
// 3
```
- 箭头函数  `()=>{}`
>`箭头函数没有自己的this, 它的this是继承而来; 默认指向在定义它时所处的对象(宿主对象)`
> 严格模式下 this 指向 undefined
> 一般 全局下 指向 window
> 对象的方法中调用指向 调用该方法的对象
> 构造函数里的this 指向创建出来的实例
>> `改变this指向的方法`
>> call， call(thisScope, arg1, arg2, arg3...)  传入多个参数  立即执行
>> apply， apply(thisScope,[arg1,arg2,arg3])  传入一个数组 立即执行
>> bind， bind(thisScope,arg1,arg2,arg3)   返回一个函数，需要自己执行

```js
add = (a,b) => a+b;
add(1,2)
// 3
```
#### 8.  ES6中的函数解构和数组补漏
- `函数对象解构`
```js
let obj = {
   name:'sxiaobi',
   age: 26
}
function jg({name,age}){
   console.log(name,age)
}
// 'sxiaobi' 26
jg(obj)
```
- `函数数组解构`
```js
let arr = [1,2,3];
function jg(a,b,c){
  console.log(a,b,c)
}
// 1 2 3
jg(...arr)
```
- `in`的用法 判断对象或者数组是否有某个值
```js
let obj = {
   name:'sxiaobi',
   age: 26
}
console.log('name' in obj) 
// true
```
- 数组的遍历方法
- - `forEach`
```js
let arr = ['sxiaobi','男','中国'];
arr.forEach((val,index)=>{
   console.log(index,val)
})
```
- - `map`
```js
let arr = ['sxiaobi','男','中国'];
arr.map((val,index)=>{
   console.log(index,val)
})
```
- - `filter` 数组过滤
- - - 循环
```js
let arr = ['sxiaobi','男','中国'];
arr.filter((val,index)=>{
   console.log(index,val)
})
```
- - - 判断数组是否存在某个值，存在返回当前值，不存在返回空数组
```js
var newarr = [
  { num: 1, val: 'ceshi', flag: 'aa' },
  { num: 2, val: 'ceshi2', flag: 'aa2'  }
]
console.log(newarr.filter(item=>item.num===1))
```
- - - 去除空、undefined、null
```js
var newArr = [1,2,3,4,null,'',undefined,5,6,7,8];
console.log(newArr.filter(item=>item)); // [1, 2, 3, 4, 5, 6, 7, 8]
```
- - - 去除不符合规则的数据
```js
var newArr = [1,2,3,4,5,6];
console.log(newArr.filter(item=>item<4)); // [1,2,3]

```
- - `some`
```js
let arr = ['sxiaobi','男','中国'];
arr.some((val,index)=>{
   console.log(index,val)
})
```
- - `for of`
```js
let arr = ['sxiaobi','男','中国'];
for( let [index,val] of arr.entries()){
   console.log(index,val)
}
```
- - `for in`
```js
let arr = ['sxiaobi','男','中国'];
for( let index in arr){
  console.log(index)
  console.log(arr[index])
}
```
- - `for 循环`
```js
let arr = ['sxiaobi','男','中国'];
for( let i=0;i<arr.length;i++){
  console.log(i)
  console.log(arr[i])
}
```
#### 9. ES6中的对象
- `key`值的使用，用于对象未知键名处理
```js
let keyName = "name";
let obj = {
    [key]:'sxiaobi'
}
console.log(obj)
// { name:'sxiaobi'}
```
- `Object.is()` 对比两个类型
```js
let objOne = {name:'sun'};
let objTwo = {name:'wei'};
console.log(objOne.name===objTwo.name);
console.log(Object.is(objOne.name,objTwo.name))
```
> is 与 === 的区别
> is 是严格比较，===是同值比较
```js
console.log(-0===+0) // true
console.log(Object.is(-0,+0))  // false
console.log(NaN===NaN); // false
console.log(Object.is(NaN,NaN)); // true
```
- `Object.assign(target, …sources) `  target: 目标对象,sources: 源对象。 用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。
```js
var aa = {aa:'sun'};
var bb = {bb:'xiao'};
var cc = {cc:'bi'};
let dd = Object.assign(aa,bb,cc)
console.log(aa) // {aa: "sun", bb: "xiao", cc: "bi"}
console.log(bb) // {bb: "xiao"}
console.log(cc) // {cc: "bi"}
console.log(dd) // {aa: "sun", bb: "xiao", cc: "bi"}
```

### 10. Symbol()
> 基本数据类型：`String`、`Boolean`、`Number`、`undefined`、`null`、`Symbol`
> 引用数据类型：`Object`、`Array`、`Function`
- Symbol的打印
```js
var txt = Symbol('sxiaobi');
console.log(txt);
console.log(txt.toString());
```
> 这时候我们仔细看控制台是有区别的，没有toString的是红字，toString的是黑字。
- Symbol在对象中的应用
```js
var jspang = Symbol();
var obj={
    [jspang]:'sxiaobi'
}
console.log(obj[jspang]);
obj[jspang]='web';
console.log(obj[jspang]);
```
- Symbol对象元素的保护作用
在对象中有很多值，但是循环输出时，并不希望全部输出，那我们就可以使用Symbol进行保护。
没有进行保护的写法：
```js
var obj = {name:'sxiaobi',age:'28',sex:'男'};
for( let item in obj ){
   console.log(obj[item])
}
// sxiaobi  28  男
```
现在我不想别人知道我的年龄，这时候我就可以使用Symbol来进行循环保护。
```js
var obj =  {name:'sxiaobi',sex:'男'};
var age = Symbol();
obj[age] = '28';
for( let item in obj ){
   console.log(obj[item])
}
// sxiaobi  男
```
#### 11. Set和weakSet数据结构
es6新增的数据结构
> 数据结构是计算机存储、组织数据的方式，是相互之间存在一种或多种特定关系的数据元素的集合，包括逻辑结构和物理结构。
> 数据类型是指数据的类型，是一个值的集合和定义在这个值集上的一组操作的总称。

- set 去重，返回一个set对象
```js
let arr = [...new Set([1,2,3,4,1,2,3,4])]
console.log(arr)
// [1,2,3,4]
```
但是不支持重复的object.

- 基本使用
```js
let arr = new Set([1,2,3]);
arr.add(4);
console.log(arr);  // 1,2,3,4
console.log(arr.has(4)); // true
arr.delete(4);
console.log(arr); // 1,2,3
console.log(arr.has(4)); // false
arr.clear();  // undefined
```
- [实际例子](https://blog.csdn.net/u012664198/article/details/97387872)
```js
let myArray=[1,2,2,3,3,4]
            let mySet=new Set(myArray);
            myArray=[...mySet];
            console.log("---数组去重---");
            console.log(myArray);//(4) [1, 2, 3, 4]
            
            let s1=new Set([1,2,3]);
            let s2=new Set([2,3,4,5]);
 
            console.log("---并集---");
            let unionSet=new Set([...s1,...s2]);
            console.log(unionSet);
 
            console.log("---交集---");
            let intersect=new Set([...s1].filter(x=>s2.has(x)));
            console.log(intersect);//Set(2) {2, 3}
 
            console.log("---差集---");
            let difference=new Set([...s1].filter(x=>!s2.has(x)));
            console.log(difference);//Set(1) {1}
```
#### 12. map数据结构
- 基本使用
```js
let mapJg = new Map();
mapJg.set('key','val');
console.log(mapJg) // Map(1) {"key" => "value"}
console.log(mapJg.has('key')) // true
console.log(mapJg.size) // 1
mapJg.delete('key');
console.log(mapJg.has('key')) // false
mapJg.clear();  // undefined
```
- map结构和数组结构的转换
```js
let map = new Map([
  [1, 'one'],
  [2, 'two'],
  [3, 'three'],
])
[...map.keys()]// [1, 2, 3]
[...map.values()]// ['one', 'two', 'three']
[...map.entries()]// [[1,'one'], [2, 'two'], [3, 'three']]
[...map]// [[1,'one'], [2, 'two'], [3, 'three']]
```
- [实际例子](https://www.jianshu.com/p/e6bc5a770b7a)
```js
var errors = new Map([
    [400, 'InvalidParameter'],
    [404, 'Not found'],
    [500, 'InternalError']
]);
for( let [val,index] of errors.entries()){
   console.log(val)
   console.log(index)
}
// 400
// InvalidParameter
// 404
// Not found
// 500
// InternalError
```
