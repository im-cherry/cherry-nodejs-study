# 12 Join

## 1. Join Two ro More Tables

`JOIN` 문을 사용하여 둘 이상의 테이블 사이의 관련 열을 기반으로 행을 결합할 수 있습니다.

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
  var sql =
    "SELECT users.name AS user, products.name AS favorite FROM users JOIN products ON users.favorite_product = products.id";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

## 2. Left Join

선호하는 제품이 있든 없든 모든 사용자를 반환하려면 `LEFT JOIN` 문을 사용합니다.

```mysql
SELECT users.name AS user,
products.name AS favorite
FROM users
LEFT JOIN products ON users.favorite_product = products.id
```

<br />
<br />

## 2. Right Join

모든 제품과 해당 제품을 즐겨찾기로 갖고 있는 사용자를 반환하려면 사용자가 즐겨찾기로 갖고 있지 않더라도 `RIGHT JOIN` 문을 사용합니다.

```mysql
SELECT users.name AS user,
products.name AS favorite
FROM users
RIGHT JOIN products ON users.favorite_product = products.id
```

<br />
<br />
