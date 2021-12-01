# fundamental-reactjs
### introduction JSX
```javascript
// fitur es6 untuk memanggil modul
import React from "react"; //memiliki babel babel = kompiler untuk konversi javascript ke versi javascrpit standar
import ReactDOM from "react-dom";

ReactDOM.render(
  // agar dapat memasukan banyak element harus di bunkus oleh 1 element sebagai parent
  <div>
    <h1>Hello Wold!</h1>
    <p>this is paragraph</p>
  </div>,
  document.querySelector("#root")
);
```
### Javascript Expressions in JSX
```javascript
import React from "react";
import ReactDOM from "react-dom";

// deklarasi variabel
const name = "fahriz";
// deklarasi variabel element dengan nilai <h1> dan panggil name menggunakan {} sebagai expression -->
const element = <h1>hello, {name}</h1>;

ReactDOM.render(element, document.getElementById("root"));
```

### Expression Vs Statement
* Expression
Di evaluasi akan di evaluasi untuk sebuah nilai, atau setelah kodenya selesai di eksekusi akan menghasilkan nilai
```javascript
{3 + 5}
// akan di evaluasi menghasilkan nilai yaitu 8
```

* Statement
```javascript
if (name === "Fahriz") { // statement
console.log("Im fahriz");
else {
  console.log("im not fahriz")
}
```
Statement meminta komputer untuk melakukan beberapa pekerjaan untuk mengevaluasi diatas yaitu name === fahriz 
dan kemudian tergantung statement itu menghasilkan sesuatu.

### Template Literal
Fitur es6 untuk menginjeksi string kedalam javascript
format code
> ```javascript
> {`${expression}`}
> ```

```javascript
import React from "react";
import ReactDOM from "react-dom";

const firstName = "Fahriz";
const lastName = "Dimas";
const luckyNumber = 16;

ReactDOM.render(
  <div>
    <h1>Hello {`${firstName} ${lastName}</h1>
    <p>your lucky number is {luckyNumber}</p>
  </div>,
  document.getElementById("root")
);
```

### Practice Expression in JSX
```javascript
import React from "react";
import ReactDOM from "react-dom";

const name = "Angela";
const currentDate = new Date();
const year = currentDate.getFullYear(); //memanggil tahun saat ini

ReactDOM.render(
  <div>
    <p>Created by {name}</p>
    <p>Copyright {year}</p>
  </div>,
  document.getElementById("root")
);
```
