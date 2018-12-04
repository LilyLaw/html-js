## ES6 简介

http://es6.ruanyifeng.com/

ECMAScript 6.0 (简称ES6) 是JavaScript的下一代标准，于2015年6月发布。目标是**使得JavaScript可以用来编写复杂的大型应用程序，成为企业级开发语言**。

> 看到此处应该想到，以后在开发的时候多考虑大型应用程序下的某些功能该如何实现，力求高性能，不将就

> 学习应该是踏踏实实的，不要急于求成，也不要过分钻牛角尖，没达到那个层面钻牛角尖也钻不出什么来。

> 学习一门语言，不仅要学习它的知识，也要学习它的文化，所以会偶尔涉及一点额外的东西。

### 1. ECMAScript 和 JavaScript 的关系

回顾历史，1996年11月，JavaScript的创造者[Netscape](https://en.wikipedia.org/wiki/Netscape) 将JavaScript标准提交给标准化组织 [ECMA](https://en.wikipedia.org/wiki/Ecma_International) ，希望这种语言能够成为国际标准。次年ECMA发布262号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言成为ECMAScript，此版本为1.0版。

https://www.ecma-international.org/publications/standards/Ecma-262.htm

### 2. ES6 和ECMAScript2015 的区别

文档 http://es6.ruanyifeng.com/#docs/intro#ES6-%E4%B8%8E-ECMAScript-2015-%E7%9A%84%E5%85%B3%E7%B3%BB

自己总结一下

### 3. 语法提案标准流程

文档 http://es6.ruanyifeng.com/#docs/intro#%E8%AF%AD%E6%B3%95%E6%8F%90%E6%A1%88%E7%9A%84%E6%89%B9%E5%87%86%E6%B5%81%E7%A8%8B

### 4. ECMAScript 历史

文档 http://es6.ruanyifeng.com/#docs/intro#ECMAScript-%E7%9A%84%E5%8E%86%E5%8F%B2

### 5. 部署进度

各大浏览器的最新版本，对ES6的支持可以查看 http://kangax.github.io/compat-table/es6/ 

node 是JavaScript的服务器运行环境（runtime），它对ES6 的支持度更高。

使用npm时候有不懂的看文档 https://docs.npmjs.com/

### 6. Babel转码器

[Babel](https://babeljs.io/) 是一个广泛使用的ES6 转码器，可以将ES6代码转换为ES5代码，这意味着你可以用ES6方式来编写代码，又不用担心是否支持。如下代码

``` javascript
// 转码前：
input.map(item=>item+1);

// 转码后
input.map(function(item){
	return item+1;
});
```



















卧槽这个文档好有用
https://www.cnblogs.com/weschen/p/7154284.html