## RegExp 对象

JavaScript内置对象RegExp支持正则表达式

一般有两种实例化RegExp对象的方法

### 字面量

```javascript
let reg1 = /\bis\b/g , reg2 = /\bis\b/;	// 实例化的RegExp对象。
let str = 'he is a boy , is he good at math, is n ';
let res1 = str.replace(reg1,'IS'), res2 = str.replace(reg2,'IS');

console.log(res1);	// he IS a boy , IS he good at math, IS n 
console.log(res2);	// he IS a boy , is he good at math, is n 
```
体会一下 ```g``` 的作用


### 构造函数

``` javascript
let reg1 = new RegExp('\\bis\\b') , reg2 = new RegExp('\\bis\\b','g');
let str = 'he is a boy , is he good at math, is n ';
let res1 = str.replace(reg1,'IS'), res2 = str.replace(reg2,'IS');

console.log(res1);	// he IS a boy , is he good at math, is n 
console.log(res2);	// he IS a boy , IS he good at math, IS n
```

### 修饰符

```g``` : global 全文搜索，如果不写，则默认只匹配第一个
```i``` : ignore case 忽略大小写，默认是大小写敏感的
```m``` : multiple lines 多行搜索

### 元字符

正则表达式由两种基本字符组成

- 原义文本字符
- 元字符：在正则表达式中有特殊含义的字符
	比如 ： `*`,`+`,`?`,`$`,`^`,`.`,`|`,`\`,`(`,`)`,`{`,`}`,`[`,`]`



