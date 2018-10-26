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
	
   这段代码是说，点击div盒子就隐藏自身显示。
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
