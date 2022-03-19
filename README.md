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

#### Declarative Programming
Antar pengguna akan terlihat dibawah kondisi yang berbeda tergantung dari state.
Deklarative berfokus pada apa yang harus dicapai oleh program tanpa menjabarkan step by stepnya(functional programming);
```javascript
const products = [
 {id:1, name:'buku', qty:7, price:7000},
 {id:2, name:'pensil', qty:2, price:4000},
 {id:3, name:'rautan', qty:1, price:2000},
 {id:4, name:'bulpoin', qty:10, price:2000},
 {id:5, name:'penggaris', qty:2, price:2000},
]
/* Declarative Pattern */
function isRestock(qty) {
 return qty < 5
}
const restock = products.filter((item)=> {
 return isRestock(item.qty)
})
console.log(restock)
/*
[
 { id: 2, name: 'pensil', qty: 2, price: 4000 },
 { id: 3, name: 'rautan', qty: 1, price: 2000 },
 { id: 5, name: 'penggaris', qty: 2, price: 2000 }
]
*/
```
Berbeda dengan kode sebelumnya, pada kode di atas, mula-mula dideklarasikan ketentuan restock jika
qty kurang dari lima melalui fungsi isRestock.
Kemudian dengan menggunakan fungsi filter dipangillah fungsi isRestock pada tiap iterasinya, maka
item yang terpenuhi kemudian akan dikembalikan dan disimpan dalam variabel restock.
Nah, pendekatan kedua inilah declarative pattern. Functional programming itu sebisa mungkin
menggunakan declarative pattern.

```javascript
import React from "react";

var isDone = false;

const strikeStyle = {
  textDecoration: "line-through"
};

function App() {
  return (
    <div>
      <p style={isDone ? strikeStyle : null}>Buy milk</p>
    </div>
  );
}

export default App;
```

### Imperative Programming
```javascript
const products = [
 {id:1, name:'buku', qty:7, price:7000},
 {id:2, name:'pensil', qty:2, price:4000},
 {id:3, name:'rautan', qty:1, price:2000},
 {id:4, name:'bulpoin', qty:10, price:2000},
 {id:5, name:'penggaris', qty:2, price:2000},
]
/* Imperative Pattern */
let restock = []
for (let i = 0; i < products.length; i++) {
 if (products[i].qty < 5) {
 restock.push(products[i])
 }
}
console.log(restock)
/*
[
 { id: 2, name: 'pensil', qty: 2, price: 4000 },
 { id: 3, name: 'rautan', qty: 1, price: 2000 },
 { id: 5, name: 'penggaris', qty: 2, price: 2000 }
]
*/
```
Kode diatas,
* pertama kali disiapkan variabel restok dengan nilai array kosong,
* lalu dengan menggunakan perulangan for,
* iterasi dilakukan berdasarkan panjang arraynya,
* diawali dengan definisi variabel i bernilai 0 sebagai index pertama,
* kemudian dilakukan pengecekan apakah nilai dari variabel i lebih kecil dari panjang array,
* kemudian pada setiap iterasinya nilai i ditambah dengan 1 atau increment
* kemudian masih pada iterasi tersebut dilakukan pengecekan apakah key qty pada item dengan index
* itu nilainya kurang dari tiga atau tidak,
* jika kurang dari tiga maka item tersebut dimasukkan ke dalam variabel restock

### Destructuring assignment 
Destructuring assignment merupakan fitur Javascript yang berfungsi memecah item atau properti dari
sebuah array atau objek ke dalam variabel yang berbeda.
### Array Destructuring 
Sebagai contoh, kita akan memecah setiap items pada array menjadi sebuah variabel tersendiri
biasa:
```javascript
const colors = ['merah', 'kuning', 'hijau']
// cara biasa
let satu = colors[0]
let dua = colors[1]
let tiga = colors[2]
console.log(satu) // merah
console.log(dua) // kuning
console.log(tiga) // hijau
```
array destructuring
```javascript
const colors = ['merah', 'kuning', 'hijau']
// array destructuring
let [satu, dua, tiga] = colors
console.log(satu) // merah
console.log(dua) // kuning
console.log(tiga) // hijau
```
#### Object Destructuring
```javascript
const user = {
 name: 'Melodi',
 gender: 0,
 age: 24
}
// object destructuring
let { name, gender, age } = user
console.log(name) // Melodi
console.log(gender) // 0
console.log(age) // 24
```

### Practice Destructuring
```javascript
const cars = [
  {
    model: "Honda Civic",
    //The top colour refers to the first item in the array below:
    //i.e. hondaTopColour = "black"
    coloursByPopularity: ["black", "silver"],
    speedStats: {
      topSpeed: 140,
      zeroToSixty: 8.5
    }
  },
  {
    model: "Tesla Model 3",
    coloursByPopularity: ["red", "white"],
    speedStats: {
      topSpeed: 150,
      zeroToSixty: 3.2
    }
  }
];

export default cars;

```

```javascript
// CHALLENGE: uncomment the code below and see the car stats rendered
import React from "react";
import ReactDOM from "react-dom";
import cars from "./practice";

const [tesla, honda] = cars;
const {
  model,
  coloursByPopularity: [teslaTopColour],
  speedStats: { topSpeed: teslaTopSpeed }
} = tesla;
const {
  speedStats: { topSpeed: hondaTopSpeed },
  coloursByPopularity: [hondaTopColour]
} = honda;

console.log(tesla.topSpeed);
ReactDOM.render(
  <table>
    <tr>
      <th>Brand</th>
      <th>Top Speed</th>
    </tr>
    <tr>
      <td>{tesla.model}</td>
      <td>{teslaTopSpeed}</td>
      <td>{teslaTopColour}</td>
    </tr>
    <tr>
      <td>{honda.model}</td>
      <td>{hondaTopSpeed}</td>
      <td>{hondaTopColour}</td>
    </tr>
  </table>,
  document.getElementById("root")
);
```
Kita juga perlu perhatikan
penamaan variabel-variabelnya. Pastikan penamaannya sama seperti yang dimiliki oleh
properti objeknya


### React Hook
Hook merupakan cara agar kita bisa menggunakan atau mengakses state dan ReactJS lifecycle
dengan functional component.

### UseState
Untuk menyimpan variabel dan dipantau ketika ada perubahan nilai maka component akan di render ulang.
Format Penulisan
```javascript
const [nameState, setterState] = React.useState(initialValue)
```
Keterangan:
* nameState adalah nama dari variabel yang akan dimasukkan ke state yaitu: number
* setterState adalah nama fungsi yang akan digunakan untuk mengubah nilai state number, yaitu
* increment
* initialValue adalah nilai awal dari state number atau dalam hal ini 0
```javascript
const Counter = () => {
 const [number, increment] = React.useState(0)
 return <div>
 <h1> Counter App</h1>
 <p>Nilai counter saat ini: {number}</p>
 <button onClick={() => increment(number+1)}> + </button>
 </div>
}
```

contoh dalam react:
```javascript
import React, { useState } from "react";

function App() {
  const [number, setNumber] = useState(0);

  function increment() {
    setNumber(number + 1);
  }

  function decrement() {
    setNumber(number - 1);
  }

  return (
    <div className="container">
      <h1>{number}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </div>
  );
}

export default App;
```
jadi useState React Hook digunakan untuk website agar diperbaharui secara dinamis

### Memperbarui objek dan array dalam keadaan
Anda dapat menempatkan objek dan array ke dalam status. Di React, status dianggap hanya-baca, jadi Anda harus menggantinya daripada mengubah objek yang sudah ada . Misalnya, jika Anda memiliki formobjek dalam status, jangan perbarui seperti ini:

```javascript
// Don't mutate an object in state like this:
form.firstName = 'Taylor';
```

Sebagai gantinya, ganti seluruh objek dengan membuat yang baru:
```javascript
setForm({
  ...form,
  firstName: 'Taylor'
});
```

### Contoh 1 dari 4 :Bentuk (objek)
Dalam contoh ini, formvariabel state memegang sebuah objek. Setiap input memiliki pengendali perubahan yang memanggil setFormstatus berikutnya dari seluruh formulir. Sintaks { ...form }spread memastikan bahwa objek status diganti daripada dimutasi.

```javascript
import { useState } from 'react';

export default function Form() {
  const [form, setForm] = useState({
    firstName: 'Barbara',
    lastName: 'Hepworth',
    email: 'bhepworth@sculpture.com',
  });

  return (
    <>
      <label>
        First name:
        <input
          value={form.firstName}
          onChange={e => {
            setForm({
              ...form,
              firstName: e.target.value
            });
          }}
        />
      </label>
      <label>
        Last name:
        <input
          value={form.lastName}
          onChange={e => {
            setForm({
              ...form,
              lastName: e.target.value
            });
          }}
        />
      </label>
      <label>
        Email:
        <input
          value={form.email}
          onChange={e => {
            setForm({
              ...form,
              email: e.target.value
            });
          }}
        />
      </label>
      <p>
        {form.firstName}{' '}
        {form.lastName}{' '}
        ({form.email})
      </p>
    </>
  );
}

```

Secara teknis, dimungkinkan untuk mengubah isi dari objek itu sendiri . Ini disebut mutasi:
```javascript
position.x = 5;
```
Menyalin objek dengan sintaks spread
Pada contoh sebelumnya, positionobjek selalu dibuat segar dari posisi kursor saat ini. Namun seringkali, Anda ingin memasukkan data yang ada sebagai bagian dari objek baru yang Anda buat. Misalnya, Anda mungkin ingin memperbarui hanya satu bidang dalam formulir, tetapi mempertahankan nilai sebelumnya untuk semua bidang lainnya.

Bidang input ini tidak berfungsi karena onChangepenangan mengubah status:
```javascript
import { useState } from 'react';

export default function Form() {
  const [person, setPerson] = useState({
    firstName: 'Barbara',
    lastName: 'Hepworth',
    email: 'bhepworth@sculpture.com'
  });

  function handleFirstNameChange(e) {
    person.firstName = e.target.value;
  }

  function handleLastNameChange(e) {
    person.lastName = e.target.value;
  }

  function handleEmailChange(e) {
    person.email = e.target.value;
  }

  return (
    <>
      <label>
        First name:
        <input
          value={person.firstName}
          onChange={handleFirstNameChange}
        />
      </label>
      <label>
        Last name:
        <input
          value={person.lastName}
          onChange={handleLastNameChange}
        />
      </label>
      <label>
        Email:
        <input
          value={person.email}
          onChange={handleEmailChange}
        />
      </label>
      <p>
        {person.firstName}{' '}
        {person.lastName}{' '}
        ({person.email})
      </p>
    </>
  );
}
```
Misalnya, baris ini mengubah status dari render sebelumnya:
```javascript
person.firstName = e.target.value;
```
Cara yang dapat diandalkan untuk mendapatkan perilaku yang Anda cari adalah dengan membuat objek baru dan meneruskannya ke setPerson. Tetapi di sini, Anda juga ingin menyalin data yang ada ke dalamnya karena hanya satu bidang yang berubah:
```javascript
setPerson({
  firstName: e.target.value, // New first name from the input
  lastName: person.lastName,
  email: person.email
});
```
Anda dapat menggunakan sintaks ... penyebaran objek sehingga Anda tidak perlu menyalin setiap properti secara terpisah.
```javascript
setPerson({
  ...person, // Copy the old fields
  firstName: e.target.value // But override this one
});
```

Sekarang formulirnya berfungsi!

Perhatikan bagaimana Anda tidak mendeklarasikan variabel status terpisah untuk setiap bidang input. Untuk formulir besar, menyimpan semua data yang dikelompokkan dalam suatu objek sangatlah mudah—asalkan Anda memperbaruinya dengan benar!

```javascript
import { useState } from 'react';

export default function Form() {
  const [person, setPerson] = useState({
    firstName: 'Barbara',
    lastName: 'Hepworth',
    email: 'bhepworth@sculpture.com'
  });

  function handleFirstNameChange(e) {
    setPerson({
      ...person,
      firstName: e.target.value
    });
  }

  function handleLastNameChange(e) {
    setPerson({
      ...person,
      lastName: e.target.value
    });
  }

  function handleEmailChange(e) {
    setPerson({
      ...person,
      email: e.target.value
    });
  }

  return (
    <>
      <label>
        First name:
        <input
          value={person.firstName}
          onChange={handleFirstNameChange}
        />
      </label>
      <label>
        Last name:
        <input
          value={person.lastName}
          onChange={handleLastNameChange}
        />
      </label>
      <label>
        Email:
        <input
          value={person.email}
          onChange={handleEmailChange}
        />
      </label>
      <p>
        {person.firstName}{' '}
        {person.lastName}{' '}
        ({person.email})
      </p>
    </>
  );
}
```

Perhatikan bahwa ...sintaks spread adalah "dangkal"—hanya menyalin sesuatu sedalam satu tingkat. Ini membuatnya cepat, tetapi itu juga berarti bahwa jika Anda ingin memperbarui properti bersarang, Anda harus menggunakannya lebih dari sekali.

# reducers
```javascript
function(state, action){
 switch(action.type){
 case 'ADD_ITEM':
 return // logic untuk menghandle add item ke dalam state
 case 'REMOVE_ITEM':
 return // logic untuk menghandle remove item dari state
 default:
 return state; // tidak ada tipe event yang cocok, kembalikan
state dengan tanpa perubahan
 }
}
```
# Store
Building Block berikutnya adalah Store. Sejatinya, store hanyalah cara untuk mengumpulkan reducer
yang jumlahnya lebih dari satu menjadi satu state global yang akan dikonsumsi oleh komponen React.
Pada Redux kita menggunakan fungsi combineReducers untuk mengumpulkan reducers menjadi
satu, kemudian kita buat Store dengan fungsi createStore seperti ini:

```javascript
import { combineReducers, createStore } from 'redux';
// MISALNYA KITA SUDAH MEMBUAT 2 REDUCER INI
import itemReducer from './features/items';
import userReducer from './features/users';
// gabungkan reducers jadi satu
let rootReducers = combineReducers({
 items: itemReducer,
 users: userReducer
});
// buat store
let store = createStore(rootReducers);
export default store;
```
