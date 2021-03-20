# Constant
This page is used to introduce Constants defined in `micro_route`

**If there is a '*' character at the end of the title, the object can be used and modified by developers**

### int: DEBUG *

Used to control the debug output level of this module

0 - crash (default)

1 - error

2 - warn

3 - info

4 - debug

You can modify this constant to control the output level

### str: charset *
Used to control The charset of `micro_route`, UTF-8 is by default

### dict: _HTML_ESCAPE_CHARS *
​	The character escape list provided by `micro_route`,it  will try to escape the string sent back by the browser when parsing it
```python
#Prototype
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
​	The dictionary object provided by route `micro_route` is used to store the HTTP status code and its description language. You can modify it to achieve the purpose of self defining the status description language

such as:

​	HTTP/1.1 200 OK

```python
#Prototype
STATU_CODES:dict = micropython.const({
    '200' : 'OK',
    '201' : 'Created',
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
This dictionary is used to store the file suffix and its imme type. You can customize the imme type by modifying this dictionary. This dictionary is usually used when sending local static files

```python
#Prototype
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
This is the template `micro_route ` used to respond to HTTP requests. If there are no special requirements, please do not modify it

```python
#Prototype
_TEMPLATE_HTTPRESP:str = micropython.const ("""\
{http_ver} {statu_code} {statu_explane}\r\n\
{headers}\r\n\
{content}\
""")
```

### str: VERSION
This constant provides a text string of version information, which you can print at development time

### str: \_\_REGXP\_*
These variables specify the 'regex' expression used when `micro_route` processing HTTP requests.
**Please don't modify them at will**
```python
#Prototype
__REGXP_TYPE_STRING = micropython.const("([^\d][^/|.]*)")
__REGXP_TYPE_INT = micropython.const("(\d*)")
__REGXP_TYPE_FLOAT = micropython.const("(\d*\.?\d*)")
__REGXP_TYPE_PATH = micropython.const("(.*)")
__REGXP_AGREEMENT = micropython.const("(GET|POST|HEAD|PUT|DELETE|CONNECT|OPTIONS|TRACE|PATCH) (.*) (.*)")
__REGXP_VAR_VERI = micropython.const("<(string|int|float|custom=.*):(\w+)>")
__comper_var_veri = re.compile (__REGXP_VAR_VERI)
__comper_agreement = re.compile (__REGXP_AGREEMENT)
```