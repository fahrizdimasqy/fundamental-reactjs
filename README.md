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

<!-- deklarasi variabel -->
const name = "fahriz";
<!-- deklarasi variabel element dengan nilai <h1> dan panggil name menggunakan {} sebagai expression -->
const element = <h1>hello, {name}</h1>;

ReactDOM.render(element, document.getElementById("root"));
```
