# 发送文件

有时候我们可能希望向浏览器发送一个文件, 我们可以使用 `response` 自带的 send_file () 方法.

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
    response.send_file ("/www/index.html")
    # 注意这里必须是完整的绝对路径.
    
app.run ()
```

