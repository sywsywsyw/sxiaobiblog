---
title: 以更高的速度和效率调试JavaScript
date: 2017-11-08 00:55:50
tags:
categories: JS
---
------

<!-- more -->


# 转载

项目地址: [https://blog.fundebug.com/2017/11/08/14-javascript-debugging-tips/)
项目地址: [https://raygun.com/javascript-debugging-tips)


了解你的工具的时候，做事情有显著差异。尽管JavaScript的声誉作为调试困难，如果你把一些你的袖子的错误和缺陷需要解决的时间少。

**我们列出了14个调试技巧，你可能不知道**，但要记住下一次你发现自己需要调试你的JavaScript代码！

<u>**让我们开始吧**</u>

大多数这些提示是Chrome和Firefox的督察，虽然许多还将与其他人员的工作。

## 1。“调试器；”

console.log”后，调试器；&#39;是我最喜欢的快速和肮脏的调试工具。一旦你的代码，浏览器会自动停止执行时。你甚至可以把它包在条件句，所以它只会在你需要它。

if (thisThing) {
    debugger;
}
## 2。显示对象表

有时候，你有一套复杂的对象，你想看。你可以console.log和滚动列表，或打破console.table帮手。使得它更容易看到你在做什么！

var animals = [
    { animal: 'Horse', name: 'Henry', age: 43 },
    { animal: 'Dog', name: 'Fred', age: 13 },
    { animal: 'Cat', name: 'Frodo', age: 18 }
]; console.table(animals);

将输出：

[![Screenshot showing the resulting table for JavaScript debugging tip 2 ](https://raygun.com/upload/Debugging%202b.png)](https://raygun.com/upload/Debugging%202b.png)

## 三.尝试所有的尺寸

在每一个移动设备在你的桌子上会很棒的，在现实世界中是不可行的。如何调整你的视图来代替呢？Chrome提供了你所需要的一切。跳进你的检验员和点击**“模式”切换装置**按钮看你的媒体查询来生活！

[![](https://raygun.com/upload/Debugging%201%20.png)](https://raygun.com/upload/Debugging%201%20.png)

## 4。如何快速找到你的DOM元素

马克在元素面板一个DOM元素和使用它在您的控制台。铬检查员保持最后的五个元素在其历史上，最终的标记元素显示为0美元，第二个标记元1美元等。

如果你标记以下为“item-4′项目，“item-3 &#39;、&#39; ITEM-2 &#39;，&#39; item-1 &#39;，&#39; item-0 &#39;然后你可以访问DOM节点这样的控制台：

[![](https://raygun.com/upload/Debugging%202.png)](https://raygun.com/upload/Debugging%202.png)

## 5。基准循环使用控制台。time() timeend()和控制台。

它可以是超级有用，知道长的东西已经执行，尤其是当调试慢回路。你甚至可以设置多个定时器的方法分配一个标签。让我们看看它是如何工作的：

console.time('Timer1');

var items = [];

for(var i = 0; i < 100000; i++){ items.push({index: i});
} console.timeEnd('Timer1');

这就产生了以下结果：

[![](https://raygun.com/upload/Debugging%203.png)](https://raygun.com/upload/Debugging%203.png)

## 6。得到一个函数的堆栈跟踪

你可能知道的JavaScript框架，产生大量的代码–快。

它创建视图和触发器的事件，所以你会想知道是什么引起的函数调用。

由于JavaScript不是一个结构化语言，它有时是很难得到的概述**什么**发生**什么时候**。这是当console.trace（或只是微量的控制台）来方便，能够调试JavaScript。

想象你想看到的函数调用funcz在汽车实例33线整个堆栈跟踪：

var car;
var func1 = function() { func2();
}

var func2 = function() { func4();
}
var func3 = function() {
}

var func4 = function() { car = new Car(); car.funcX();
}
var Car = function() {
	this.brand = ‘volvo’;
	this.color = ‘red’;
	this.funcX = function() {
		this.funcY();
	}

	this.funcY = function() {
		this.funcZ();
	}

	this.funcZ = function() { console.trace(‘trace car’)
	}
} func1();
var car;
var func1 = function() { func2();
}
var func2 = function() { func4();
}
var func3 = function() {
}
var func4 = function() { car = new Car(); car.funcX();
}
var Car = function() {
	this.brand = ‘volvo’;
	this.color = ‘red’;
	this.funcX = function() {
		this.funcY();
	}
	this.funcY = function() {
		this.funcZ();
	}
 	this.funcZ = function() { console.trace(‘trace car’)
	}
} func1();

将输出线：33

[![](https://raygun.com/upload/Debugging%204.png)](https://raygun.com/upload/Debugging%204.png)

现在我们可以看到，**func1**打电话**还是一样的，**这被称为**func4****func4**然后创建一个实例**车**然后调用的函数**car.funcx**，等等

即使你认为你很了解你的脚本可以很方便的。比方说，你想提高你的代码。让你的大所有相关功能列表的痕迹。每一个人都是可点击的，你现在可以去它们之间来回。它就像一个菜单只为你。

## 7。unminify调试JavaScript代码是一个简单的方法

有时你可能在生产上有问题，和你的源地图没能到服务器。**不要害怕**。铬可以unminify JavaScript文件更可读的格式。代码不会为你真正的代码–有用，但至少你可以看到发生了什么。单击{ }很打印按钮下面的检查源代码查看器。

[![](https://raygun.com/upload/Debugging%205.png)](https://raygun.com/upload/Debugging%205.png)

## 8。快速查找功能调试

比方说，你想在一个函数中设置断点。

最常见的两种方式就是：

**1。找到你的线和添加断点检验
2。添加在你的脚本调试器**

在这些解决方案，你必须点击在你的文件中找到你想调试一行

什么可能是不太常见的是使用控制台。使用调试（funcname）在控制台和脚本将停止它达到的功能时，你通过了。

很快，但缺点是它不在私人或匿名函数的工作。但如果不是这样的话，很可能找到一个功能调试的最快方式。（注：有一个功能叫做console.debug这不是一回事。）

var func1 = function() { func2();
};

var Car = function() {
	this.funcX = function() {
		this.funcY();
	}

	this.funcY = function() {
		this.funcZ();
	}
}

var car = new Car();

型调试（汽车节）在控制台和脚本将停止在调试模式时，它会调用一个函数来car.funcy：

[![](https://raygun.com/upload/Debugging%206.png)](https://raygun.com/upload/Debugging%206.png)

## 9。黑盒子脚本不相关

今天我们经常有几个库和框架在Web应用程序。他们中的大多数都是测试和相对无缺陷。但是，调试器仍然进入了所有的文件，有没有相关的调试任务。解决的办法是黑盒子，你不该脚本需要调试。这也包括你自己的脚本。[阅读更多关于本文调试黑盒。](https://raygun.com/blog/javascript-debugging-with-black-box/)

## 10。在调试复杂找到重要的东西

在更复杂的调试，我们有时想输出多行。你能做的一件事保持较好的结构你的输出是使用更多的控制台的功能，例如，console.log，console.debug，console.warn，console.info，console.error等等。然后你可以过滤你的检查员。但有时这真的不是你想要的东西的时候，你需要调试JavaScript。现在，你可以得到创意和风格你的消息。使用CSS和使你自己的结构化控制台消息当你想调试JavaScript：

console.todo = function(msg) { console.log(‘ % c % s % s % s‘, ‘color: yellow; background - color: black;’, ‘–‘, msg, ‘–‘);
} console.important = function(msg) { console.log(‘ % c % s % s % s’, ‘color: brown; font - weight: bold; text - decoration: underline;’, ‘–‘, msg, ‘–‘);
} console.todo(“This is something that’ s need to be fixed”); console.important(‘This is an important message’);

将输出：

[![](https://raygun.com/upload/Debugging%207.png)](https://raygun.com/upload/Debugging%207.png)

**例如：**

在控制台。log()可以设置%s字符串，整数和% %我C自定义风格。你或许能找到更好的方法来使用这。如果你使用一个单一的网页框架，你也许想要查看消息和另一个模型，集合的一种类型，控制器等。也许也叫短像wlog，堵塞和MLOG运用你的想象力！

## 11。看具体的函数调用和参数

在Chrome的控制台，你可以监视特定的功能。每次调用函数时，它将是传入的值记录。

var func1 = function(x, y, z) {
//....
};

将输出：

[![](https://raygun.com/upload/Debugging%208.png)](https://raygun.com/upload/Debugging%208.png)

这是一个伟大的方式，看看哪个参数传递给函数。但我要说它会好的如果控制台可以告诉多少参数的期望。在上面的例子中，func1期望3个参数，但只有2是通过。如果不是在处理代码可能会导致一个可能的错误。

## 12。快速访问控制台中的元素

一个更快的方式在控制台做queryselector与美元符号。$（&#39;css-selector”）将返回第一个匹配的CSS选择器。$（&#39;css-selector”）将返回所有的人。如果您使用的是一元一次以上，值得保存为一个变量。

[![](https://raygun.com/upload/Debugging%2010.png)](https://raygun.com/upload/Debugging%2010.png)

## 13。邮递员是伟大的（但火狐更快）

许多开发商利用邮递员玩Ajax请求。邮递员是优秀的，但它可以打开一个新的浏览器窗口有点烦人，写新的请求对象，然后测试他们。

有时很容易使用你的浏览器。

当你这样做时，你不再需要担心身份验证Cookie如果您发送一个密码安全的网页。这是你如何将编辑和发送请求在Firefox。

打开检查员去网络标签。右键单击所需的请求并选择编辑和发送。现在你可以改变任何你想要的。更改标题和编辑你的参数和打重发。

下面我提出一个请求，两次不同性质：

![When debugging JavaScript, Chrome lets you pause when a DOM element changes](https://raygun.com/upload/Debugging%2011.png)

## 14。突破节点上的变化

DOM是一件有趣的事。有时事情的变化，你不知道为什么。然而，当你需要调试JavaScript，浏览器可以让你暂停的时候，一个DOM元素的变化。你甚至可以监测它的属性。在Chrome的督察，右键单击元件选择打破设置使用：

[![](https://raygun.com/upload/Debugging%2014.png)](https://raygun.com/upload/Debugging%2014.png)
