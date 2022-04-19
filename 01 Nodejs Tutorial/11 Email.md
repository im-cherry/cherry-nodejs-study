# 11 Email

## 1. The Nodemiler Module

`Nodeemailer` 모듈을 사용하면 컴퓨터에서 이메일을 쉽게 보낼 수 있습니다.

```
$ npm install nodemailer
```

```javascript
var nodemailer = require("nodemailer");
```

<br />
<br />

## 2. Send an Email

선택한 이메일의 사용자 이름과 비밀번호를 사용하여 이메일을 보냅니다.

```javascript
var nodemailer = require("nodemailer");

var transporter = nodemailer.createTransport({
  service: "gmail",
  auth: {
    user: "youremail@gmail.com",
    pass: "yourpassword",
  },
});

var mailOptions = {
  from: "youremail@gmail.com",
  to: "myfriend@yahoo.com",
  subject: "Sending Email using Node.js",
  text: "That was easy!",
};

transporter.sendMail(mailOptions, function (err, info) {
  if (err) {
    console.log(err);
  } else {
    console.log("Email sent: " + info.response);
  }
});
```

<br />
<br />

## 3. Multiple Receivers

두 명 이상의 수신자에게 이메일을 보내려면 쉼표를 구분하여 emailOptions 객체의 `to` 속성에 추가합니다.

```javascript
var mailOptions = {
  from: "youremail@gmail.com",
  to: "myfriend@yahoo.com, myotherfriend@yahoo.com",
  subject: "Sending Email using Node.js",
  text: "That was easy!",
};
```

<br />
<br />

## 4. Send HTML

이메일에 HTML 형식의 텍스트를 보내려면 `text` 속성 대신 `html` 속성을 사용합니다.

```javascript
var mailOptions = {
  from: "youremail@gmail.com",
  to: "myfriend@yahoo.com",
  subject: "Sending Email using Node.js",
  html: "<h1>Welcome</h1><p>That was easy!</p>",
};
```

<br />
<br />
