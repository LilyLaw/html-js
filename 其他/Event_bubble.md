## 事件冒泡深度解析(自以为很深度了(￣ェ￣;))

不废话，先上代码：

``` html
<!DOCTYPE html>
<html>
  <head>
	<meta charset="utf-8">
	<title>Show video box example</title>
	<style>
		div {
			position: absolute;
			top: 50%;
			transform: translate(-50%, -50%);
			width: 480px;
			height: 380px;
			border-radius: 10px;
			background-color: #eee;
			background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.1));
		}
		.hidden {
			left: -50%;
		}
		.showing {
			left: 50%;
		}
		div video {
			display: block;
			width: 400px;
			margin: 40px auto;
		}
	</style>
  </head>
  <body>
	<button>Display video</button>
	<div class="hidden">
	  <video>
		<source src="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.mp4" type="video/mp4">
		<source src="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.webm" type="video/webm">
		<p>Your browser doesn't support HTML5 video. Here is a <a href="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.mp4">link to the video</a> instead.</p>
	  </video>
	</div>
	<script>
	  var btn = document.querySelector('button');
	  var videoBox = document.querySelector('div');
	  var video = document.querySelector('video');

	  btn.onclick = function() {
		videoBox.setAttribute('class','showing');
	  }

	  videoBox.onclick = function() {
		videoBox.setAttribute('class','hidden');
	  };

	  video.onclick = function() {
		video.play();
	  };
	</script>
  </body>
</html>
```
   解释一下代码，注意看js:
   
  这段代码是说，点击button就显示出div这个盒子（结合css）。
   ``` javascript
	btn.onclick = function() {
		videoBox.setAttribute('class','showing');
	}
   ```
	
   这段代码是说，点击div盒子就隐藏自身（结合css）。
   ``` javascript
	videoBox.onclick = function() {
		videoBox.setAttribute('class','hidden');
	};
   ```

   这段代码是说，点击video就播放。
   ``` javascript
	video.onclick = function() {
		video.play();
	};
   ```
   
   再回头看DOM结构，很容易发现问题：
   ``` html
	<div class="hidden">
		  <video>
			<source src="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.mp4" type="video/mp4">
			<source src="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.webm" type="video/webm">
			<p>Your browser doesn't support HTML5 video. Here is a <a href="https://github.com/LilyLaw/html_js_training/blob/master/img/rabbit320.mp4">link to the video</a> instead.</p>
		 </video>
	</div>
   ```
   video 标签在div标签里面，那么你点击了video也就点击了外面的div，确实会使视频自动播放，可是也让div隐藏了。
   所以即使你只点击了video也触发了两者的事件句柄。
   
### 冒泡和捕捉

   当一个绑定在拥有父元素的元素上的事件被触发了（比如上面例子中的```<video>```），现在的浏览器运行两个不同的阶段——捕获阶段和冒泡阶段。

#### 捕获阶段
 - 浏览器检查元素的最外层祖先（```<html>```）是否在捕获阶段在其上注册了onclick事件处理程序，如果是，则运行它。
 - 然后移动到```<html>```里面的下一个元素，重复上述操作，以此类推，直到他实际到达单击的元素。


#### 冒泡阶段
 - 浏览器检查被点击的元素是否在冒泡阶段在其上注册了`onclick` 事件句柄，如果有的话就运行它。
 - 之后移动到当前元素的下一个直接祖元素重复上述操作，以此类推，直到到达```<html>```元素。

如图所示：
![bubbling-capturing](https://github.com/LilyLaw/html_js_training/blob/master/img/bubbling-capturing.png)


在现代浏览器中，默认情况下，所有事件处理程序都在冒泡阶段注册。因此，在我们当前的示例中，当您单击视频时，单击事件会从```<video>```元素向外冒泡到```<html>```元素。一路上：
 - 找到```video.onclick```句柄然后执行，所以视频播放。
 - 继续向上冒泡找到```videoBox.onclick```句柄然后执行，所以视频也被隐藏了。

#### 使用stopPropagation()解决问题

   stopPropagation() 方法阻止冒泡，它调用注册在当前元素事件然后执行它，但事件链不会再向上冒泡，它的祖元素上的事件不会被执行。
   所以可以像下面这样修改代码：
   ``` javascript
	video.onclick = function(event) {
        event.stopPropagation();  //阻止冒泡
        video.play();
    };
   ```
   
   **历史缘由** 为什么要同时捕捉和冒泡？在糟糕的旧时代，浏览器与现在的交叉兼容性要低得多，Netscape只使用事件捕获，而Internet Explorer只使用事件冒泡。当W3C决定尝试标准化行为并达成共识时，他们最终得到了这个包含两者的系统，这是一个现代化的浏览器实现的。
   
   **拓展一下** 默认情况下，所有事件处理程序都在冒泡阶段进行注册，这在大多数情况下更有意义。如果你真的想在捕获阶段注册一个事件，你可以通过使用addEventListener（）注册你的处理程序，并将可选的第三个属性设置为true来实现(￣▽￣)／。（看一下就行，目前感觉没啥用。）
   
#### 事件委托

   冒泡也允许我们利用事件委托 - 这个概念依赖于这样的事实：如果你想要点击大量子元素中的任何一个时运行一些代码，你可以在他们的父元素上设置事件监听器并且发生在他们身上的事件会冒泡到他们的父母，而不是必须单独为每个孩子设置事件监听器。
   **这个感觉非常有用哦！曾经遇到过很多这样的需求哦！ミﾟДﾟ彡**
   
   [事件委托](https://github.com/LilyLaw/html_js_training/blob/master/%E5%85%B6%E4%BB%96/Event_delegation.md)
   
### 总结

   事件实际上并不是核心JavaScript的一部分 - 它们是在浏览器Web API中定义的。