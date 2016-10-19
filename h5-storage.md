## h5之前 -- cookies
* http请求头携带cookies信息
* 大小 4k
* 主Domain污染

## localStorage & sessionStorage
* localStorage 永久存储，sessionStorage 关闭浏览器或者新建tab页才失效
* 大小 5M
* API : getItem、 setItem、 removeItem、 key、 clear

注意事项：
* 需要异常处理，避免超出容量抛错
* IE8+支持

使用限制：
* 存储更新策略，过期控制
* 子域名之间不能共享存储数据
* 超出存储大小之后如何存储（LRU、FIFO）
* 客户端通过参数形式传递给server端

## indexedDB

## application cache
> 如果修改资源文件，必须通过修改manifest文件来刷新被缓存的文件列表
