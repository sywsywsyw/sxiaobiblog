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

<!-- more -->

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

### 4. 函数

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

### 5. 引用类型 Array String Date RegExp

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

### 6. 面向对象编程
##### 6.1 类
> // TypeScript 是基于类的面向对象的编程语言
> 
类是对象具体事务的一个抽象，对象是类的具体表现。
```js
var testClass = /** @class */ (function () {
    function testClass(name, age) {
        this.name = name;
        this.age = age;
    }
    testClass.prototype.findSister = function () {
        console.log('找到ywf小姐姐');
    };
    return testClass;
}());
var jiejie = new testClass('范冰冰', 18);
console.log(jiejie);
jiejie.findSister();x
// testClass { name: '范冰冰', age: 18 }
// 找到ywf小姐姐
```
我们先用class关键字声明了一个类，并在里边声明了name和age属性。constructor为构造函数。构造函数的主要作用是给类中封装的属性进行赋值。

使用和定义类其实很简单，关键是理解类的思想。要有抽象逻辑的能力，这样才能复用和增强维护性。

##### 6.2 修饰符
* public 默认修饰符 公用修饰符
* protected 受保护的修饰符 可以在本类和子类中使用
* private 私有修饰符 在类内
* readonly 只读修饰符 
```js
class final{
    public sex:string
    protected name:string
    private age:number
    public constrcutor(sex:string,name:string,age:number){
        this.sex = sex;
        this.name = name;
        this.age = age;
    }
    public sayHellow(){
        console.log('小姐姐对你说：你好');
    }

    protected sayLove(){
        console.log('小姐姐对你说：我爱你')
    }
}

let finalStr:final = new final('女','ywf',28);
console.log(finalStr.sex);
console.log(finalStr.name);
console.log(finalStr.age);
finalStr.sayHellow();
finalStr.sayLove();
```
```bash
final.ts:23:32 - error TS2554: Expected 0 arguments, but got 3.
23 let finalStr:final = new final('女','ywf',28);
                                  ~~~~~~~~~~~~
final.ts:25:22 - error TS2445: Property 'name' is protected and only accessible within class 'final' and its subclasses.
25 console.log(finalStr.name);
                        ~~~~
final.ts:26:22 - error TS2341: Property 'age' is private and only accessible within class 'final'.
26 console.log(finalStr.age);
                        ~~~
final.ts:28:10 - error TS2445: Property 'sayLove' is protected and only accessible within class 'final' and its subclasses.
28 finalStr.sayLove();
            ~~~~~~~
```
```js
class Man {
    public readonly sex: string = '男'
}

var man: Man = new Man()
man.sex = '女'
```
```bash
final.ts:36:5 - error TS2540: Cannot assign to 'sex' because it is a read-only property.
36 man.sex = '女'
       ~~~
Found 5 errors.
```
##### 6.3 Class继承和重写
== js继承只支持单重继承 ==
```js
class parentClass{
    public name:string
    public age:number
    public skill:string
    constructor(name: string, age: number,skill:string){
        this.name = name;
        this.age = age;
        this.skill = skill;
    }
    public interest(){
        console.log('父类的方法')
    }
}

let parentObj:parentClass = new parentClass('子小',20,'web');
parentObj.interest();

class childrenClass extends parentClass{
    public childrenName:string;
    public childrenAge:number;
    public childrenSkill:string;
    constructor(childrenName: string, childrenAge: number, childrenSkill:string){
        super('子小', 20, 'web');
        this.childrenName = childrenName;
        this.childrenAge = childrenAge;
        this.childrenSkill = childrenSkill;
    }
    public interest(){
        super.interest();
        console.log('子类从写了父类的方法')
    }
    public loveGril(){
        console.log('子类泡妞')
    }
}
let chilrenObj:childrenClass = new childrenClass('小子',12,'泡妞');
chilrenObj.loveGril();
chilrenObj.interest();
// 父类的方法
// 子类泡妞
// 父类的方法
// 子类从写了父类的方法
```
##### 6.4 接口 interface
* 定义接口
```js
interface GirlRequest{
    sex:string
    skill:string
}
let myGirl:GirlRequest = {sex:'女',skill:'爱我'};
console.log(myGirl);
// { sex: '女', skill: '爱我' }
```
* 可选参数的接口
```js
interface GirlRequest{
    sex:string
    skill:string
    beautiful?:boolean  // 可选参数
}
```
* 规范函数类型的接口
```js
interface SearchMan{
    (source:string,subString:string):boolean
}
let mySearch: SearchMan = function (source: string, subString: string): boolean{
    let flag = source.search(subString);
    return flag != -1;
}
console.log(mySearch('高、富、帅、德', '胖'))
// false
```
##### 6.5 命名空间 namespace
在制作大型应用的时候，为了让程序更加有层次感和变量之间不互相干扰，我们可以使用命名空间来构建程序。举个小例子：比如“德华”这件事，帅哥也有叫德华的，二师兄也有叫德华的。那我们要如何区分那。这对于女孩子选老公来说非常重要啊。
当然命名空间就是解决这个问题的，命名空间，又称内部模块，被用于组织有些具有内在联系的特性和对象。我们来看一个例子：
```js
namespace shuaiGe{
    export class Dehua{
        public name:string = '刘德华'
        talk(){
            console.log('我是帅哥刘德华')
        }
    }
}

namespace bajie{
    export class Dehua{
        public name:string = '马德华'
        talk(){
            console.log('我是二师兄马德华')
        }
    }
}

let dehua1:shuaiGe.Dehua   = new shuaiGe.Dehua()
let dehua2:shuaiGe.Dehua   = new bajie.Dehua()
dehua1.talk()
dehua2.talk()
// 我是帅哥刘德华
// 我是二师兄马德华
```
通过命名空间我们很好的把程序变的清晰了，各位小姐姐也再也不会刘德华和马德华傻傻分不清了。