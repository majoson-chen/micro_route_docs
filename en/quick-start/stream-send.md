# Streaming
Sometimes we send requests that are not just a file, but also picture data read from a camera. So we can use the stream way to send it.
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