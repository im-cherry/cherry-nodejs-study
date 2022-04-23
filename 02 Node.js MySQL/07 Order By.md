# 07 Order By

## 1. Sort the Result

`ORDER BY` 문을 사용하여 결과를 오름차순(default) 또는 내림차순으로 정렬합니다.

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
  con.query("SELECT * FROM customers ORDER BY name", function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

## 2. ORDER BY DESC

`DESC` 키워드를 사용하여 결과를 내림차순으로 정렬합니다.

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
    "SELECT * FROM customers ORDER BY name DESC",
    function (err, result) {
      if (err) throw err;
      console.log(result);
    }
  );
});
```

<br />
<br />

:arrow_forward:[08 Delete](./08%20Delete.md):arrow_forward:
