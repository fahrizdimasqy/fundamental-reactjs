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

### Inline Style JSX
```javascript
import React from "react";
import ReactDOM from "react-dom";

const heading = {
  color:"red",
  fontSize: 50,
}

heading.color="blue";

ReactDOM.render(<h1 style={heading}>Hello World!</h1>, document.getElementById("root"));
```
digunakan untuk kebutuhan cepat atau perubahan cepat karena dibuat menggunakan objek javascript

### Practice style jsx
```javascript
import React from "react";
import ReactDOM from "react-dom";

const customColor = {
  color: "red"
};

const date = new Date();
var currentTime = date.getHours();

let greeting = "";
if (currentTime < 12) {
  greeting = "Good Morning";
  customColor.color = "red";
} else if (currentTime < 12 && currentTime > 18) {
  greeting = "Good Afternoon";
  customColor.color = "green";
} else {
  greeting = "Good Evening";
  customColor.color = "blue";
}

ReactDOM.render(
  <div>
    <h1 className="heading" style={customColor}>
      {greeting}
    </h1>
  </div>,
  document.getElementById("root")
);
```
### Import Export
bisa menggunakan nilai / apapun dari file lain
* math.js
```javascript
const pi = 3.14;

function doublePi() {
  return pi * 2;
}
function triplePi() {
  return pi * 3;
}

// hanya boleh memiliki 1 export default
export default pi;

// export lebih dari 1
// nama export harus sama dengan apa yang ingin di export
export { doublePi, triplePi };
```

* index.js
```javascript
import React from "react";
import ReactDOM from "react-dom";
// export default import bisa menggunakan nama bebas, tapi jika lebih dari 1 pastikan nama yang di import sama dengan nama export
import PI, { doublePi, triplePi } from "./math.js";

ReactDOM.render(
  <ul>
    <li>{PI}</li>
    {/* karena dobulePi sebagai function maka dipanggil menggunakan() */}
    <li>{doublePi()}</li>
    <li>{triplePi()}</li>
  </ul>,
  document.getElementById("root")
);
```
