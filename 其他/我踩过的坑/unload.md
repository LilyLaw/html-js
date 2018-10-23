## unload (都是泪）

具体问题如下：
#### 1. onunload 事件无法 阻断 任何浏览器关闭页面的操作
代码1：
``` html
	<html>
	<head>
		<title></title>
	</head>
	<body onunload="alert('are you sure???')">
	</body>
	</html>
```
代码2：
``` html
	<html>
	<head>
		<title></title>
	</head>
	<body >
		<script>
			window.onunload=function(){
				alert("are you sure?");
			}
		</script>
	</body>
	</html>
```
2. 查了资料发现要用 onbeforeunload 
3. 用了onbeforeunload之后，发现IE浏览器可以，Chrome 和Firefox还是不行。

2  3 问题 代码如下
代码3：
``` html
	<html>
	<head>
		<title></title>
	</head>
	<body >
		<script>
			window.onbeforeunload=function(){
				return "are you sure?";
			}
		</script>
	</body>
	</html>
```
4. 很神奇的一点是，用onbeforeunload在Chrome和Firefox打断点那能出效果，不打断点还是不会阻止。

 **尼玛反正就是咋试在Chrome和Firefox都不行 (▼へ▼メ)**

----------

百度求助无门后翻墙看国外MDN。
> [MDN unload](https://developer.mozilla.org/en-US/docs/Web/Events/unload)
> [MDN beforeunload](https://developer.mozilla.org/en-US/docs/Web/Events/beforeunload)

----------

自己整理了解了一些，好像找到问题了(ಥ_ಥ) 

### unload

> The unload event is fired when the document or a child resource is being unloaded.

意思就是，unload事件会在  正在卸载文档和子资源的时候触发。

这个事件会在  ```beforeunload``` 和 ```pagehide``` **之后** 触发
（仔细解读上面那句话哦！）

 unload 事件触发时的文档在一种特定的状态：
 - 所有资源仍然存在（img，iframe等）
 - 最终用户看不到任何东西
 - UI交互无效（window.open,alert,confirm等）
		所以代码1和代码2中的alert是无效的，会报错。
 - 报错不会停止卸载该工作流程
	 意思就是即使报错了，这个页面继续卸载。
	 
 **所以尼玛unload这东西到底有啥用呢？？？反正页面最后也得关  ヽ(。_°)ノ**
 
 
 