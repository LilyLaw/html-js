## try catch

主要是代码执行顺序的问题，在浏览器里自己运行一下

``` javascript
try{
	try{
		throw new Error('里面的错误');
	}
	catch(error){
		console.log('报错啦： ',error);
	}
	finally{
		console.log('里面的结束了')
	}

	throw new Error('外面的错误')
}
catch(error){
	console.log('报错啦：  ', error);
}
finally{
	console.log('外面结束了');
}
```