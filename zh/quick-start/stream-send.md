# 流式传输

有时候我们发送的请求可能不只是一个文件那么简单, 也许是从摄像头中读出的画面数据, 我们可以使用 `流(stream)` 的方式对其进行传输.

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
        ... # get data
        response.send (data)

app.run ()
```

