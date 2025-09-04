# Run Server
⚡️ You can run your server using Flask 



```python3
# server.py
from flask import Flask

app = Flask(__name__)


@app.route('/')
def index():
    return "Hello Flask"


app.run(debug=True)
```
