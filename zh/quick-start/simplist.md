# 一个最简单的路由

很多情况下我们需要处理的情况并不复杂, 因此一个最简单的响应路由即可解决问题.

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
    response = context.response
    response.send_header ()
    while True:
        ... # get the data
        response.send (data)
    
app.run ()
```



上面的代码将会自动连接wifi, 并且在浏览器访问时返回文本 **"\<h1\>Hello World!\</h1\>"**

