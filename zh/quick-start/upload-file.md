# 上传文件

有时候浏览器会上传文件, 但是这些文件可能会过大, 所以我们得手动读取文件.

```python
# main.py
import micro_route, network

# connect to network
WLAN = network.WLAN (network.STA_IF)
WLAN.active (True)
WLAN.connect ("SSID","PASSWD")

# set the web route
app = micro_route ()
@app.route ('/',method="POST",auto_recv=False)
def index (context):
    response = context.response
    with open (file_name, 'wb') as file:
        buf = response.recv_data (1024)
        while buf:
            file.write (buf)
            buf = response.recv_data (1024)

app.run ()
```