# Routing variables
In many cases, defining a dead route rule doesn't do what we want, so routing variables emerge.

## Definition
To define a routing variable, you must follow its writing rules:

```
<type:var_name>
```

Typee is optional:
- string
- float (including int)
- int
- path
- Custom (user-defined regex expression rule)

## Use
The following code demonstrates how to use routing variables:
```python
# main.py
import micro_route, network

# connect to network
WLAN = network.WLAN (network.STA_IF)
WLAN.active (True)
WLAN.connect ("SSID","PASSWD")

# set the web route
app = micro_route ()
@app.route ('/<string:goods_name>/<float:price>/<int:amount>/')
def index (context,goods_name:str, price:float, amount:int):
    total = price * amount
    return "<h1>{0} total {1}$</h1>".format (goods_name,total)

app.run ()
```

When you visit `/apple/5.2/100`, 
The browser will display:

"\<h1\>apple total 520$\</h1\>"

## string type
Define a string
For example: `apple`, `pair`...
Excluding `apple/pair`

## int type
Define an integer
For example: `100`, `50`, `125`
Not included: `100.0`, `99.5`

## float type
Define a floating point number, including integers
For example: `100', `100.23456`

## path type
Define a path **All variables after the `path` type may become invalid.**

## custom type
Cusm type is a special variable with a naming rule of `<custom=Regex:var_Name>`

This feature has not been fully tested and may cause strange errors in the program when you try to use the `custom` type.