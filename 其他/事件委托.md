## 事件委托

   事件委托允许你不在每一个具体的节点上添加事件监听器（如```onclick```），而是将事件监听器添加在父元素上。该事件监听器分析冒泡事件以查找匹配的子元素。
   
   上代码：
   ``` html
   <!DOCTYPE html>
	<html>
	  <head>
		<meta charset="utf-8">
		<title>事件委托</title>
		<style>
			ul{
				background:lightgreen;
				padding: 0;
				overflow: hidden;
			}
			li{
				background: pink;
				margin:20px 0;
				padding: 10px;
				list-style: none;
			}
		</style>
	  </head>
	  <body>
		<ul id="parent-list">
			<li id="post-1">Item 1</li>
			<li id="post-2">Item 2</li>
			<li id="post-3">Item 3</li>
			<li id="post-4">Item 4</li>
			<li id="post-5">Item 5</li>
			<li id="post-6">Item 6</li>
		</ul>

		<script>
			// 先不写哦！
		</script>
	  </body>
	</html>
   ```
   
   **要求实现** 点击某一个```<li>``` 文字颜色变为黄色，同级的```<li>``` 颜色都是黑色。
   
   若按照以往思路，则给每一个```<li>```添加一个事件监听器```onclick``` ,现在使用事件委托来实现，将监听器添加给父元素，js代码如下所示：
   ``` javascript
    var eParent = document.getElementById("parent-list");
	eParent.onclick = function(event){
		eTarget = event.target;

		// 判断点击的是不是li标签，如果不加判断点击ul标签则所有li字体颜色都变黄色
		if(eTarget.nodeName.toLowerCase()=="li"){
			// 所有子元素字体颜色变成黑色。
			for(var i = 0;i < eParent.children.length;i++){
				eParent.children[i].style.color = "black";
			}
			
			// 目标元素字体颜色变成黄色。
			eTarget.style.color = "yellow";
		}
    }
   ```
   
为什么建议用事件委托，而不是给每个子元素添加事件监听器呢？

试想一下，如果```li```被频繁的添加或删除，那么添加监听事件会很麻烦（每增加一个元素就要添加对应的所有事件）尤其是添加和删除代码位于元素的不同位置，简直噩梦。

   综上，利用事件委托可以有以下两点好处：
   1. 提高性能（**其实我还是没懂怎么就提高性能了，因为每个子元素没有监听器就提高性能了吗？？？[・ヘ・?]** ）
   2. 新添加的元素拥有对应的所有事件
      
   
   此处踩坑，  [DOM那些children。。。(T﹏T) ](https://github.com/LilyLaw/html_js_training/blob/master/%E5%85%B6%E4%BB%96/%E6%88%91%E8%B8%A9%E8%BF%87%E7%9A%84%E5%9D%91/childrenNode.md)
   
  此外需要了解一下 [javascript 性能](https://github.com/LilyLaw/html_js_training/blob/master/%E5%85%B6%E4%BB%96/javascript_performance.md)