## [严格模式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)

提供更强的错误检查,增强安全性

严格模式使用方式

1. 方法内引用:
``` javascript
function func(){
	'use strict';
}
```

2. 全局引用
``` javascript
'use strict';

function func(){
	// xxx
}
```

### 严格模式下的特殊要求

1. 不允许用with
2. 不允许未声明的变量被赋值.
3. arguments 变为参数的静态副本.
	看一下这段代码:
	``` javascript
	function changeName(name){
		'use strict';  //使用严格模式
		arguments[0] = 'Changed';
		console.log(name);
	}

	function changeNameTwo(name){
		arguments[0] = 'Changed';
		console.log(name);
	}

	changeName('Vivan');	// Vivan  严格模式下不会被改变
	changeName();			// undefined
	changeNameTwo('Vivan');	// Changed
	changeNameTwo();		// undefined
	```
	
	但当**参数为引用类型**数据时,则有别于基本数据类型,会相互影响
	``` javascript
	function changeName(person){
		'use strict';
		arguments[0].name = 'Changed';
		console.log(person.name);
	}

	function changeNameTwo(person){
		arguments[0].name = 'Changed';
		console.log(person.name);
	}

	changeName({name:'lily'});	// Changed
	changeNameTwo({name:'lily'});	// Changed
	```

4. delete 函数或参数会报错
	``` javascript
	!function(a){
		'use strict';
		delete a;  // 报错,SyntaxError
	}(1)
	```

5. delete 不可配置的属性也会报错
	``` javascript
	!function(){
		'use strict';
		var obj = {};
		Object.defineProperty(obj,'a',{configurable:false};
		console.log(delete a);   // 报错
	}()
	```

6. 禁止八进制字面量
	``` javascript
	'use strict';
	var a = 0123;
	console.log(b);  // 报错
	```
