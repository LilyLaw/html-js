## 框架

frameset 和 frame 简单示例

``` html
	<!DOCTYPE html>
	<html lang="en">
		<frameset cols="25%,50%,25%">
			<frame src="a.html">
			<frame src="b.html">
			<frame src="c.html">
		</frameset>
	</html>
```

### frameset

> frameset 元素可定义一个框架集，被用来组织多个窗口（框架）。每个框架存有独立的文档。在其最简单的应用中，frameset元素仅仅会规定在框架集中存在多少列或多少行，必须使用cols或rows属性。

**注意事项**
>frameset 标签 和 body 标签不能同时使用。
>若需要为不支持框架的浏览器添加一个 noframes 标签，则此标签必须放在```<body> </body>```标签中

### noframes

> noframes 元素可为那些不支持框架的浏览器显示文本。noframes 元素位于 frameset 元素内部。其中的文本必须包装在 ```<body></body>```  标签中！

noframes 示例
``` html
	<!DOCTYPE html>
	<html lang="en">
		<frameset cols="25%,50%,25%">
			<noframes>
				<body>
					您的浏览器不支持frame
				</body>
			</noframes>
			<frame src="a.html">
			<frame src="b.html">
			<frame src="c.html">
		</frameset>
	</html>
```

### frame

```<frame>``` 标签定义 frameset 中的一个特定的窗口（框架）。

[frame 基本属性](http://www.w3school.com.cn/tags/tag_frame.asp)