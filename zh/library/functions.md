# 函数

本页提供 `micro_route` 中所定义的一些辅助函数, 这些辅助函数也许可以帮助开发者开发

### func: debug_info (level:int,*args)

​	本函数用来打印一些调试信息

> @param level: 用来设置打印信息的级别. 关于级别的详细信息, [见此](./CONSTS.html/#int-debug-)
>
> @return : None

```python
micro_route.debug_info(3, "Hello " , "World")
>>> "Hello World"
```



### func: make_path (paths:list)

​	把一个 `str` 的 `list` 合并在一起, 变成一个 url.

> @param paths: 一个 str 的 list, 例如 : ["hello", "world"]
>
> @return: list

```python
paths = ["hello" , "world"]
micro_route.make_path (paths)
>>> "/hello/world"
```



### func: split_url (url:str)

​	把 `url` 分级分割成一个 `list`

> @param url: 欲分割的url
>
> @return: list

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

​	本方法将会将传入的 `url` 文本规范化

> @param url: 欲规范化的url
>
> @ return: str

```python
micro_route.parse_url ("hello/world")
>>> "/hello/world"
```



### escape_chars (string:str)

​	本方法将会对传入的 `string` 中的特殊特殊字符串转义成普通字符串.

> @param string: 欲转义的字符串
>
> @return: str

​	**例子**

```python
escape_chars ("Hello&nbspWorld")
>>> "Hello World"
```



### func: load_form_data (data:str)

​	本方法将会 `HTML` 的 `form` 表单字符串数据解析为 `Python` 的字典对象, 通常用来解析 `POST` 的数据

> @param data: str|bytes
>
> @return : dict

​	**例子**

```python
micro_route.dump_form_data ("user_name=123&passwd=456")
>>> {
    "user_name" : "123",
    "passwd"    : "456"
}
```

