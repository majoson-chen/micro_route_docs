# Request

本文介绍 `request` 对象的内置对象和方法



## 属性

### str: method

​	浏览器访问的方式, 通常为: `"GET"` `"POST"` `"HEAD"` `"PUT"`



### str: url

​	浏览器访问时的 `url` , 通常不包括参数.

​	例如: `"/hello/world"` 而不是 `"/hello/world?user_name=abc"`



### str: http_version

​	浏览器报文中的 http 版本

​	通常为: `HTTP/1.1`



### dict: headers

​	浏览器报文中的 Headers 信息.

​	本属性只能获取浏览器发送的 `header` 信息, 如果你想设置返回的 `header` , 请在 `response` 对象中设置.



### tuple: addr

​	本属性提供浏览器访问的 ip 和 端口, 形如: `("192.168.3.65", "10086")`



### dict: from

​	如访问方式为 `"POST"` , 且定义路由时设置参数 `auto_recv` 为 `True` (默认为True) , 则 `micro_route` 在接收到浏览器的 `POST` 数据时会尝试自动解析为python的 `dict` 对象.

​	如果浏览器发送的数据过大, 可能会使 `micro_route` 接收的数据不完整从而导致解析错误.



### dict: args

​	本字典用于储存 url 中的参数.

​	例如浏览器访问 `/hello?user_name=abc`

​	那么 `args` 对象就会被解析为: 

`{"user_name": "abc"}`



### bytes: data

​	本对象用于储存 `micro_route` 在解析时获取到的数据.

​	本对象是不安全的, 如果浏览器发送的数据过大, 那么此对象的数据可能不完整.



### socket.socket: client

​	本对象指向浏览器发起的socket请求的对象.

​	你可以直接调用该对象处理数据.

​	关于 `socket.socket` 的更多信息, 详见 [usocket – socket module — MicroPython 1.14 documentation](http://docs.micropython.org/en/latest/library/usocket.html#methods)



## 方法:

### func: recv_data (bufsize:int = 4096)

​	本方法用于接收浏览器发送的数据.

​	如果您手动调用本方法, 返回的数据将不会存入 `data` 属性中

> @param bufsize: 缓冲区大小, 最大接收数据的大小.
>
> @return: bytes

​	**例子:**

```python
# 读取完整的数据到 data 中
data = b"
part = request.recv_data (1024)
while part:
    b += part
    part = request.recv_data (1024)
    
# 这种方法会浪费多一个 变量part 的内存, 你可以使用 client.recvinto () 来避免这种浪费.
```