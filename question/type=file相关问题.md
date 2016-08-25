    function ProcessFile( e ) { 
        var file = document.getElementById('file').files[0] && document.getElementById('file').files;
        if (file) {
            var reader = new FileReader();
            reader.onload = function ( event ) { 
                var txt = event.target.result;
                document.getElementById("result").innerHTML = txt;
            };
        }
        reader.readAsDataURL( file );
    }
    function contentLoaded () {
        document.getElementById('file').addEventListener( 'change' , ProcessFile , false );
    }
    window.addEventListener( "DOMContentLoaded" , contentLoaded , false );
html代码

    <input type="file" accept="image/*" id="cameraInput" />

# 原因：实现图片上传预览效果
## keywords:
* DOMContentLoaded
* change
* FileReader、files、event.target.result、readAsDataURL()


### DOMContentLoaded:
页面文档完全加载并解析完毕之后,会触发DOMContentLoaded事件，HTML文档不会等待样式文件,图片文件,子框架页面的加载(load事件可以用来检测HTML页面是否完全加载完毕(fully-loaded))。

	document.addEventListener("DOMContentLoaded",function(){},false)
	
须ie9+浏览器支持，对于ie8可以使用readystatechange事件,在更早的IE版本中,可以通过每隔一段时间执行一次document.documentElement.doScroll("left")来检测这一状态，因为这条代码在DOM加载完毕之前执行时会抛出错误(throw an error)。

jq等js库实现dom节点加载完毕执行事件即是以上方法。

### change:
The change event is fired for \<input>,\<select>, and \<textarea> elements when a change to the element's value is committed by the user. Unlike the input event, the change event is not necessarily fired for each change to an element's value.

触发条件：

* When the element is activated (by clicking or using the keyboard) for \<input type="radio"> and \<input type="checkbox">;

* When the user commits the change explicitly (e.g. by selecting a value from a \<select>'s dropdown with a mouse click, by selecting a date from a date picker for \<input type="date">, by selecting a file in the file picker for \<input type="file">, etc.);

* When the element loses focus after its value was changed, but not commited (e.g. after editing the value of \<textarea> or \<input type="text">).

### FileReader对象
使用FileReader对象,web应用程序可以异步的读取存储在用户计算机上的文件(或者原始数据缓冲)内容,可以使用File对象或者Blob对象来指定所要处理的文件或数据.其中File对象可以是来自用户在一个\<input>元素上选择文件后返回的FileList对象,也可以来自拖放操作生成的 DataTransfer对象,还可以是来自在一个HTMLCanvasElement上执行mozGetAsFile()方法后的返回结果.

files属性：
一个FileList对象通常来自于一个HTML input元素的files属性,你可以通过这个对象访问到用户所选择的文件。

result属性：
读取到的文件内容.这个属性只在读取操作完成之后才有效,并且数据的格式取决于读取操作是由哪个方法发起的. 只读.

readAsDataURL()方法：
The readAsDataURL method is used to read the contents of the specified Blob or File. When the read operation is finished, the readyState becomes DONE, and the loadend is triggered. At that time, the result attribute contains  the data as a URL representing the file's data as a base64 encoded string.


