# 05 Select From

## 1. Selecting From a Table

MySQL의 테이블에서 데이터를 선택하려면 `SELECT` 문을 사용합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  con.query("SELECT * FROM customers", function (err, result, fields) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

## 2. Selecting Columns

테이블의 일부 열만 선택하려면 `SELECT` 문 다음에 열 이름을 사용합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  con.query(
    "SELECT name, address FROM customers",
    function (err, result, fields) {
      if (err) throw err;
      console.log(result);
    }
  );
});
```

<br />
<br />

## 3. The Result Object

result 객체는 각 행을 객체로 포함하는 배열입니다.  
만약 세번째 레코드의 address 를 반환하기 위해서는 `console.log(result[2].address)` 를 사용합니다.

<br />
<br />

## 4. The Fields Object

콜백 함수의 세번째 매개변수 fields 는 각 필드에 대한 정보를 포함하는 배열입니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  con.query(
    "SELECT name, address FROM customers",
    function (err, result, fields) {
      if (err) throw err;
      console.log(fields);
      console.log(fields[1].name); // 두 번째 필드의 name 을 반환
    }
  );
});
```

<br />
<br />

:arrow_forward:[06 Where](./06%20Where.md):arrow_forward:
