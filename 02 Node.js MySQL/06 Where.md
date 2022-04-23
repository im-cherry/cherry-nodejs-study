# 06 Where

## 1. Select With a Filter

테이블에서 레코드를 선택할 때 `WHERE` 문을 사용하여 선택을 필터링 할 수 있습다.

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
    "SELECT * FROM customers WHERE address = 'Par Lane 38'",
    function (err, result) {
      if (err) throw err;
      console.log(result);
    }
  );
});
```

<br />
<br />

## 2. Wildcard Characters

주어진 문자나 구로 시작하거나 포함하거나 끝나는 레코드를 선택할 수도 있습니다.
`%` 를 사용하여 0개, 1개 또는 여러 문자를 나타냅니다.

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
    "SELECT * FROM customers WHERE address LIKE 'S%'",
    function (err, result) {
      if (err) throw err;
      console.log(result);
    }
  );
});
```

<br />
<br />

## 3. Escaping Query Values

쿼리 값이 사용자가 제공한 변수인 경우 값을 이스케이프해야합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "myusername",
  password: "mypassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  var name = "Amy";
  var addr = "Mountain 21";
  var sql = "SELECT * FROM customers WHERE address = ? OR name = ?";
  con.query(sql, [name, addr], function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

:arrow_forward:[07 Order By](./07%20Order%20By.md):arrow_forward:
