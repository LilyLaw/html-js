## dataTransfer

dataTransfer对象用于保存拖放操作期间被拖动的数据。它可以保存一个或多个数据，每个数据有一种或多种数据类型，

### 属性

 1. dropEffect
	 获取或设置拖放操作的类型。值必须是"none","copy","link","move";
 2. effectAllowed
	 设置或返回被拖动元素允许发生的拖动行为
 3. files
	 包含在数据传输过程中所有可用的本地文件列表。如果拖动操作不涉及拖动文件，此属性列表为空。
 4. items
	 返回一个DataTransferItemList对象，改对象是所有拖动数据的列表。
 5. types
	返回一个DOMStringList对象，该对象包括了存入dataTransfer中数据的所有类型。
	
### 方法

 1. clearData(format)
	清除给定类型的数据，format参数可选。如果参数为空或者没有指定，所有关联的数据都会被清除。如果没有指定类型的数据或者数据传输过程中没有数据，则该方法不起任何作用。
 2. getData(format)
	返回给定类型的数据，参数可选。
 3. setData(format,data)
	设置给定类型的数据。如果原先不存在给定类型的数据，则新增。如果给定类型的数据已存在，则替换。
 4. setDragImage(element,x,y)
	设置拖放操作的自定义图标。其中element设置自定义图标，x设置图标与鼠标在水平方向上的距离，y设置图标与鼠标在垂直方向上的距离。
	
	代码实例：
``` html
<!DOCTYPE html>
<html>

<head>
    <title></title>
    <meta charset="utf-8">
    <style>
        div{
            width:400px;
            height:200px;
            background: lightgreen;
            margin-bottom: 20px;
            padding: 20px;
            box-sizing: border-box;
        }
        p{
            width: 200px;
            height: 100px;
            background: pink;
            margin: 0;
        }
    </style>
</head>

<body>
    <div id="originbox" ondrop="drop(event);" ondragover="allowDrop(event);">
        <p id="dragEle" draggable="true" ondragstart="dragbegin(event);">拖拽我</p>
    </div>
    <div id="targetbox" ondrop="drop(event);" ondragover="allowDrop(event);"></div>
    <img src="15.jpg" style="width: 20px;height: auto;" alt="">
    <script type="text/javascript">
        function dragbegin(event){
            event.dataTransfer.setData("testmememem",event.target.id);
            var img = new Image();
            img.src = "15.jpg";
            img.style.width = "20px";
            img.style.height ="auto";
            console.log(img);
            event.dataTransfer.setDragImage(img,0,0);
        }
        function allowDrop(event){
            event.preventDefault();
        }
        function drop(event){
            var a = event.dataTransfer.getData("testmememem");
            document.getElementById(event.target.id).appendChild(document.getElementById(a));
        }
    </script>
</body>

</html>
```
	
**注意** event.preventDefault() 阻止浏览器对事件的默认行为。