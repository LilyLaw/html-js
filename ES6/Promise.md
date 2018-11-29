## Promise 对象

抛砖引玉,先上一段代码:
``` html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>promise animation</title>
	<style>
		.ball{
			width: 40px;
			height: 40px;
			border-radius: 50%;
		}
		.ball1{
			background: lightgreen;
		}
		.ball2{
			background: pink;
		}
		.ball3{
			background: lightblue;
		}
	</style>
</head>
<body>
	<div class="ball ball1" style = "margin-left: 0;"></div>
	<div class="ball ball2" style = "margin-left: 0;"></div>
	<div class="ball ball3" style = "margin-left: 0;"></div>

	<script>
		var ball1 = document.querySelector('.ball1');
		var ball2 = document.querySelector('.ball2');
		var ball3 = document.querySelector('.ball3');

		function animate(ball,distance,cb){
			setTimeout(function(){
				var marginLeft = parseInt(ball.style.marginLeft,10);
				if(marginLeft===distance){
					cb&&cb();
				}else {
					if(marginLeft<distance){
						marginLeft++;
					}else if(marginLeft>distance){
						marginLeft--;
					}


					ball.style.marginLeft = marginLeft + "px";

					animate(ball,distance,cb);
				}
			},13);
		}

		animate(ball1,100,function(){
			animate(ball2,200,function(){
				animate(ball3,300,function(){
					animate(ball3,150,function(){
						animate(ball2,150,function(){
							animate(ball1,150,function(){
							});
						});
					});
				});
			});
		});
	</script>
</body>
</html>
```

在浏览器里查看效果

在调用阶段的代码如下:
``` javascript
animate(ball1,100,function(){
	animate(ball2,200,function(){
		animate(ball3,300,function(){
			animate(ball3,150,function(){
				animate(ball2,150,function(){
					animate(ball1,150,function(){
					});
				});
			});
		});
	});
});
```

可以很容易发现问题: 代码层级环环相扣,如果想改变某一个的执行顺序,则必须将之后的代码执行顺序一个一个调过来.非常麻烦,不利于维护.

基于上述问题,我们优化代码,使用Promise来实现.如下代码:
``` html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>promise animation</title>
	<style>
		.ball{
			width: 40px;
			height: 40px;
			border-radius: 50%;
		}
		.ball1{
			background: lightgreen;
		}
		.ball2{
			background: pink;
		}
		.ball3{
			background: lightblue;
		}
	</style>
</head>
<body>
	<div class="ball ball1" style = "margin-left: 0;"></div>
	<div class="ball ball2" style = "margin-left: 0;"></div>
	<div class="ball ball3" style = "margin-left: 0;"></div>

	<script>
		var ball1 = document.querySelector('.ball1');
		var ball2 = document.querySelector('.ball2');
		var ball3 = document.querySelector('.ball3');

		var Promise = window.Promise;
		function promiseAnimate(ball,distance){
			return new Promise(function(resolve,reject){
				function _animate(){
					setTimeout(function(){
						var marginLeft = parseInt(ball.style.marginLeft,10);
						if(marginLeft===distance){
							resolve();
						}else {
							if(marginLeft<distance){
								marginLeft++;
							}else if(marginLeft>distance){
								marginLeft--;
							}

							ball.style.marginLeft = marginLeft + "px";

							_animate();
						}
					},13);
				}
				_animate();
			});
		}

		promiseAnimate(ball1,100)
			.then(function(){
				return promiseAnimate(ball2,200);
			})
			.then(function(){
				return promiseAnimate(ball3,300);
			})
			.then(function(){
				return promiseAnimate(ball3,150);
			})
			.then(function(){
				return promiseAnimate(ball2,150);
			})
			.then(function(){
				return promiseAnimate(ball1,150);
			})
	</script>
</body>
</html>
```

调用阶段代码如下:
``` javascript
promiseAnimate(ball1,100)
	.then(function(){
		return promiseAnimate(ball2,200);
	})
	.then(function(){
		return promiseAnimate(ball3,300);
	})
	.then(function(){
		return promiseAnimate(ball3,150);
	})
	.then(function(){
		return promiseAnimate(ball2,150);
	})
	.then(function(){
		return promiseAnimate(ball1,150);
	})
```

具体逻辑稍后描述,但看代码就会发现较之前代码高内聚低耦合,改小球顺序只需简单移动本身即可,便于后期维护.

###  [Promise 简介][1]
[1]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
实现异步编程,比传统的解决方案更加强大合理.

Promise 对象有以下特点:
1.  对象状态不受外界影响,Promise对象代表一个一步操作,有3中状态:```pending```(进行中) ,```fulfilled```(已成功) ,```rejected```(已失败)
2.  一旦状态更改,就不会再变.

### 基本用法

创建实例:
``` javascript
var promise = new Promise(function(resolve,reject){
	if(/*异步操作成功*/){
		resolve();
	}else{
		reject();
	}
})
```

Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject。它们是两个函数，由 JavaScript 引擎提供，不用自己部署。

resolve函数的作用是，将Promise对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；reject函数的作用是，将Promise对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去.

Promise 实例生成以后,可以使用then方法分别指定resolved状态和rejected状态的回调函数.
``` javascript
promise.then(function(){
	//success
},function(err){
	//failure
});
```

then方法可以接受两个回调函数作为参数。第一个回调函数是Promise对象的状态变为resolved时调用，第二个回调函数是Promise对象的状态变为rejected时调用。其中，第二个函数是可选的，不一定要提供。这两个函数都接受Promise对象传出的值作为参数。

#### Promise.prototype.then()

   为 Promise 实例添加状态改变时的回调函数。前面说过，then方法的第一个参数是resolved状态的回调函数，第二个参数（可选）是rejected状态的回调函数。

   then方法返回的是一个新的Promise实例（注意，不是原来那个Promise实例）。因此可以采用链式写法，即then方法后面再调用另一个then方法。
   ``` javascript
	getJSON("/posts.json").then(function(json) {
	  return json.post;
	}).then(function(post) {
	  // ...
	});
   ```

#### Promise.prototype.catch()

   Promise.prototype.cath() 是 .then(null,rejection) 方法的别名,用于指定发生错误时的回调函数.
   ``` javascript
	getJson('/post/json').then(function(){
		// 请求成功,正常返回
	}).cathc(function(){
		// 处理getJson和前一个回调函数运行时发生的错误.
	});
   ```

   上面代码中，getJSON方法返回一个 Promise 对象，如果该对象状态变为resolved，则会调用then方法指定的回调函数；如果异步操作抛出错误，状态就会变为rejected，就会调用catch方法指定的回调函数，处理这个错误。另外，then方法指定的回调函数，如果运行中抛出错误，也会被catch方法捕获。

#### Promise.prototype.finally()

   finally() 方法用于指定不管Promise对象最后状态如何,都会执行的操作.该方法是ES2018引入的.
   ``` javascript
   promise
   		.then(function(){})
		.catch(function(){})
		.finally(function(){})
   ```
   下面是一个例子，服务器使用 Promise 处理请求，然后使用finally方法关掉服务器。
   ``` javascript
	server.listen(port)
	  .then(function () {
		// ...
	  })
	  .finally(server.stop);
   ```

   finally() 方法的回调函数不接受任何参数,所以没办法知道前面的promise状态到底是fulfilled还是rejected. 这表明,finally()方法里面的操作,应该是与状态无关,不依赖于Promise的执行结果.
   
 剩下的方法在http://es6.ruanyifeng.com/#docs/promise  
 自己看去吧,多看看例子

   
   




  
  
