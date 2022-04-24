# 06 json-server 이용하기

json-server 는 Node.js 로 아직 웹 서버가 구축이 되지 않았을 때 개발을 진행할수 있도록 도와줍니다.

<br/>

## 1. REST API

- API(Application Programming Interface) : 애플리케이션을 구축하고 통합하기 위한 프로토콜 세트
- REST(Representational State Transfer) : 자원을 이름으로 구분하여 해당 자원의 상태(전송되는 데이터-JSON)를 주고 받는 모든 것을 의미합니다.
- 웹에서는 일반적으로 서버에 구현해 놓은 REST API 를 클라이언트가 호출해서 데이터 전송, 조회, 수정, 삭제 같은 기능을 서버에 요청할 수 있게 해줍니다.

<br/>
<br/>

## 2. json-server 설치

```
$ npm install -g json-server
```

<br/>
<br/>

## 3. json 파일 생성

```json
{
  "posts": [{ "id": 1, "title": "json-server", "author": "typicode" }],
  "comments": [{ "id": 1, "body": "some comment", "postId": 1 }],
  "profile": { "name": "typicode" }
}
```

<br/>
<br/>

## 4. json-server 실행

```
$ json-server --watch [json 파일명]
```

<br/>
<br/>

## 5. GET 요청

데이터 조회

```javascript
fetch("http://localhost:3000/comments") // 전체 조회
  .then((response) => response.json())
  .then((json) => console.log(json));

fetch("http://localhost:3000/comments/1") // id 로 조회
  .then((response) => response.json())
  .then((json) => console.log(json));

fetch("http://localhost:3000/comments?postId=1") // query로 postId = 1 로 조회
  .then((response) => response.json())
  .then((json) => console.log(json));
```

<br/>
<br/>

## 5. POST 요청

데이터 생성

```javascript
fetch("http://localhost:3000/posts", {
  method: "POST",
  headers: {
    "content-type": "application/json; charset=UTF-8",
  },
  body: JSON.stringify({
    title: "The Great",
    author: "Jeremy",
  }),
})
  .then((response) => response.json())
  .then((json) => console.log(json));
```

<br/>
<br/>

## 5. PUT 요청

데이터 수정

```javascript
fetch("http://localhost:3000/posts/2", {
  method: "PUT",
  headers: {
    "content-type": "application/json; charset=UTF-8",
  },
  body: JSON.stringify({
    id: 2,
    title: "The Great Jeremy",
    author: "Jeremy",
  }),
})
  .then((response) => response.json)
  .then((json) => console.log(json));
```

<br/>
<br/>

## 5. DELETE 요청

데이터 삭제

```javascript
fetch("http://localhost:3000/posts/2", {
  method: "DELETE",
});
```

<br/>
<br/>

:arrow_forward:[07 Express로 웹 서버 구축하기](./07%20Express%EB%A1%9C%20%EC%9B%B9%20%EC%84%9C%EB%B2%84%20%EA%B5%AC%EC%B6%95%ED%95%98%EA%B8%B0.md):arrow_forward:
