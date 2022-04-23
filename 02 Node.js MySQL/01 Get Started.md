# 01 Get Started

## 1. MySQL Database

[MySQL 공식 홈페이지](https://www.mysql.com/downloads/) 에서 MySQL 데이터베이스를 다운로드 합니다.

<br />
<br />

## 2. Install MySQL Driver

컴퓨터에서 MySQL을 실행하고 나면 Nodejs를 사용하여 MySQL에 액세스할 수 있습니다.  
Nodejs로 MySQL 데이터베이스에 액세스하려면 MySQL 드라이버가 필요합니다.

```
$ npm install mysql
```

```javascript
var mysql = require("mysql");
```

<br />
<br />

## 3. Create Connection.md

데이터베이스에 대한 연결을 생성하여 시작합니다.  
MySQL 데이터베이스의 사용자 이름과 비밀번호를 사용합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourname",
  password: "yourpassword",
});

con.connect(function (err) {
  if (err) throw err;

  console.log("Connected!");
});
```

<br />
<br />

## 4. Query a Database

SQL 문을 사용하여 MySQL 데이터베이스에서 읽거나 씁니다.(쿼리)  
`query` 메서드는 sql문을 매개 변수로 사용하여 결과를 반환합니다.

```javascript
con.connect(function(err) {
    if(err) throe err;

    console.log("Connected!");
    con.query(/* sql */, function(err, result) {
        if(err) throw err;
        console.log("Result: " + result)
    })
})
```

<br />
<br />

:arrow_forward:[02 CreateDatabase](./02%20Create%20Database.md):arrow_forward:
