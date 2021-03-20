# micro_Route
**This document uses machine translation, so there will be some syntax error.**


[简体中文](Https://micro-route.m-jay.cn/docs/zh/) | English

[Project website](Https://micro-route.m-jay.cn/)

[Development Document | Document](Https://micro-route.m-jay.cn/docs/)

## I need help

I am not expert at English, so I need someone who is good at English help me to translate the document into English.

## What's this

This is a lightweight, simple, fast WEB framework working on `micropython`.

Why develop this framework?

As far as I know, the web frameworks that are known to run on `micropython` is [microWebSrv](Https://github.com/jczic/MicroWebSrv) But this framework needs `_Thread` module support

Unfortunately, this module is not supported on boards like `esp8266'.

At the same time, the operation of this module requires blocking the main thread, which means that your program can only act as a single server and cannot handle other things.

Therefore, we need a web framework that supports single-threaded running without blocking the main thread, so this framework came into being.

## Compare with microWebSrv

|Features/Framework      | micro_Route | microWebSrv |
| ---------------------- | ----------- | ----------- |
| Python Habitual Naming | *           |             |
| Single Thread Support  | *           | *           |
| Multithreading Support | *           | *           |
| Non-blocking Support   | *           |             |
| Multi-Object Support   | *           |             |
|Learning Cost           |Low          |High         |
|Complexity              |Simple       |Complex      |



Our goal is to provide a simple, fast and maintainable web service, and we will try to **simplify the code and reduce the API interface**, but leave most of the custom functionality available to developers.

`micro_route` only provides a few simple functions to complete all the things, but `microWebSrv` provides too many functions  which is less often used, it makes you confusion.

## How to Use
### Installation
First you need to go [Releases] (Https://github.com/Li-Lian1069/micro_Route/releases) Download a file with the `.mpy` suffix and upload it to your board.

**Remember not to put `micro_Route.py` and  `micro_Route.mpy` into the same folder, micropython will select only `micro_Route.py` to execute**

**Attention!! Do not use `micro_Route.py` As an imported object, this is the source code that not has been compiled and optimized, which may cause compile-time memory shortages and causing failures**

### Use

#### A simple example of

```python
# main.py
import micro_route, network

# connect to network
WLAN = network.WLAN (network.STA_IF)
WLAN.active (True)
WLAN.connect ("SSID","PASSWD")

# set the web route
app = micro_route ()
@app.route ('/')
def index (context):
    return "<h1>Hello World!</h1>"

app.run ()
```

When you visit `IP/', you will see `Hello World!'displayed on your browser.


#### Magic Path

```python
@app.route ('/goods/<string:goods_name>/')
def check_goods (context,goods_name:str):
    ...
```

In the example above, we defined a variable `goods_Name`, and it will be recognized and passed into `goods_Name` parameter ** (make sure they have the same name)**

The types of magic path support are:
- string
- int
- float (including int)
- path
- Custom (using user-defined regex rules, see development documentation for details)

Writing rules for magic paths: `<type:var_Name>`

**Make sure your `var_name` as same as the parameter name in your function**

##### context
You may notice that all the processing functions we define must have a parameter names `context`, which is `micro_route`'s Context objects created for you, including `request`, `response`, `session (not yet implemented)` three objects.

`request` is used to obtain user information such as url, access method, form data, parameters, headers, etc.

`response` is used to respond to customer access. If you don't want to simply transfer text using `return` , you can also use some of the methods in `response` to customize advanced processing.

`session` Used to save and manipulate user data (under development)

Detailed data about the above objects can be found in the development documentation

##### For more features, go to the documentation to see

## IDE support
Development without IDE support is obviously painful, and I recommend you install the `RT-Thread` plug-in in `VSCODE`, which provides code tips for `micropython` , or if you have other options.

**Remember not to put `micro_Route.py` and  `micro_Route.mpy` into the same folder, micropython will select only `micro_Route.py` to execute**

If you want to enable IDE hints and completion, I recommend you use the single file upload function of `RT-Thread`, only upload `micro_Rout.mpy` to your development board so you can enable code completion and prompting for the IDE.