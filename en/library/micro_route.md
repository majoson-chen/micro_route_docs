# MICRO_ROUTE
This object is the entry class in this module, which is used to create an app object of `web application`

## Properties
Not yet

## Methods

### func: \_\_init\_\_ (

### 	bind_ip:str="0.0.0.0",

### 	bind_port:int=80, 

### 	root_path:str='/www', 

### 	sock_family:int = socket.AF_INET

### )

This method is used to instantiate a `webapp` object
> @param bind_ip: Specifies the port that the server will bind to
>
> @param bind_port: Specifies the port that the server will bind to
>
> @param root_path: Specifies the folder address where static files are stored. When no response route is defined, `micro_Route` will automatically go to the folder to find the corresponding file and send it
>
> @return: obj
**Examples:**
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

This method is used to add a route, general users do not need to use this method
When you use `@app.route ()`, the program will automatically parse and call this method

### func: route (rule:str='/',method:str="GET",auto_recv:bool=True)

This method is a decorator to specify a processing route
> @param rule: the url rules you will listen, you can use magic variables instead.
>
> @param method: the response mode for it. You can fill in `"get"`, `"post"`, `"put"`, etc
>
> @param auto_recv: Specifies whether automatically to read and parse the data sent by the browser. If the browser will send a large packet, it is recommended that you close it
**Examples:**
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

This function is used to start web server.
For details of multithreading and blocking, see [four work methods](../workmethods.html)
>@param timeout: setting the timeout, it may not work on some development board
>
>@param backlog: the number of `TCP` connect at the same time
>
>@param blocked: set whether this method is blocked
>
>@param muti_thread: sets whether to enable multithreading
​