# [7天学习nodejs](http://nqdeng.github.io/7-days-nodejs/)

## 优点

* 事件机制
* 异步io模型

## nodes基础
### 模块
> 模块内预先定义好的三个变量：require、exports、module  

1. require

> require函数用于在当前模块中加载和使用别的模块，传入一个模块名，返回一个模块导出对象,模块名中的.js可以省略，还可以使用require加载json文件

2. exports

> exports对象是当前模块的导出对象，用于导出模块公有方法和属性。别的模块通过require函数使用当前模块时得到的就是当前模块的exports对象

3. module

> 通过module对象可以访问到当前模块的一些相关信息，但最多的用途是替换当前模块的导出对象。例如模块导出对象默认是一个普通对象，如果想改成一个函数的话，可以使用此方式

#### 模块初始化
> 一个模块中的JS代码仅在模块第一次被使用时执行一次，并在执行过程中初始化模块的导出对象。之后，缓存起来的导出对象被重复利用。

#### 主模块
> 通过命令行参数传递给NodeJS以启动程序的模块被称为主模块。主模块负责调度组成整个程序的其它模块完成工作。

### 二进制模块
> NodeJS支持使用C/C++编写二进制模块。编译好的二进制模块除了文件扩展名是.node外，和JS模块的使用方式相同。

## 代码组织和部署
### 模块路径解析规则
> require函数支持斜杠（/）或盘符（C:）开头的绝对路径，也支持./开头的相对路径,也支持第三种类似类似于foo/bar的写法。

1. 内置模块  

如果传递给require函数的是NodeJS内置模块名称，不做路径解析,require('fs')

2. node_modules目录

NodeJS定义了一个特殊的node_modules目录用于存放模块。例如某个模块的绝对路径是/home/user/hello.js，在该模块中使用require('foo/bar')方式加载模块时，则NodeJS依次尝试使用以下路径。  
`/home/user/node_modules/foo/bar`
`/home/node_modules/foo/bar`
`/node_modules/foo/bar`

3. NODE_PATH环境变量

与PATH环境变量类似，NodeJS允许通过NODE_PATH环境变量来指定额外的模块搜索路径  
`NODE_PATH=/home/user/lib:/home/lib`











