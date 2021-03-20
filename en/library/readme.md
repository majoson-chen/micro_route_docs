# library
This page provides constant, function, method, object and other information related to this module
## Index:
- [constant](./consts.html)
- [function](./functions.html) - The tool functions of `micro_route`
- [request](./request.html) - used to get client information during response
- [response](./response.html) - used to responed the requests
- [session](./session.html) - get session information for client

## The use method of `request` `response` and `session`
The `request` `response` `session` object is obtained in the context object of the response route
**example:**
```python
import micro_route

@app.route ('/')
def index (context):
    request = context.request
    response = context.response
    session = context.session
    
    return str (request.addr) + " visted."
```

### Why not encapsulate the `request` `response` and `session` as a global object, as in the case of Flask or Django?
​	考虑到适用性问题, 有些开发板并不支持多线程模块, 而且像 Flask 那样把这三个对象封装成为全局对象需要涉及到内存的堆栈操作, 这在性能较低的开发版上显得有些力不从心.

↑ I don't know hot to translate it.