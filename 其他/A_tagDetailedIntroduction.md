a标签详细介绍
---

介绍a标签的以下属性，根据属性展开


----------
### href 
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
	<a href="#" onclick="js_method();">click me</a>
```

#是标签内置的一个方法，代表top的作用。所以用这种方法点击后网页后返回到页面的最顶端。

5. 

``` html
	<a href="#" onclick="js_method();return false;">click me</a>
```
这种方法点击执行了js函数后return false，页面不发生跳转，执行后还是在页面的当前位置。

----------
### download
download 属性是Html5中为 a 标签新添加的属性，用来直接下载文件。

>如果不加download属性，直接链接文件资源，浏览器会直接进行预览。如下代码

``` html
	<a href="15.jpg">点击我查看图片</a>
```
>如果加上download属性，会下载资源，文件名就是download属性值，且浏览器不再预览，如下代码

``` html
	<a href="15.jpg" download="15.jpg">点击我下载图片</a>
```
**注意事项**
1. download属性 Chrome和Firefox支持，IE、Safari、Opera浏览器不支持。
2. 若使用download的属性，则a标签href属性必须链接资源。

----------
### rel
 a 标签的 rel 属性用于指定当前文档与被链接文档的关系。
 > a 标签的rel属性指定源文档到目标文档的关系
 > a 标签的rev属性指定目标文档到源文档的关系
 > rel属性和rev属性可以同时使用，```但HTML5不支持rev```

如下代码：

``` html
	<a href = "15.jpg" rel = "next"  rev = "prev">click me</a>
``` 
``` 浏览器不会以任何方式使用该属性，不过搜索引擎可以利用该属性获得更多有关链接的信息。一般用于SEO```



       



	 
	 

 