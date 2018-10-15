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

----------
### target
a 标签的 target 属性规定在何处打开链接文档。

>当用户第一次选择内容列表中的某个链接时，浏览器将打开一个新的窗口，将它标记为 "view_window"，然后在其中显示希望显示的文档内容。如果用户从这个内容列表中选择另一个链接，且这个 "view_window" 仍处于打开状态，浏览器就会再次将选定的文档载入那个窗口，取代刚才的那些文档。

``` html
	<a href = "15.jpg" target="view_window">click me</a>
	<a href = "1.jpg" target="view_window">click me</a>
	<a href = "2.jpg" target="view_window">click me</a>
	<a href = "3.jpg" target="view_window">click me</a>
```
有 4 个保留的目标名称用作特殊的文档重定向操作：

####  target="_blank"

浏览器总在一个新打开、未命名的窗口载入目标文档。

#### target="_self"

这个目标的值对所有没有指定目标的 a 标签是默认目标，它使得目标文档载入并显示在相同的框架或者窗口中作为源文档。这个目标是多余且不必要的，除非和文档标题 <base> 标签中的 target 属性一起使用。

#### target="_parent"
	
这个目标使得文档载入父窗口或者包含来来超链接引用的框架的框架集。如果这个引用是在窗口或者在顶级框架中，那么它与目标 _self 等效。

*注意事项*
去掌握框架。

#### target="_top"

这个目标使得文档载入包含这个超链接的窗口，用_top目标将会清除所有被包含的框架并将文档载入整个浏览器窗口。


**注意事项**
target 属性的4个属性值都以下划线开头，任何其他用一个下划线开头的窗口或目标都会被浏览器忽略。因此不要将下划线作为文档中定义的任何框架的name或id的第一个字符。




	 
	 

 