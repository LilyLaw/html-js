## Html5 拖放（Drag和Drop）详解

HTML5中规定元素可拖动。
可拖动的元素必须设置属性draggable为true
``` html
	<p draggable="true" ondragstart="dragbegin();">拖动我</p>
```
**注意** 链接和图片默认是可以拖动的，不需要draggable属性。

在拖放过程中会触发的事件：
1. 在拖动目标上触发的事件
 - ondragstart 用户开始拖动元素时触发。
 - ondrag 元素正在拖动时触发。
 - ondragend 用户完成元素拖动后触发。
 
 2. 释放目标时触发的事件：
 - ondragenter 当被鼠标拖动的对象进入其将要放置容器范围内时触发此事件。
 - ondragover 当被鼠标拖动的对象另一容器范围内拖动时触发此事件。
 - ondragleave 当被鼠标拖动的对象离开一个将要放置容器范围时触发此事件。
 - ondrop 当被鼠标拖动的对象放置到目标容器时触发此事件。
 
 代码实例
``` html
	<!DOCTYPE html>
	<html>
	<head>
		<title>HTML5拖拽</title>
		<meta charset="utf-8">
		<style>
			#div1,#div2 {
				width: 300px;
				height: 150px;
				padding: 10px;
				border: 1px solid #aaaaaa;
				margin-bottom: 20px;
			}
		</style>
	</head>
	<body>
		<p>拖动img_w3slogo.gif图片到矩形框中:</p>
		<div id="div1" ondrop="drop(event)" ondragover="allowDrop(event)">div1</div>
		<div id="div2" ondrop="drop(event)" ondragover="allowDrop(event)">div2</div>
		<img id="drag1" src="15.jpg" draggable="true" ondragstart="drag(event)" style="width:200px;height:auto;">
		<script>
			function allowDrop(ev) {
				ev.preventDefault();
			}

			function drag(ev) {
				ev.dataTransfer.setData("Text", ev.target.id);
			}

			function drop(ev) {
				ev.preventDefault();
				var data = ev.dataTransfer.getData("Text");
				ev.target.appendChild(document.getElementById(data));
			}
		</script>
	</body>
	</html>
```

分析代码：
1. 为了使元素可以拖拽，必须把元素的draggable属性设置为true
``` html
	<img draggable="true" />
```
**但注意**  HTML5中链接和图像**默认**是可拖动的。所以可以不设置:draggable="true"
所以上面的对图像处理的代码可以这样写：
``` html
	<img id="drag1" src="15.jpg" ondragstart="drag(event)" style="width:200px;height:auto;">
``` 
2. 开始拖动
	当开始拖动时，触发ondragstart事件，调用drag()，它规定了被拖动的数据。[dataTransfer](https://github.com/LilyLaw/html_js_training/blob/master/%E5%85%B6%E4%BB%96/dataTransfer.md).serData()方法设置被拖数据的数据类型和值。
``` javascript
	function drag(ev) {
		ev.dataTransfer.setData("Text", ev.target.id);
	}
```
> 在这个例子中，数据类型是 "Text"，值是可拖动元素的 id ("drag1")。

3. 放置
	ondragover规定在何处放置被拖动的数据。
	默认无法将数据或元素放到其他元素中，如果需要设置允许放置，必须阻止对元素的默认处理方式。
``` javascript
	event.preventDefault();
```
当放置被拖动数据时，会发生drop事件。
``` javascript
	function drop(ev) {
		ev.preventDefault();
		var data = ev.dataTransfer.getData("Text");
		ev.target.appendChild(document.getElementById(data));
	}
```
> 调用 preventDefault() 来避免浏览器对数据的默认处理（drop 事件的默认行为是以链接形式打开）
> 通过dataTransfer.getData("Text")方法获得被拖的数据。该方法将返回在setData()方法中设置的为相同类型的任何数据。
> 被拖数据是被拖元素的id
> 把被拖元素放置到放置元素（目标元素）中。