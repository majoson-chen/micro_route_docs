# library

本页提供与本模块相关的常量, 函数, 方法, 对象等信息

## 索引:

- [常量](./consts.html)
- [函数](./functions.html) - `micro_route` 的辅助函数
- [request](./request.html) - 在响应期间用于获取客户端信息
- [response](./response.html) - 在响应期间用于回应客户端的请求
- [session](./session.html) - 获取客户端的会话信息



## request response session 的使用方法

​	`request` `response` `session`对象在响应路由的 context 对象中获取.

​	**示例:**

```python
import micro_route

@app.route ('/')
def index (context):
    request = context.request
    response = context.response
    session = context.session
    
    return str (request.addr) + " visted."
```



### 为什么不像 Flask Django 一样把 `request` `response` `session` 封装为全局对象?

​	考虑到适用性问题, 有些开发板并不支持多线程模块, 而且像 Flask 那样把这三个对象封装成为全局对象需要涉及到内存的堆栈操作, 这在性能较低的开发版上显得有些力不从心.