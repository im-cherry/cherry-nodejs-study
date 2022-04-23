# 07 URL Module

## 1. The Built-in URL Module

- URL 모듈은 웹 주소를 읽을 수 있는 부분으로 분할합니다.

  ```javascript
  var url = require("url");
  ```

- `url.parse()` 메서드는 주소를 구분 분석하여 속성으로 포함된 URL 개체가 반환됩니다.

  ```javascript
  var url = require("url");
  var adr = "http://localhost:8080/default.htm?year=2017&month=february";
  var q = url.parse(adr, true);

  console.log(q.host); // localhost:8080
  console.log(q.pathname); // default.htm
  console.log(q.search); // ?year=2017&month=february

  var qdata = q.query;
  console.log(qdata.month); // february
  ```

<br/>
<br/>

## 2. Node.js File Server

요청된 파일을 열고 콘텐츠를 클라이언트에 반환하도록 하겠습니다.

- summer.html

  ```html
  <!DOCTYPE html>
  <html>
    <body>
      <h1>Summer</h1>
      <p>I love the sun!</p>
    </body>
  </html>
  ```

- winter.html

  ```html
  <!DOCTYPE html>
  <html>
    <body>
      <h1>Winter</h1>
      <p>I love the snow!</p>
    </body>
  </html>
  ```

```javascript
var http = require("http");
var url = require("url");
var fs = require("fs");

http
  .createServer(function (req, res) {
    var q = url.parse(req.url, true);
    var filename = "." + q.pathname;
    fs.readFile(filename, function (err, data) {
      if (err) {
        res.writeHead(404, { "Content-Type": "text/html" });
        return res.end("404 Not Found");
      }
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(data);
      return res.end();
    });
  })
  .listen(8080);
```

<br/>
<br/>

:arrow_forward:[08 NPM](./08%20NPM.md) :arrow_forward:
