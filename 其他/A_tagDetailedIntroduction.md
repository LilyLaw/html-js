a标签详细介绍
---

介绍a标签的以下属性，根据属性展开

### href 
----------------------------------------------------------------------
>href属性值可以是任何有效文档的相对或绝对URL，包括片段标识符和JavaScript代码段。

下面介绍href的常见用法

 

  #### href = "#"
	 表示回到顶部，如果当前页面需要滚动，可以通过此种方式简单实现。	 
``` html
<div>
	<a href="#">点击我回到顶部</a>
</div>
```

#### href="URL"
 1. 绝对URL
	 可以指向另一个站点如 href="http://www.baidu.com", 点击时会直接跳到改页面。
 2. 相对URL
	 指向站点内的某个链接，如 href = "index.html"。 
 3. 锚URL
	 此时指向页面中的锚，比如href="#top"，那么点击时就会跳转到当前页面id=“top”这个锚点。
	 
#### 调用js代码  
 1.
``` html
	<a href="javascript:js_method();">click me</a>
```
这种方法在传递this等参数的时候很容易出问题，而且javascript:协议作为a的href属性值时不仅会导致不必要的触发window.onbeforeunload事件，在IE里面更会使gif动画图片停止播放，***W3C标准不推荐在href里面执行JavaScript语句*** 。

2. 

``` html
	<a href="javascript:void(0)" onclick="js_method();">click me</a>
```
这是最常用的方法，也是最周全的方法，onclick方法负责执行js函数，而void是一个操作符，void(0)返回undefined，地址不发生跳转。而且这种方法不会像第一种方法一样直接将js方法暴露在浏览器的状态栏。

3. 

``` html
	<a href="javascript:;" onclick="js_method();">click me</a>
```
这种方法跟跟2种类似，区别只是执行了一条空的js代码。 ***推荐使用***

4. 

``` html
	<a href="#" onclick="js_method();"></a>
```

#是标签内置的一个方法，代表top的作用。所以用这种方法点击后网页后返回到页面的最顶端。

5. 

``` html
	<a href="#" onclick="js_method();return false;"></a>
```
这种方法点击执行了js函数后return false，页面不发生跳转，执行后还是在页面的当前位置。



       



	 
	 

 