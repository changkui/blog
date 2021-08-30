## BOM

`BOM`既浏览器对象模型(BOM, Browser Object Model)，是使用`JavaScript`开发Web应用程序的核心

在JavaScript高级程序设计一书中主要讲了关于DOM的以下内容

- 理解 `BOM`的核心----window对象

- 控制窗口及其弹窗

- 通过`location`对象获取页面信息

- 使用`navigator`对象了解浏览器

- 通过`history`对象操作浏览器历史

  

#### window对象

`BOM`的核心是`window`对象，表示为浏览器的实例。

`window`在浏览器中有两重身份：

	- `ECMAScript`中的`Global`对象
	- 浏览器窗口的`JavaScript`接口

这就是说网页中所有定义的对象、变量和函数都以`window`作为`Global`对象



##### Global作用域

`window`对象被复用为`ECMAScript`的`Global`对象

通过`var`声明的所有`全局`变量和函数都会变成`window`对象的属性和方法, 自动会成为`window`对象的成员

- 全局变量是`window`对象的属性
- 全局函数是`window`对象的方法

```js
可以理解为var声明的变量
var name = 1;
console.log(name)	// 1 
其实就是自动变成了
window.name = 1;
console.log(name) // 1
```

注意：但是如果使用`let`或`const`替代`var`，则不会把变量添加给全局对象







