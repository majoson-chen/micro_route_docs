# Send Files

Sometimes we might want to send a file to our browser, so we can use the `send_file ()` method that comes with `response`.
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