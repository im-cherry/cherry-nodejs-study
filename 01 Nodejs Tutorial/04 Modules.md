# 04 Modules

## 1. What is a Module in Node.js?

모듈은 JavaScript 라이브러리와 동일하다고 생각하세요.  
응용 프로그램에 포함하는 기능의 집합입니다.

<br/>
<br/>

## 2. Built-in Modules (내장 모듈)

Node.js 에는 추가 설치 없이 사용할 수 있는 [내장 모듈들](https://www.w3schools.com/nodejs/ref_modules.asp)이 있습니다.

<br/>
<br/>

## 3. Include Modules

모듈을 포함하려면 `require()` 함수를 사용하세요.

```javascript
var http = require("http");
```

애플리케이션이 HTTP 모듈에 액세스할 수 있으며 서버를 생성할 수 있습니다.

```javascript
http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.end("Hello World!");
  })
  .listen(8080);
```

<br/>
<br/>

## 4. Create Your Own Modules

고유한 모듈을 만들고 애플리케이션에 쉽게 포함할 수 있습니다.  
아래 예시는 날짜 및 시간 개체를 반환하는 모듈을 만듭니다.

- myfirstmodule.js
  ```javascript
  exports.myDateTime = function () {
    return Date();
  };
  ```

`exports` 를 사용하여 모듈 파일 외부에서 속성과 메서드를 사용할 수 있도록 합니다.

<br/>
<br/>

## 5. Include Your Own Module

모든 Node.js 파일에 모듈을 포함하고 사용할 수 있습니다.

- demo_module.js

```javascript
var http = require("http");
var dt = require("./myfirstmodule");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write("The date and time are currently: " + dt.myDateTime());
    res.end();
  })
  .listen(8080);
```

```
$ node demo_module.js
```

<br/>
<br/>

:arrow_forward:[05 HTTP Module](./05%20HTTP%20Module.md) :arrow_forward:
