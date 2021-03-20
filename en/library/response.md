# Response
This document introduces the built-in objects and methods of the `Response` object


## Properties

### dict: headers

This dictionary is used to store the `headers` data that will be sent. You can modify this object directly.

### Socket.socket: client
This object is used to store the `socket` object from which the browser originated the request, and you can call the methods directly to implement your own functions.

About `Socket.socket`'s more  information, [see here](Http://docs.micropython.org/en/latest/library/usocket.html#methods)


### str: mime_Type
This object is used to set the `MIME` type of the corresponding content. You can set this object directly, `micro_Route` will automatically add this object when sending a message.

Default to `text/html`.

To use the built-in `MIME'dictionary, see [consts - MIME_TYPES_MAP](./consts.html#dict-mimetypesmap-)

### str: statu_Code
This object is used to set the corresponding `HTTP status Code` to the browser. You can set this property manually and then `micro_Route` will automatically use this status code in response.

## Methods

### func: send_header (
### 	statu_explane:str = None,
### 	content:str = ""
### )
This method is used to send HTTP messages to the browser, which can send data to the browser after.

If the send fails, a `TimeoutError` will be raised.

By setting `statu_Code` property to set the corresponding `HTTP` status code
> @param statu_explane: The interpretation of this `HTTP` status code, If None, we'll use the built-in explanation dictionary if left blank for the interpretation of this `HTTP`status code
>
> @param content: Send body content, leave blank to send only `HTTP` message

### func: send (content:[str,bytes])
This function will send body content to the browser if you have not called `send_Header`, this method will be called once automatically.

You can call send () multiple times in processing routes to send data for streaming purposes.

If the send fails, a `TimeoutError` will be raised
> @param content: what str|bytes wants to send
>
> @return: None

### func: redirect (
### 	location:str, 
### 	statu_code:str="302"
### )

This method sends a redirected request to the browser. When this request is sent, the data you return will be invalidated.
> @param statu_code: Status code to use. 302: Temporary orientation 301: Permanent orientation
>
> @return: None

### func: close ()
This method will close the connection with the client.
> @return: None

### func: abort (

### 	statu_code:str=500, 

### 	content:str="", 

### 	statu_explane=None

### )

This method will interrupt the request between the client and you, usually when the server does not want to process the request or when the client accesses data that should not be accessed.
> @param statu_code: str, `HTTP status Code` returned on interrupt, default to 500
>
> @param content: str, leave blank the body you want to return. This parameter is used to customize the error interface
>
> @param statu_explane: str, used to replace the default `HTTP Status Code Interpretation Text` Same as above `send_Header ()`

### func: send_file (path:str)
Send a local file.
> @param path: please pass a absolute path, if your file is located at /www/Index.html, Then it is recommended that you fill in "/www/Index.html"
>
> @return None