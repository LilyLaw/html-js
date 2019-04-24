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

### 正则表达式对象属性

- global 是否是全局搜索，默认是false
- ignoreCase 是否忽略大小写，默认是false
- multiline 是否是多行搜索，默认是false
- source 表达式文本内容（不包含修饰符）
- lastIndex  当前表达式匹配内容的最后一个字符的下一个位置

### 正则表达式对象方法

-test 测试字符串参数中是否存在匹配正则表达式模式的字符串





