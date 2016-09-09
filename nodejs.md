# nodejs

## Modules 模块
> 调用“require('name')”并将返回值赋给一个和模块同名的局部变量  

## Buffers 缓存对象
> 原始的数据保存在Buffer 类的实例中。Buffer 类似于一个整数数组，不同之处在于它和在V8内存堆之外分配的 一段内存数据相对应。Buffer 对象的大小不能调整。你可以通过"require('buffer').Buffer"来使用这个类。

## EventEmitter 事件触发器
> 所有能够触发事件的对象都是events.EventEmitter 的实例.  
> 当事件触发器过程中出现错误时，典型的处理方式是它将触发一个'error'事件。Error 事件的特殊性在于：如果 没有函数处理这个事件，它将会输出调用堆栈，并随之退出应用程序。