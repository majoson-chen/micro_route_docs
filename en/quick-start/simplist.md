# One of the easiest routes
In many cases, the situation we need to deal with is not complex, so the simplest response route can solve the problem.
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
    """<h1>hello world!</h1>"""
    
app.run ()
```

The above code will automatically connect to WiFi and return the text **"\<h1\>Hello World!\</h1\>"** when the browser accesses it.

