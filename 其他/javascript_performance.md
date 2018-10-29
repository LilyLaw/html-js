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

#### JavaScript作用域。

   页面加载时，JavaScript引擎会创建一个全局的执行环境，所有全局变量和函数都作为window对象的属性和方法来创建。之后每执行一个函数，JavaScript引擎都会创建一个对应的执行环境，并将该环境放入环境栈中，所以当前正在执行函数的执行环境是在环境栈的最顶部的，当函数执行完毕后，其执行环境会弹出栈，并被销毁，保存在其中的变量和函数定义也会销毁。

   当代码在一个执行环境中执行时，JavaScript引擎会创建变量对象的`作用域链` ，它可以保证对执行环境有权访问的变量和函数的有序访问。当需要查找某个变量或函数时，JavaScript引擎会通过执行环境的作用域链来查找变量和函数，从作用域链的顶端开始，如果没有找到，则向下寻找直到找到为止。若一直到全局作用域都没有找到，则该变量或函数为undefined。
   
   1.  使用局部变量

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

   这样写的好处：（1）window和undefined都是为了减少变量查找所经过的作用域。当window传递给闭包内部后，在闭包内部使用时会把它当成一个局部变量，显然比原先的查找模式要快些，因为原先在最外层；（2）undefined是JavaScript的全局属性。将undefined做为参数传递给闭包，因为没有给它传值，它的值就是undefined，这样闭包内部在使用它的时候就可以把它当做局部变量使用，从而提高查找速度。**严格意义上来说，undefined不是关键字，而是JavaScript预定义的全局变量**  （3）undefined在某些低版本的浏览器（如IE8、IE7）中值是可以被修改的（在ECMAScript3中，undefined是可读/写变量，可以给它赋任意值，这个错误在ECMAScript5中做了修正）将undefined作为参数并且不给它传值可以防止因undefined值被修改而造成的错误。

   2. 避免增长作用域链
   	在JavaScript中有两种语句可以临时增加作用域链。```with```、```try-catch```。
	
	   with可以使对象的属性像全局变量来使用。实际上是将一个新的变量对象添加到执行环境作用域的最外层，这个变量对象包含了指定对象的所有属性，因此可以直接访问。看似方便却增长了作用域链，需要多查找几层才能找到，因此不推荐使用。
	[with 详解](https://github.com/LilyLaw/html_js_training/blob/master/%E4%BD%9C%E7%94%A8%E5%9F%9F/with.html) 
	
      try-catch中的catch从句和with类似，也是在作用域链的顶端增加了一个对象，该对象包含了由catch指定命名的异常对象。但是因为catch语句只有在发生错误时才执行，因此影响比较少。[try-catch详解](https://github.com/LilyLaw/html_js_training/blob/master/%E4%BD%9C%E7%94%A8%E5%9F%9F/try_catch.html)
	  
----------

#### 其他优化方式
	
   
	
