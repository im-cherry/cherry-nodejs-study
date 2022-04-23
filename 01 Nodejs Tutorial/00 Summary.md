# Summary

```
$ node 파일명.js
```

```javascript
var http = require("http");
var url = require("url");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });

    var query = url.parse(req.url, true).query;
    var text = query.year + " " + query.month;

    res.write(req.url);
    res.write(query);
    res.write(text);
    res.end();
  })
  .listen(8080);
```

```javascript
var http = require("http");
var fs = require("fs");

http.createServer(function (req, res) {
  fs.readFile("index.html", function (err, data) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write(data);
    return res.end();
  });
});
```

```javascript
var events = require("events");
var eventEmitter = new events.EventEmitter();

var myEventHandler = function () {
  console.log("I hear a scream!");
};

eventEmitter.on("scream", myEventHandler);
eventEmitter.emit("scream");
```

<br />
<br />
