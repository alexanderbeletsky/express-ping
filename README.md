express-health
==============

Let your express applications **expose a simple API to inform about its internal status** to both operators and to other applications. This module was created as an express middleware to simplify its usage.

Usage
-----

* Add "express-health" to your package.json dependencies (```npm install express-health --save```)
* Include the middleware in your express application:

```javascript
var health = require('express-health');
var express = require('express');

var app = express();
...
app.use(health.ping); // this is the only addition
app.use(app.router);
...

app.listen(3000);
```

Once you launch your express application, it will add a new **/ping** endpoint to check the app status. If you **GET http://localhost:3000/ping** you will receive the following information:

```json
{
  "timestamp": 1389004812756,
  "uptime": 2187,
  "memory": {
    "rss": 21147648,
    "heapTotal": 11344896,
    "heapUsed": 4341552
  },
  "versions": {
    "http_parser": "1.0",
    "node": "0.10.22",
    "v8": "3.14.5.9",
    "ares": "1.9.0-DEV",
    "uv": "0.10.19",
    "zlib": "1.2.3",
    "modules": "11",
    "openssl": "1.0.1e"
  },
  "title": "node",
  "arch": "x64",
  "platform": "darwin",
  "argv": [
    "node",
    "/Users/guido/express-health/examples/server.js"
  ],
  "application": {
    "name": "express-health",
    "version": "0.2.0"
  }
}
```

TODO
----

* Include CPU usage.
* Include [OS information](http://nodejs.org/api/os.html).
* Debate around the JSON organization (contributions are welcome).

License
-------

MIT
