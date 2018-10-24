## 事件冒泡深度解析


``` html
	<html>
	<head>
		<meta charset="utf-8">
		<title>bubble event</title>
		<style>
		.ele0 {
			width: 400px;
			height: 400px;
			border: 1px solid black;
			background-color: red;
			position: relative;
		}

		.ele1 {
			width: 300px;
			height: 300px;
			border: 1px;
			background-color: green;
			position: absolute;
			top: 0;
		}

		.ele2 {
			width: 200px;
			height: 200px;
			border: 1px;
			background-color: blue;
			position: absolute;
			top: 0;
		}
		</style>
		<script>
		window.onload = function() {
			var ele = document.getElementsByTagName("div");

			if (ele[0].addEventListener) {
				ele[0].addEventListener("click", function() {
					console.log("点击的是盒子ele0！");
				});
			} else {
				ele[0].attachEvent("onclick", function() {
					console.log("点击的是盒子ele0！");
				});
			}
			if (ele[1].addEventListener) {
				ele[1].addEventListener("click", function() {
					console.log("点击的是盒子ele1!");
				});
			} else {
				ele[1].attachEvent("onclick", function() {
					console.log("点击的是盒子ele1！");
				});
			}

			if (ele[2].addEventListener) {
				ele[2].addEventListener("click", function() {
					console.log("点击的是盒子ele2！");
				});
			} else {
				ele[2].attachEvent("onclick", function() {
					console.log("点击的是盒子ele2！");
				});
			}
		}
		</script>
	</head>

	<body>
		<div class="ele0">
			<div class="ele1">
				<div class="ele2"></div>
			</div>
		</div>
	</body>
	<html>
```