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
### Expression Vs Statement
Expression untuk menghasilkan nilai
```javascript
a = a+6; //expresi karena menghasilkan nilai dari a ditambah 6
```

```javascrpit
hasil = 5*2; //expresi karena akan menghasilkan nilai 5*2 yaitu 10 yang disimpan di variable hasil
```

Stament untuk melakukan sesuatu
```javascript
var a = 5; // untuk membuat variable bernilai 5
```
```javascript
console.log(5); // statement karena untuk menampilkan angka 5 dalam konsole
```


### Props
mengirimkan props
```javascript
<Component nama_props={value} />
```

mengakses props
> props.nama_props

```javascript
import React from "react";
import ReactDOM from "react-dom";

// parameter props untuk menerima data yang dikirimkan atribute dari custom component dalam bentuk objek
function Card(props) {
  return (
    <div>
      {/* cara memanggil data property yang dikirimkan dari custom component yang digunakan props.nama_attribute */}
      <h2>{props.name}</h2>
      <img src={props.img} alt="avatar_img" />
      <p>{props.tlp}</p>
      <p>{props.email}</p>
    </div>
  );
}

ReactDOM.render(
  <div>
    <h1>My Contacts</h1>
    {/* attribute ini dikirimkan dan d tangkap oleh parameter props */}
    <Card
      name="Beyonce"
      img="https://blackhistorywall.files.wordpress.com/2010/02/picture-device-independent-bitmap-119.jpg"
      tlp="+123 456 789"
      email="b@beyonce.com"
    />
    <Card
      name="Jack Bauer"
      img="https://pbs.twimg.com/profile_images/625247595825246208/X3XLea04_400x400.jpg"
      tlp="987 654 321"
      email="jack@nowhere.com"
    />
  </div>,
  document.getElementById("root")
);
```
### Maping data ke component
format Maping

> nama_variabel/array.map(fungsi_yang_di_mapping)

pertama buat component terlebih dahulu jangan lupa gunakan props sebagai parameter untuk bisa menangkap datanya
* Entry.jsx
```javascript
import React from "react";
function Entry(props) {
  return (
    <div className="term">
      <dt>
        <span className="emoji" role="img" aria-label="Tense Biceps">
          {props.emoji}
        </span>
        <span>{props.name}</span>
      </dt>
      <dd>{props.meaning}.</dd>
    </div>
  );
}
export default Entry;
```
* Export data dummy
```javascript
const emojipedia = [
  {
    id: 1,
    emoji: "💪",
    name: "Tense Biceps",
    meaning:
      "“You can do that!” or “I feel strong!” Arm with tense biceps. Also used in connection with doing sports, e.g. at the gym."
  },
  {
    id: 2,
    emoji: "🙏",
    name: "Person With Folded Hands",
    meaning:
      "Two hands pressed together. Is currently very introverted, saying a prayer, or hoping for enlightenment. Is also used as a “high five” or to say thank you."
  },
  {
    id: 3,
    emoji: "🤣",
    name: "Rolling On The Floor, Laughing",
    meaning:
      "This is funny! A smiley face, rolling on the floor, laughing. The face is laughing boundlessly. The emoji version of “rofl“. Stands for „rolling on the floor, laughing“."
  }
];

export default emojipedia;
```
lalu buat sebuah function untuk di maping yang berisi component yang ingin di maping
* App.jsx
```javascript
import React from "react";
import Entry from "./Entry";
import emojipedia from "../emojipedia";


//fungsi createEntry dengan parameter emojiItem yang dimana parameter ini digunakan untuk menangkap datanya
function createEntry(emojiItem) {
  return (
  //panggil Component Entry dan beri props untuk dikirimkan
    <Entry
      key={emojiItem.id}
      emoji={emojiItem.emoji}
      name={emojiItem.name}
      meaning={emojiItem.meaning}
    />
  );
}

function App() {
  return (
    <div>
      <h1>
        <span>Emojipedia</span>
      </h1>
     //maping data emojipedia ke fungsi createEntry yang berisi component Entry
      <dl className="dictionary">{emojipedia.map(createEntry)}</dl>
    </div>
  );
}
export default App;
```

### Map, Reduce, Filtet, Find and FindIndex

Map -Create a new array by doing something with each item in an array.
```javascript
var numbers = [3, 56, 2, 48, 5];
function double(x) {
   return x * 2;
}
const newNumbers = numbers.map(double);

var newNumbers = [];
  numbers.forEach(function (x) {
  newNumbers.push(x * 2);
});

const newNumbers = numbers.map(function (x) {
    return x * 2;
});

// console.log(newNumbers);
```

Filter - Create a new array by keeping the items that return true.
```javascript
 const newNumbers = numbers.filter(function(num) {
  return num < 10;
});
```


Reduce - Accumulate a value by doing something to each item in an array.
```javascript
var newNumber = numbers.reduce(function (accumulator, currentNumber) {
   console.log("accumulator = " + accumulator);
   console.log("currentNumber = " + currentNumber);
    return accumulator + currentNumber;
})
console.log(newNumber);
```

Find - find the first item that matches from an array.

```javascript
const newNumber = numbers.find(function (num) {
   return num > 10;
})
// console.log(newNumber);
```
FindIndex - find the index of the first item that matches.
```javascript
const newNumber = numbers.findIndex(function (num) {
   return num > 10;
 })

console.log(newNumber);
```
### Arow Function
> variabel = (parameter) => statement;

jika memiliki 1 parameter dan 1 statement bisa d hapus kurungnya() dan kurung {}

> variabel = (parameter) => statement;

jika memiliki lebih dari 1 parameter dan lebih dari 1 statement
```javascript
variabel = (parameter1, paramter2) => {
  
  if(parameter1 == parameter2 ) {
    return parameter1 * parameter2;
  } else {
    return "wrong";
  }
}
;
```

### Ternary Operator

```javascript
condition ? benar : salah;
```
contoh:
```javascript
const x = 80;
x > 75 ? "lulus" : "tidak lulus";
```

### And Operator
and operator di javascript
```javascript
(expression && expression)
```
contoh:
```javascript
var x = 5;
(x > 5 && x < 7);
// x > 5 = true dan x < = true maka nilai keseluruhan expresi adalah true
```
sekarnag jika x nilainya adalah 1
```javascript
var x = 1;
(x > 5 && x < 7);
// x > 5 = false karena nilainya sudah false maka expresi selanjutnya tidak akan di cek karena salah satu nilainya sudah false
```

AND Operator di React
```javascript
condition && expression
//sisi kiri adalah kondisi dan di sisi kanan adalah expresion  yang akan di evaluasi selama kondisinya benar
true && expression
//tapi jika kondisinya salah maka sisi kanan tidak akan di evaluasi
false && expression
```
contoh:
```javascript
const currentTime = 18;
currenTime > 12 && <h1> kenapa kamu masih bekerja? </h1>
// akan menghasilkan kenapa kamu masih bekerja?
// jika currentTime tidak memenuhi kondisi maka sisi kanan tidka akan di cek
// biasanya ini digunakan hanya untuk memeriksa 1 kondisi
```

### State
State adalah sebuah object untuk menyimpan data pada React dan akan di render atau muat ulang ketika data mengalami perubahan.
biasanya digunakan untuk perubahan antarmuka tetapi perubahan itu bergantung pada nilai variabel itu

