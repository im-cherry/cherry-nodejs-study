# 04 Nodejs 시작하기

## 1. Node.js 에서 자바스크립트 파일 실행하기

```
$ node [자바스크립트 파일명]
```

<br/>
<br/>

## 2. 모듈(Module)

모듈은 분리된 각각의 자바스크립트 파일이고 각 파일은 특정한 목적을 가진 여러 개의 함수와 변수의 집합입니다.

- calculator.js

```javascript
const defaultNum = 1;

function add(num1, num2) {
  return num1 + num2;
}

function minus(num1, num2) {
  return num1 - num2;
}

module.exports = {
  defaultNum,
  add,
  minus,
};
```

- module.js

```javascript
const { add, minus, defaultNum } = require("./calculator");

console.log(add(7, 2));
console.log(minus(7, 2));
console.log(defaultNum);
```

<br/>
<br/>

:arrow_forward:[05 Nodejs 내장 모듈과 객체](./05%20Nodejs%20%EB%82%B4%EC%9E%A5%20%EB%AA%A8%EB%93%88%EA%B3%BC%20%EA%B0%9D%EC%B2%B4.md):arrow_forward:
