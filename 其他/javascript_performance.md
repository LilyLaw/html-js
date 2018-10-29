## JavaScript 性能优化

在编写js代码的时，当一个页面交互较多，网页需要运行很久，展示给用户的是有很长事件页面一片空白。
其次，当工作要求需要在页面引入大量插件，同样会出现大量空白时段。
这样的交互很不友好，怎么解决呢？

最根本原因还是js代码加载时段以及代码自身优化。

总结一下优化的方法：

###  js代码加载位置

   js代码最好放在 ```</body>```之前
	因为浏览器解析html是自上至下解析的。如果刚在```<head></head>```标签内部，则 ```<body></body>``` 里面的内容还没有被解析，浏览器呈现的就全是空白。
	
----------

### 代码层面优化

#### 从JavaScript作用域谈起。

   页面加载时，JavaScript引擎会创建一个全局的执行环境，所有全局变量和函数都作为window对象的属性和方法来创建。之后每执行一个函数，JavaScript引擎都会创建一个对应的执行环境，并将该环境放入环境栈中，所以当前正在执行函数的执行环境是在环境栈的最顶部的，当函数执行完毕后，其执行环境会弹出栈，并被销毁，保存在其中的变量和函数定义也会销毁。

   当代码在一个执行环境中执行时，JavaScript引擎会创建变量对象的`作用域链` ，它可以保证对执行环境有权访问的变量和函数的有序访问。当需要查找某个变量或函数时，JavaScript引擎会通过执行环境的作用域链来查找变量和函数，从作用域链的顶端开始，如果没有找到，则向下寻找直到找到为止。若一直到全局作用域都没有找到，则该变量或函数为undefined。
   
   - 使用局部变量

		从上面我们知道查找变量的时候回一层一层去找直到找到最顶层，层数越多，查找事件越长。所以应尽可能的使用局部变量
	如下代码：
	
   ``` javascript
	function createEle(){
		var ele = document.createElement("div");
	}

	function createEle2(){
		var doc = document;
		var ele = doc.createElement("div");
	}
   ```
	
   当document使用次数比较少的时候，用createEle()的方法写没什么影响，但如果是一个大循环里面多次调用document对象，最好将document赋值给局部变量。
   
   来看下jquery:
   ``` javascript
   (function(window,undefined){
   		var jQuery = function(){}
		//...
		window.jQuery = window.$ = jQuery;
   })(window);
   ```
	
