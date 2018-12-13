## 语法糖

语法糖（Syntactic sugar），也译为糖衣语法，是由英国计算机科学家彼得·约翰·兰达（Peter J. Landin）发明的一个术语，指计算机语言中添加的某种语法，这种语法对语言的功能并没有影响，但是更方便程序员使用。通常来说使用语法糖能够增加程序的可读性，从而减少程序代码出错的机会。

如下代码：

``` javascript
let [a, b, c, d] = [1, 'aa', '**', 5];
console.log(a);
console.log(b);
console.log(c);
console.log(d);
console.log("---------------");
//Symbol(值类型数据，唯一的)
let [e, f] = [3, 3];
console.log(e == f);
let g = Symbol(3);
let h = Symbol(3);
console.log(g == h);
console.log("---------------");
//Set 去除重复值
var set = new Set([1, 1, 2, 2, 3, 3, 5, 5, 4, 6, 4, 6]);
console.log(set);
for (var key of set) {
	console.log(key);
}
console.log("---------------");
//箭头函数
let fn = () => {
	return "fn";
}
console.log(fn());
```

更多的解释看这个文档  https://segmentfault.com/a/1190000010159725