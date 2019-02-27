## [input type=range][1]

定义带有 slider 控件的数字字段。注意该属性的浏览器兼容问题，若实际需要此类控件，建议自己写。

看如下代码：
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>input type=range</title>
    <style>
        div{
            width: 500px;
            margin: 50px auto;
        }
    </style>
</head>
<body>
    <div>
        <input type="range" name='lllrange' step="4" onchange="testxx(this.value)" min='-100' max='100'>
    </div>

    <div>
        <input type="range" list="tickmarks" onchange="testxx(this.value)" name="anrange">
        <datalist id="tickmarks">
          <option value="0">
          <option value="10">
          <option value="20">
          <option value="30">
          <option value="40">
          <option value="50">
          <option value="60">
          <option value="70">
          <option value="80">
          <option value="90">
          <option value="100">
        </datalist>
    </div>

    <div>
        <input type="range" list="antickmarks" onchange="testxx(this.value)" name="ttrange">
        <datalist id="antickmarks">
          <option value="0" label="0%">
          <option value="10">
          <option value="20">
          <option value="30">
          <option value="40">
          <option value="50" label="50%">
          <option value="60">
          <option value="70">
          <option value="80">
          <option value="90">
          <option value="100" label="100%">
        </datalist>
    </div>

    <script>
        function testxx(e){
            console.log(e);
        }
    </script>
</body>
</html>
```


  [1]: https://developer.mozilla.org/zh-TW/docs/Web/HTML/Element/input/range