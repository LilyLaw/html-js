## Html 全局属性

----------
### accesskey

> 激活（使元素获得焦点）元素的快捷键。
> 支持accesskey属性的元素有：```<a>```,```<area>```,```<button>```,```<input />```,```<label>```,```<legend>```,```<textarea>```。

如下代码：

``` html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>accesskey</title>
	</head>
	<body>
		<div>
			<input type="number" accesskey="h"  value="it's accesskey is h" />
		</div>
		<div>
			<label for="testinputacc" accesskey="i">it's accesskey is i</label>
			<input type="text" id="testinputacc" value="it's accesskey is i">
		</div>
		<div>
			<button accesskey="j">it's accesskey is j</button>
		</div>
		<div>
			<a href="http://www.baidu.com" target="_blank" accesskey="k">it's accesskey is k</a>
		</div>
		<div>
			 <textarea name="" id="" cols="30" rows="10" accesskey="l">it's accesskey is l</textarea>
		</div>
	</body>
	</html>
```

**注意事项**
> 虽然说 ```accesskey``` 属性值和键盘对应，但并不是说直接按下这个键，就能快捷访问。浏览器是通过组合访问的形式进行页面元素的快速访问的。具体组合方式见下表

|         | windows       | Linux         | Mac             |
| ------- | ------------- | ------------- | --------------- |
| Firefox | Alt+shift+key | Alt+shift+key | Control+Alt+key |
| IE      | Alt + key     | 无            | 无              |
| Chrome  | Alt + key     | Alt + key     | Control+Alt+key |
| Safari  | 无            | 无            | Control+Alt+key |
| Opera   | 同 Chrome     | 同 Chrome     | 同 Chrome       |

----------

### class

> class 属性规定元素的类名（classname）。
> class 属性大多数时候用于指向样式表中的类（class）。不过，也可以利用它通过 JavaScript 来改变带有指定 class 的 HTML 元素。

**注意事项**
1.  class 属性不能在以下Html元素中使用：```base，head，html，meta，param，script，style，title```
2.  可以给 HTML 元素赋予多个 class，例如：```<span class="left_menu important">```。这么做可以把若干个 CSS 类合并到一个 HTML 元素。
3.  类名不能以数字开头！只有 Internet Explorer 支持这种做法。

----------

### contenteditable

> contenteditable 属性规定元素内容是否可编辑（如果元素未设置 contenteditable 属性，那么元素会从其父元素继承该属性。）。

如下代码 ：
``` html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>accesskey</title>
		<style>
			p{
				padding: 20px;
				background: lightgreen;
			}
			div{
				margin-top: 20px;
				padding: 20px;
				background:pink;
			}
		</style>
	</head>
	<body>
		<p contenteditable="true">这是可编辑的段落，试试来编辑吧</p>

		<div contenteditable="true">
			<p>这是可编辑的段落，来试试吧</p>
		</div>
	</body>
	</html>
```

----------

### data-*

> data-* 属性用于存储页面或应用程序的私有自定义数据。
> data-* 属性赋予我们在所有HTML元素上嵌入自定义data属性的能力。

data-* 属性包括两部分:
 - 属性名不应该包含任何大写字母，并且在前缀“data-”之后必须有至少一个字符。
 - 属性值可以是任意字符串。
 
 ```用户代理会完全忽略前缀为 "data-" 的自定义属性。```
 
 如下代码
``` html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>data-*</title>
	</head>
	<body>
		<ul>
			<li data-type = "animal">pig</li>
			<li data-type = "plant">tree</li>
			<li data-type = "human">Chinese</li>
		</ul>
	</body>
	</html>
```

----------

### dir

> dir 属性规定元素内容的文本方向。
> dir 属性在以下标签中无效：```<base>```，```<br>```，```<frame>```，```<frameset>```，```<hr>```，```<iframe>```，```<param>```，```<script>```。

如下代码
``` html
	<p dir="rtl">Write this text right-to-left ! abcdefghigklmnopqrstuvwxyz  !!!!!</p>
	<p dir="rtl"> 寒雨连江夜入吴，平明送客楚山孤 </p>

	<!-- 另一种展现形式 -->
	<p><bdo dir="rtl">芙蓉楼送辛渐</bdo></p>
	<p><bdo dir="rtl">王昌龄</bdo></p>
	<p><bdo dir="rtl">寒雨连江夜入吴，</bdo></p>
	<p><bdo dir="rtl">平明送客楚山孤。</bdo></p>
	<p><bdo dir="rtl">洛阳亲友如相问，</bdo></p>
	<p><bdo dir="rtl">一片冰心在玉壶。</bdo></p>
```

展示效果如下所示，自己思考
![dir展示效果](https://github.com/LilyLaw/html_js_training/blob/master/img/dir.png?raw=true)

----------

### draggable

> 规定元素是否可拖动。

实现拖动如下代码

``` html
	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>drag</title>
		<style>
			#divone, #divtwo {
				float: left;
				margin-right: 10px;
				width: 300px;
				height: 120px;
				line-height: 120px;
				text-align: center;
				border: 1px solid #808080;
			}
			p {
				vertical-align: middle;
			}
		</style>
	</head>
	<body>
		<div id="divone" ondrop="dragEnd(event)" ondragover="dragging(event)">
			<p draggable="true" id="dragP" ondragstart="dragStart(event)">abcdefghijklmn</p>
		</div>

		<div id="divtwo" ondrop="dragEnd(event)" ondragover="dragging(event)"></div>

		<script type="text/javascript">
			// 开始拖动
			function dragStart(ev){
				ev.dataTransfer.setData("Text",ev.target.id);
			}

			// 拖动中
			function dragging(ev){
				//去除浏览器对数据的默认处理
				ev.preventDefault();
			}

			// 拖放结束（放置）
			function dragEnd(ev){
				ev.preventDefault();
				var data = ev.dataTransfer.getData("Text");
				ev.target.appendChild(document.getElementById(data));
			}
		</script>
	</body>
	</html>
```
```具体的html拖放行为查看 drag.md 文件```

----------

### hidden

> hidden属性是布尔属性
> 浏览器不应该显示已规定hidden属性的元素

代码如下
``` html
	<div hidden="hidden">这是被隐藏的元素</div>
	<p>这是没有被隐藏的属性</p>
```

----------

### lang

> lang 属性规定元素内容的语言。
> lang 属性在以下标签中无效```<base>```，```<br>```，```<frame>```，```<frameset>```，```<hr>```，```<iframe>```，```<frame>```，```<script>```

如下代码
``` html
	<p lang="fr">Ceci est un paragraphe.</p>
```
[语言代码](http://www.w3school.com.cn/tags/html_ref_language_codes.asp)

----------

### spellcheck

> spellcheck 属性规定是否对元素进行拼写和语法检查：1. input 元素中的文本值；2. textarea元素中的文本；3. 可编辑元素中的文本。

```<p contenteditable="true" spellcheck="true">这是一个段落。</p>```

**这个属性很鸡肋，我没试出效果来**

----------

### title

> title 属性规定关于元素的额外信息。通常会在鼠标移动到元素上时显示一段工具提示文本。

如下代码

``` html
	<abbr title="People's Republic of China">PRC</abbr> was founded in 1949.
	<p title="Free Web tutorials">W3School.com.cn</p>
	<a href="http://www.baidu.com" title="百度官网">baidu</a>
```
**注意** title 属性常与 form 以及 a 元素一同使用，以提供关于输入格式和链接目标的信息。同时*它也是 abbr 和 acronym 元素的必需属性。*