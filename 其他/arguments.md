## arguments 变为参数的静态副本

先看一段代码理解一下

``` javascript
function myname(a,b){
	console.log(arguments[0]);	//1
	console.log(arguments[1]);	//2
}

myname(1,2);
```