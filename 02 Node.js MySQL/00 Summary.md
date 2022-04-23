# Summary

```
$ npm install mysql
```

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
  con.query("CREATE DATABASE mydb", function (err, result) {
    if (err) throw err;

    console.log("Database created!");
  });
});
```

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourname",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) console.log(err);

  console.log("Connected!");

  // 데이터 베이스 생성
  var createTableSql =
    "CREATE TABLE customers (name VARCHAR(255), address VARCHAR(255))";
  con.query(createTableSql, function (err, result) {
    if (err) throw err;
    console.log("Table created!");
  });

  // 테이블 생성
  var alterTableSql =
    "ALTER TABLE customers ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY";
  con.query(alterTableSql, function (err, result) {
    if (err) throw err;
    console.log("Table altered!");
  });

  // 데이터 추가
  var InsertTableSql =
    "INSERT INTO customers (name, address) VALUES ('임채은', '대전')";
  con.query(InsertTableSql, function (err, result) {
    if (err) throw err;

    console.log(result.insertId);
    console.log(result.affectedRows);
    console.log("Table altered!");
  });

  // 데이터 조회
  var selectTableSql = "SELECT name, address FROM customers";
  con.query(selectTableSql, function (err, result) {
    if (err) throw err;

    console.log(result);
  });

  // 데이터 조건 조회
  var name = "임채은";
  var addr = "대전";
  var whereSql = "SELECT * FROM customers WHERE name = ? OR address = ?";
  // var whereTableSql = "SELECT * FROM customers WHERE address LIKE '충청%'";
  con.query(whereSql, [name, addr], function (err, result) {
    if (err) throw err;

    console.log(result);
  });

  // 데이터 정렬
  var orderBySql = "SELECT * FROM customers ORDER BY name";
  //  var orderBySql = "SELECT * FROM customers ORDER BY name DESC";
  con.query(orderBySql, function (err, result) {
    if (err) throw err;

    console.log(result);
  });

  // 데이터 삭제
  var deleteSql = "DELETE FROM customers WHERE address = '서울'";
  con.query(deleteSql, function (err, result) {
    if (err) throw err;

    console.log(result.affectedRows);
    console.log(result);
  });

  // 테이블 삭제
  var dropTableSql = "DROP TABLE IF EXISTS customers";
  con.query(dropTableSql, function (err, result) {
    if (err) throw err;

    console.log(result);
  });

  // 데이터 수정
  var updateSql =
    "UPDATE customers SET address = '대전광역시' where address = '대전'";
  con.query(updateSql, function (err, result) {
    if (err) throw err;

    console.log(result.affectedRows);
  });

  // 데이터 제한 조회
  var limitSql = "SELECT * FROM customers LIMIT 5"; // 5개 레코드 반환
  // var limitSql = "SELECT * FROM customers LIMIT 2, 5"; // 위치 3에서 시작하여 5개 레코드 반환
  con.query(limitSql, function (err, result) {
    if (err) throw err;

    console.log(result.affectedRows);
  });

  // 데이터 결합 조회
  var joinSql =
    "SELECT user.name AS user, products.name AS favorite FROM users JOIN products ON user.favorite_product = products.id ";
  con.query(limitSql, function (err, result) {
    if (err) throw err;

    console.log(result);
  });
});
```
