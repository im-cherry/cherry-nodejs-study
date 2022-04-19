# 09 Events

## 1. Events in Node.js

컴퓨터의 모든 작업은 이벤트입니다. 연결이 이루어지거나 파일이 열릴때와 같습니다.  
Node.js 의 객체는 파일을 열고 닫을 때 readStream 객체가 이벤트를 발생시키는 것처럼 이벤트를 발생시킬 수 있습니다.

```javascript
var fs = require("fs");
var rs = fs.createReadStream("./demofile.txt");
rs.on("open", function () {
  console.log("The file is open.");
});
```

<br />
<br />

## 2. Events Module

Node.js 에는 `event` 라고 하는 내장 모듈이 있습니다.  
여기에서 자신의 이벤트를 생성, 실행 및 수신할 수 있습니다.  
이벤트 속성과 메서드에 액세스 하려면 `EventEmitter` 객체를 만들어야 합니다.

```javascript
var events = require("events");
var eventEmitter = new events.EventEmitter();
```

<br />
<br />

## 3. The EventEmitter Object

EventEmitter 객체를 사용하여 고유한 이벤트에 이벤트 핸들러를 할당할 수 있습니다.  
이벤트를 발생시키려면 `emit()` 메소드를 사용하세요.

```javascript
var events = require("events");
var eventEmitter = new events.EventEmitter();

var myEventHandler = function () {
  console.log("I hear a scream!");
};

eventEmitter.on("scream", myEventHandler); // scream 이벤트가 발생했을 때, 이벤트 핸들러 할당
eventEmitter.emit("scream");
```

<br />
<br />

:arrow_forward:[10 Upload Files](./10%20Upload%20Files.md) :arrow_forward:
