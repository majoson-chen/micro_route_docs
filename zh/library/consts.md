# 常量

本页用来介绍 `micro_route` 中定义的常量

**如标题的末尾带有 `*` 字符, 则说明该对象可以供开发者使用和修改**

### int: DEBUG *

​	用来控制本模块的调试输出级别

​	0 - crash (默认)

​	1 - error

​	2 - warn

​	3 - info

​	4 - debug

​	可以直接修改本常量来控制输出级别



### str: charset *

​	用来控制 `micro_route` 的编码, 默认为 `utf-8`



### dict: _HTML_ESCAPE_CHARS *

​	`micro_route` 提供的字符转义列表, `micro_route` 在解析浏览器发送回来的字符串时会尝试对其进行转义

```python
# 原形
_HTML_ESCAPE_CHARS = micropython.const({
    "&amp;"   :  "&",
    "&quot;"  :  '"',
    "&apos;"  :  "'",
    "&gt;"    :  ">",
    "&lt;"    :  "<",
    "&nbsp"   :  " "
})
```



### dict: STATU_CODES *

​	`micro_route` 提供的字典对象用来保存HTTP状态码及其描述语言, 您可以通过修改它来达到自定义状态描述语言的目的. 状态码和状态描述语言将会用于 HTTP 协议的报文头部中, 例如:

​	HTTP/1.1 200 OK

​	对象原形:

```python
STATU_CODES:dict = micropython.const({
    '200' : 'OK',
    '201' : 'Created',Location头信息返回。
    '301' : 'Moved Permanently',
    '302' : 'Found',
    '304' : 'Not Modified',
    '403' : 'Forbidden',
    '404' : 'Not Found',
    '405' : 'Method Not Allowed',
    '500' : 'Internal Server Error',
    '502' : 'Bad Gateway',
    '503' : 'Service Unavailable',
    '505' : 'HTTP Version Not Supported'
})
```



### dict: MIME_TYPES_MAP *

​	这个字典用来存放文件后缀名与其对应的 IMME 类型, 您可以通过修改这个字典来达到自定义 IMME 类型的目的, 这个字典通常在发送本地静态文件时被使用.

​	函数原形

```python
MIME_TYPES_MAP:dict = micropython.const({
    ".txt"   : "text/plain",
    ".htm"   : "text/html",
    ".html"  : "text/html",
    ".css"   : "text/css",
    ".csv"   : "text/csv",
    ".js"    : "application/javascript",
    ".xml"   : "application/xml",
    ".xhtml" : "application/xhtml+xml",
    ".json"  : "application/json",
    ".zip"   : "application/zip",
    ".pdf"   : "application/pdf",
    ".ts"    : "application/typescript",
    ".woff"  : "font/woff",
    ".woff2" : "font/woff2",
    ".ttf"   : "font/ttf",
    ".otf"   : "font/otf",
    ".jpg"   : "image/jpeg",
    ".jpeg"  : "image/jpeg",
    ".png"   : "image/png",
    ".gif"   : "image/gif",
    ".svg"   : "image/svg+xml",
    ".ico"   : "image/x-icon"
    # others : "application/octet-stream"
})
```



### str: _TEMPLATE_HTTPRESP

​	这是 `micro_route` 用来响应 HTTP 请求的模板, 如果没有特殊需求请勿随便修改

​	函数原形

```python
_TEMPLATE_HTTPRESP:str = micropython.const ("""\
{http_ver} {statu_code} {statu_explane}\r\n\
{headers}\r\n\
{content}\
""")
```



### str: VERSION *

​	该常量提供了一个版本信息的文本串, 您可以在开发时打印他.



### str: \_\_REGXP\_*

​	这些变量指定了 `micro_route` 在处理 HTTP 请求时使用的 `regex` 表达式,

​	**请不要随意修改它们**

​	原形:

```python
__REGXP_TYPE_STRING = micropython.const("([^\d][^/|.]*)")
__REGXP_TYPE_INT = micropython.const("(\d*)")
__REGXP_TYPE_FLOAT = micropython.const("(\d*\.?\d*)")
__REGXP_TYPE_PATH = micropython.const("(.*)")
__REGXP_AGREEMENT = micropython.const("(GET|POST|HEAD|PUT|DELETE|CONNECT|OPTIONS|TRACE|PATCH) (.*) (.*)")
__REGXP_VAR_VERI = micropython.const("<(string|int|float|custom=.*):(\w+)>")
__comper_var_veri = re.compile (__REGXP_VAR_VERI)
__comper_agreement = re.compile (__REGXP_AGREEMENT)
```

