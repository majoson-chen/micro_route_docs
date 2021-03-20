# Upload File
Sometimes browsers upload files, but they may be too large, so we have to read them manually.

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