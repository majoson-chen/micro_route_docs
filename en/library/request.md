# Request
This document introduces the built-in objects and methods of the `request` object
## Properties

### str: method
The browser access method, is usually `get`, `post`, `head`, `put`

### str: url
The `url` when browser accesses, usually does not include parameters
For example: `"/hello/world"` instead of `"/hello/world?user_name=abc"`

### str: http_version
HTTP version in browser message.

Usually: `http/1.1`

### dict: headers
Header information in browser message

This property can only get the `header` information sent by the browser. If you want to set the returned `header`, please set it in the `response` object

### tuple: addr
This property provides the `IP` and `port` accessed by the browser, such as: `("192.168.3.65", "10086")`

### dict: from
If the access mode is `post`, and the parameter `auto_recv` is set `True` when defining the route (default is true), then when `micro_route` receiving the browser's post data, it will attempt to resolve to Python dict object automatically

If the data sent by the browser is too large, the received data may be incomplete to resulting in parsing errors.

### dict: args

This dictionary is used to store parameters in the `url`.

For example, browser access `/hello?user_name=abc`

Then the `args` object will be resolved to: 

`{"user_name": "abc"}`

### bytes: data
This object is used to save the raw data provided by browser.

This object is not safe. If the data sent by the browser is too large, the data of this object may not be complete.

### socket.socket: client
This object points to the object of socket request initiated by browser.

You can call the object to process the data.

About more the information of `socket.socket`, [see here](http://docs.micropython.org/en/latest/library/usocket.html#methods)

## Methods

### func: recv_data (bufsize:int = 4096)

This method is used to receive the data sent by browser.

If you call this method manually, the data returned will not be saved in the `data` attribute

>@param bufsize: buffer size, The maximum size to received data.
>
> @return: bytes

**Examples:**
```python
# 读取完整的数据到 data 中
data = b"
part = request.recv_data (1024)
while part:
    b += part
    part = request.recv_data (1024)
    
# 这种方法会浪费多一个 变量part 的内存, 你可以使用 client.recvinto () 来避免这种浪费.
```