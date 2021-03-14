# Response

本文介绍 `Response` 对象的内置对象和方法



## 属性

### dict: headers

​	本字典用于储存即将发送的 `headers` 数据, 您可以直接修改本对象.



### socket.socket: client

​	本对象用于储存浏览器发起请求的 `socket` 对象, 您可以直接调用其中的方法来实现您自己的功能.

​	关于 `socket.socket` 的更多信息, 详见 [usocket – socket module — MicroPython 1.14 documentation](http://docs.micropython.org/en/latest/library/usocket.html#methods)



### str:  mime_type

​	本对象用来设定相应内容的 `MIME` 类型, 您可以直接设置本对象, `micro_route` 将会在发送报文时自动添加该对象.

​	默认为 `text/html`

​	想使用内置的 `MIME` 字典, 详见 [常量 - MIME_TYPES_MAP](./consts.html#dict-mimetypesmap-)

​	更多 `MIME` 类型, 详见 [MIME 参考手册 (w3school.com.cn)](https://www.w3school.com.cn/media/media_mimeref.asp)



### str: statu_code

​	本对象用于设定向浏览器相应的 `HTTP状态码` , 你可以手动设定此属性, 随后 `micro_route` 会在响应时自动使用此状态码.



## 方法

### func: send_header (

### 	statu_explane:str = None,

### 	content:str = ""

### )

​	本方法用于向浏览器发送HTTP报文, 随后可以向浏览器发送数据.

​	如果发送失败, 将会引发一个  `TimeoutError`

​	通过设置 `statu_code` 属性来设置相应的 `HTTP状态码` 

> @param statu_explane: 对此 `HTTP` 状态码的解释, 若留空则使用内置的解释字典
>
> @param content: 发送的正文内容, 若留空则只发送 `HTTP` 报文



### func: send (content:[str,bytes])

​	本函数将会向浏览器发送正文内容, 如果您还未调用过 `send_header` , 本方法会自动调用一遍.

​	您可以在处理路由中多次调用 send () 来发送数据以到达流式传输的目的.

​	如果发送失败, 将会引发一个  `TimeoutError`

> @param content: str|bytes 欲发送的内容
>
> @return : None



### func: redirect (

### 	location:str, 

### 	statu_code:str="302"

### )

​	本方法会向浏览器发送一个重定向的请求, 当发送此请求之后, 您返回的数据将被无效处理.

> @param statu_code: 欲使用的状态码. 302:临时定向 301:永久定向
>
> @return: None



### func: close ()

​	本方法将会关闭与客户端之间的连接.

> @return: None



### func: abort (

### 	statu_code:str=500, 

### 	content:str="", 

### 	statu_explane=None

### )

​	本方法将会中断客户端与 `micro_route` 之间的请求, 通常是服务器不想处理该请求或是客户访问了不该访问的数据时使用本方法.

> @param statu_code: str , 中断时返回的 `HTTP状态码` , 默认为500
>
> @param content: str, 欲返回的正文, 可留空. 该参数用于自定义错误界面
>
> @param statu_explane: str , 用于替换默认的 `HTTP状态码解释文本` 同上 `send_header ()`



### func: send_file (path:str)

​	发送一个本地文件.

> @param path: 请使用绝对路径, 如果你的文件位于 /www/index.html, 那么建议您填 "/www/index.html"
>
> @return None



