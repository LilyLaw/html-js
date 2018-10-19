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