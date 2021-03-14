# MICRO_ROUTE

本对象是本模块中的入口类, 用于创建一个 `WEB应用`的 `APP对象`



## 属性

​	暂无



## 方法

### func: \_\_init\_\_ (

### 	bind_ip:str="0.0.0.0",

### 	bind_port:int=80, 

### 	root_path:str='/www', 

### 	sock_family:int = socket.AF_INET

### )

​	本方法用来实例化一个 `WEBAPP` 对象

> @param bind_ip: 指定服务器将会绑定的端口
>
> @param bind_port: 指定服务器将会绑定的端口
>
> @param root_path: 指定存放静态文件的文件夹地址, 当没有定义响应路由时, `micro_route` 会自动去该文件夹中寻找相应的文件并发送.
>
> @return: obj

​	**例子:**

```python
import micro_route
app = micro_route.MICRO_ROUTE ()
```



### func: append_to_route_tree (

### 	rule:str,

### 	func:object,

### 	method:str,

### 	var_l:list,

### 	auto_recv:bool

### )

​	该方法用来添加一个路由, 一般用户不需要用到此方法.

​	当你使用 `@app.route()` 时, 程序会自动解析并调用此方法.



### func: route (rule:str='/',method:str="GET",auto_recv:bool=True)

​	本方法是一个装饰器, 用来指定一个处理路由.

> @param rule: 欲监听的URL规则, 可以使用魔法变量
>
> @param method: 监听的响应方式, 可填 `"GET"` `"POST"` `"PUT"` 等等
>
> @param auto_recv: 指定是否自动读取浏览器发送来的数据并自动解析, 如果浏览器将会发送一个很大的数据包, 建议您关闭它.

​	**例子：**

```python
import micro_route
app = micro_route.MICRO_ROUTE ()

@app.route ("/","POST")
def index ():
    print ("A post vist")
	return "hi" # this will send to the browser.
```



### func: run (

### 		timeout:int=None,

### 		backlog:int=5,

### 		blocked:bool=False,

### 		muti_thread:bool = False

### )

​	本函数用于开始WEB服务器的监听.

​	关于多线程和阻塞的详细详细, 详见 [四种工作方式](../workmethods.html)

> @param timeout: 设定超时时间, 可能在一些开发版上无法工作.
>
> @param backlog: `socket` 允许同时连接的 `TCP` 数量
>
> @param blocked: 设定本方法是否阻塞.
>
> @param muti_thread: 设定是否启用多线程.



​	