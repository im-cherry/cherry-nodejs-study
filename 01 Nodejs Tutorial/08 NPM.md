# 08 NPM

## 1. What is NPM?

NPM은 Node.js 패키지 또는 모듈용 패키지 관리자입니다.

<br />
<br />

## 2. What is a Package?

Node.js 의 패키지에는 모듈에 필요한 모든 파일이 포함되어 있습니다.  
모듈은 프로젝트에 포함할 수 있는 JavaScript 라이브러리입니다.

<br />
<br />

## 3. Download a Package

```
npm install upper-case  // uppser-case 패키지 다운로드
```

<br />
<br />

## 4. Using a Package

- demo_uppercase.js

  ```javascript
  var http = require("http");
  var uc = require("upper-case");
  http
    .createServer(function (req, res) {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(uc.upperCase("Hello World!"));
      res.end();
    })
    .listen(8080);
  ```

```
node demo_uppercase.js
```

<br />
<br />

:arrow_forward:[09 Events](./09%20Events.md) :arrow_forward:
