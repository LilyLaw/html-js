## HTML DOM Event 对象

> Event对象代表事件的状态，比如事件在其中发生的元素，键盘按键的状态，鼠标的位置，鼠标按钮的状态。
> **事件通常与函数结合使用，函数不会在事件发生前被执行。**

### 事件句柄（Event Handlers）

 - onabort 图像的加载被中断
``` html
	<img src="https://github.com/LilyLaw/html_js_training/blob/master/img/15.jpg?raw=true" onabort="abortImage()" />
    <script type="text/javascript">
        function abortImage() {
            alert('Error: Loading of the image was aborted')
        }
    </script>
```
 - onblur 元素失去焦点
	 支持该事件的html标签有如下
	>  ```<a>```, ```<acronym>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>,``` 
```<button>```, ```<caption>```, ```<cite>```, ```<dd>```, ```<del>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>,``` 
```<em>```, ```<fieldset>```, ```<form>```, ```<frame>```, ```<frameset>```, ```<h1> t```o ```<h6>```, ```<hr>```, ```<i>,``` 
```<iframe>```, ```<img>```, ```<input>```, ```<ins>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>,``` 
```<object>```, ```<ol>```, ```<p>```, ```<pre>```, ```<q>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>,``` 
```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>,``` 
```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```

	支持该事件的 JavaScript 对象：
	> button, checkbox, fileUpload, layer, frame, password, 
radio, reset, submit, text, textarea, window

 - onchange 事件会在域的内容改变时发生。
	 支持该事件的 HTML 标签：
	 > ```<input type="text">```, ```<select>```, ```<textarea>```
	 
	 支持该事件的 JavaScript 对象：
	 > fileUpload, select, text, textarea
	 
	 代码实例：
``` html
	<input type="text" onchange="logme(event);">
    <script type="text/javascript">
        function logme(event) {
            console.log(event.target.value);
        }
    </script>
```
**注意**  onchange 在属性值改变，```且失去焦点```的时候才可以激活。

 - onclick 单击
	 onclick 事件是在同一元素上发生```鼠标按下和鼠标松开```的时候才发生。
	 
 - ondblclick 双击
	 双击后才发生。
	 
	 代码实例：
``` html
	<input type="text" ondblclick="logme(event);">
    <script type="text/javascript">
        function logme(event) {
            console.log(event.target.value);
        }
    </script>
```

 - onerror 在加载文档或图像时发生错误
	 支持该事件的html标签：
	>  ```<img>```，```<object>```，```<style>```
	 
	 支持该事件的JavaScript对象：
	 > window, image
``` html
	<img src="sdfjsdfjsdf.jpg" alt="" onerror="logerror();">
    <script>
        function logerror(){
            console.log("I can't find the image");
        }
    </script>
```

 - onfocus 元素获得焦点
	 支持该事件的html标签：
	 > ```<a>```，```<acronym>```，```<address>```，```<area>```，```<b>```，```<bdo>```，```<big>```，```<blockquote>```，```<button>,``` 
```<caption>```，```<cite>```，```<dd>```，```<del>```，```<dfn>```，```<div>```，```<dl>```，```<dt>```，```<em>```，```<fieldset>,``` 
```<form>```，```<frame>```，```<frameset>```，```<h1> t```o ```<h6>```，```<hr>```，```<i>```，```<iframe>```，```<img>```，```<input>,``` 
```<ins>```，```<kbd>```，```<label>```，```<legend>```，```<li>```，```<object>```，```<ol>```，```<p>```，```<pre>```，```<q>,``` 
```<samp>```，```<select>```，```<small>```，```<span>```，```<strong>```，```<sub>```，```<sup>```，```<table>```，```<tbody>,``` 
```<td>```，```<textarea>```，```<tfoot>```，```<th>```，```<thead>```，```<tr>```，```<tt>```，```<ul>```，```<var>```
	
	支持该事件的JavaScript对象
	> button, checkbox, fileUpload, layer, frame, password, radio, reset, select, submit, text, textarea, window

 - onkeydown 某个键盘按键被按下
	 
	 支持该事件的html标签：
	 > ```<a>```， ```<acronym>```， ```<address>```， ```<area>```， ```<b>```， ```<bdo>```， ```<big>```， ```<blockquote>```， ```<body>```，```<button>```， ```<caption>```， ```<cite>```， ```<code>```， ```<dd>```， ```<del>```， ```<dfn>```， ```<div>```， ```<dt>```， ```<em>```，```<fieldset>```， ```<form>```， ```<h1>```  to  ```<h6>```， ```<hr>```， ```<i>```， ```<input>```，```<kbd>```， ```<label>```， ```<legend>```，```<li>```， ```<map>```， ```<object>```， ```<ol>```， ```<p>```，```<pre>```，```<q>```， ```<samp>```， ```<select>```， ```<small>```，```<span>```， ```<strong>```， ```<sub>```，```<sup>```， ```<table>```， ```<tbody>```，```<td>```，```<textarea>```，```<tfoot>```，```<th>```，```<thead>```，```<tr>```，```<tt>```，```<ul>```，```<var>```
	 
	 支持该事件的JavaScript对象：
	 > document, image, link, textarea
	 
	 代码实例：
``` html
	<input type="text" onkeydown="loginfo(event)">
    <script>
        function loginfo(e){
           console.log(e);
        }
    </script>
```
 - onkeypress 某个键盘按键被按下并松开
	支持该事件的html标签：
	> ```<a>```, ```<acronym>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<del>```, ```<dfn>```, ```<div>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<map>```, ```<object>```, ```<ol>```, ```<p>```, ```<pre>```, ```<q>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```

	支持该事件的JavaScript对象：
	> document, image, link, textarea
	
	代码实例：
``` html
	<input type="text" onkeypress="loginfo(event)">
    <script>
        function loginfo(e){
           console.log(e);
        }
    </script>
```

 - onkeyup 某个键盘按键被松开
	 
	 支持该事件的html标签:
	 > ```<a>```, ```<acronym>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```,```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<del>```, ```<dfn>```, ```<div>```, ```<dt>```, ```<em>```,```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```,```<li>```, ```<map>```, ```<object>```, ```<ol>```, ```<p>```, ```<pre>```, ```<q>```, ```<samp>```, ```<select>```, ```<small>```,```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```,```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```
	 
	 支持该事件的JavaScript对象：
	 > document, image, link, textarea
	 
	 代码实例：
``` html
	<input type="text" onkeyup="loginfo(event)">
    <script>
        function loginfo(e){
           console.log(e);
        }
    </script>
```

 - onload 一张页面或一幅图像加载完成
	
	支持该事件的html标签：
	> ```<body>```，```<frame>```，```<frameset>```，```<iframe>```，```<img>```，```<link>```，```<script>```
	
	支持该事件的JavaScript对象：
	> image, layer, window

	代码实例：
``` html
	<html>
	<head>
		<title></title>
	</head>
	<body>
		<img src="15.jpg" alt="" onload="loginfo(event);">
		<script>
			function loginfo(e){
			   console.log("图片加载完成");
			}

			window.onload=function(){
				console.log("页面加载完成");
			}
		</script>
	</body>
	</html>
```

 - onmousedown 鼠标按钮被按下
	
	支持该事件的html标签：
	> ```<a>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<map>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```
	
	支持该事件的JavaScript对象：
	> button, document, link
	
	代码实例：
``` html
	<img src="15.jpg" alt="" onmousedown="loginfo(event);">
    <script>
        function loginfo(e){
           console.log("图片加载完成");
        }
    </script>
```
   **注意** 鼠标左右键点击都可以触发此事件
   
 - onmouseup 鼠标按键被松开
	
	支持该事件的html标签：
	> ```<a>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<map>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```
	
	支持该事件的JavaScript对象：
	> button, document, link
	
	代码实例：
```html
	<img src="15.jpg" alt="" onmouseup="loginfo(event);">
    <script>
        function loginfo(e){
           console.log("图片加载完成");
        }
    </script>
```

 - onmousemove 鼠标被移动
	 事件在鼠标指针移动时发生
	 
	 支持该事件的html标签：
	 > ```<a>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```,```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```,```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```,```<li>```, ```<map>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```,```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```,```<tr>```, ```<tt>```, ```<ul>```, ```<var>```

	支持该事件的JavaScript对象：
	> 默认情况下，onmousemove不是任何对象的事件，
因为鼠标移动非常频繁。
   
   代码实例：
``` html
	<img src="15.jpg" alt="" onmousemove="loginfo(event);">
    <script>
        function loginfo(e){
           console.log("图片加载完成");
        }
    </script>
```

   **注意：**每当用户鼠标移动一个像素就会发生一个mousemove事件，这会耗费系统资源去处理所有这些mousemove事件，因此应谨慎地使用该事件。
   
 - onmouseout 鼠标指针从元素上移开
	
	支持该事件的html标签：
	> ```<a>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<map>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```

	支持该事件的JavaScript对象：
	> layer，link
	
	代码实例：
``` html
	<img src="15.jpg" alt="" onmouseout="loginfo(event);" style="width:400px;height:auto;">
    <script>
        function loginfo(e){
           console.log("图片加载完成");
        }
    </script>
```

 - onmouseover 鼠标移到某元素之上
	
	支持该事件的html 标签：
	>  ```<a>```, ```<address>```, ```<area>```, ```<b>```, ```<bdo>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<caption>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<map>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<tbody>```, ```<td>```, ```<textarea>```, ```<tfoot>```, ```<th>```, ```<thead>```, ```<tr>```, ```<tt>```, ```<ul>```, ```<var>```
	
	支持该事件的JavaScript对象：
	> layer, link
	
	代码实例：
``` html
	<img src="15.jpg" alt="" onmouseover="loginfo(event);" style="width:400px;height:auto;">
    <script>
        function loginfo(e){
           console.log("图片加载完成");
        }
    </script>
```

 - onreset	重置按钮被点击
	
	支持该事件的html标签：
	> ```<form>```
	
	支持该事件的JavaScript对象：
	> form

	代码实例：
``` html
	<form action="" onreset="resetform(event);">
        姓名：<input type="text" name="name" value="LilyLaw">
        性别：<input type="radio" name="sex" checked="checked" value="female"> female <br/>
        <input type="radio" name="sex" value="male"> 
        <input type="reset" value="reset">
    </form>
    <script>
        function resetform(e){
            console.log("this form will be reset");
        }
    </script>
```

 - onresize 窗口或框架重新被调整大小
	
	支持该事件的html标签：
	> ```<a>```, ```<address>```, ```<b>```, ```<big>```, ```<blockquote>```, ```<body>```, ```<button>```, ```<cite>```, ```<code>```, ```<dd>```, ```<dfn>```, ```<div>```, ```<dl>```, ```<dt>```, ```<em>```, ```<fieldset>```, ```<form>```, ```<frame>```, ```<h1>``` to ```<h6>```, ```<hr>```, ```<i>```, ```<img>```, ```<input>```, ```<kbd>```, ```<label>```, ```<legend>```, ```<li>```, ```<object>```, ```<ol>```, ```<p>```, ```<pre>```, ```<samp>```, ```<select>```, ```<small>```, ```<span>```, ```<strong>```, ```<sub>```, ```<sup>```, ```<table>```, ```<textarea>```, ```<tt>```, ```<ul>```, ```<var>```

	支持该事件的JavaScript对象：
	> window

	代码实例：
``` html
	<div onresize="divresize(event)">sdfsdfsdfsdfs</div>
    <script>
        function divresize(){
            console.log("divresize");
        }
        window.onresize = function(){
            console.log("windowresize");
        }
    </script>
```

 - onselect 文本被选中

	支持该事件的html标签：
	> ```<input type="text">```, ```<textarea>```

	支持该事件的JavaScript对象：
	> window

	**注意** 我目前没找到获取选中内容的方法
	
 - onsubmit 确认按钮被点击
 
	 支持该事件的html标签:
	 > ```<form>```

	支持该事件的JavaScript对象：
	> form	

	``` html
		<form action="######" method="get" name="myform" onsubmit="return submitform(event);">
			<input type="text" name="name">
			<input type="text" name="sex">
			<input type="text" name="age">

			<input type="submit" value="submit">
		</form>

		<script>
			function submitform(e){
				console.log(e);
				return false;
			}
		</script>
	```
	
 - onunload 用户退出页面
	
	支持该事件的html标签：
	> ```<body>```，```<frameset>```

	支持该事件的JavaScript对象：
	> window

	代码实例：
	IE下起作用，其他不管用
``` html
	<body onbeforeunload = "return 'are you sure to close this tab???';">
	</body>
```

   **注意** Chrome，Firefox 试了很多种方法都不管用，心累，日他妈的，记得把这个问题解决哦！！！
   
   踩坑指路  ----->   [unload 踩坑](https://github.com/LilyLaw/html_js_training/blob/master/%E5%85%B6%E4%BB%96/%E6%88%91%E8%B8%A9%E8%BF%87%E7%9A%84%E5%9D%91/unload.md)

----------

### 
