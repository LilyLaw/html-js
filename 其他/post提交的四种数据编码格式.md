## post提交的四种数据编码格式

### application/x-www-form-urlencode

form表单有一个属性```enctype```，用于设置将表单内容提交给服务器的MIME类型。当使用form表单并且```method="post"```提交数据的时候，enctype的默认值就是application/x-www-form-urlencode，将表单提交数据进行urlencode，在请求发送过程中会对数据进行序列化处理，以键值对形式，例如:
key1=value1&key2=value2的方式发送到服务器。如下代码

``` html
<form action="#" method="post">
	<p>姓名：<label for=""><input name="name" type="text"></label></p>
	<p>年龄：<label for=""><input name="age" type="text"></label></p>
	<p>性别：<label for=""><input name="sex" type="text"></label></p>
	<p><input type="submit" value="提交"></p>
</form>
```

浏览器的网络请求如下：

![x-www-form-urlencodde](https://github.com/LilyLaw/html_js_training/blob/master/img/x-www-form-urlencode.png?raw=true)

可以看到浏览器捕获的提交数据格式是键值对。这就是此种方式提交的数据编码。

### application/json

