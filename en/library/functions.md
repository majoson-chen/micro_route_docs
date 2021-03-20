#Function

This page provides some auxiliary functions defined in `micro_route` may help developer's develop

### func: debug_info (level:int ,*args)
This function is used to print some debugging information
>@param level: used to set the print level, for more details, [see here](./CONSTS.html/#int-debug-)
>
> @return : None
```python
micro_route.debug_info(3, "Hello " , "World")
>>> "Hello World"
```

### func: make_path (paths:list)
Merge a list filled with `str` obj into a URL
>@param paths: a list of STRs, for example: ["hello", "world"]
>
>@return: list
```python
paths = ["hello" , "world"]
micro_route.make_path (paths)
>>> "/hello/world"
```

### func: split_url (url:str)
Split `url` into a 'list`
>@param url: URL to be split
>
>@return: list
```python
micro_route.split_url ("/")
>>> []

micro_route.split_url ('/hello/world')
>>>  ['hello', 'world']

micro_route.split_url ('/hello/world/')
>>> ['hello', 'world']

micro_route.split_url ('hello/world/')
>>> ['hello', 'world']
```

### func: parse_url (url:str)
This method will normalize the incoming `url` text
>@param url: the URL to be normalized
>
>@return: str
```python
micro_route.parse_url ("hello/world")
>>> "/hello/world"
```

### escape_ chars ( string:str )
This method will escape the special string in the incoming `string` to a normal string
>@param string: the string to escape
>
>@return: str
**Examples**
```python
escape_chars ("Hello&nbspWorld")
>>> "Hello World"
```

### func: load_form_data (data:str)
This method parses the `form` string data of `HTML` into a `Python` dictionary object, which is usually used to parse `post` data
> @param data: str|bytes
>
> @return : dict
**Examples**
```python
micro_route.dump_form_data ("user_name=123&passwd=456")
>>> {
    "user_name" : "123",
    "passwd"    : "456"
}
```