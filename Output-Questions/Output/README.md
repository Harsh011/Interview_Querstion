<h2>1.</h2>

```js
{
  let a = 1;
  let b = 2;

  console.log(a); // Output: 1
  console.log(b); // Output: 2
}

console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
```

---

<h2>2.</h2>

```js
{
  let a = 1;
  let b = 2;
  var c = 1;
  console.log(a); // Output: 1
  console.log(b); // Output: 2
}
console.log("c", c); // Output: c 1
console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
```

---

<h2>3.</h2>

```js
function sayhello() {
  let a = 1;
  let b = 2;
  var c = 1;
  console.log(a); // Output: 1
  console.log(b); // Output: 2
}

sayhello();

console.log("c", c); // ReferenceError: c is not defined
console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
```

---

<h2>4.</h2>

```js
function sayhello() {
  let a = 1;
  let b = 2;
  c = 1; // Implicit global variable
  console.log(a); // Output: 1
  console.log(b); // Output: 2
}

sayhello();

console.log("c", c); // Output: 1
console.log(a); // ReferenceError: a is not defined
console.log(b); // ReferenceError: b is not defined
```

---

<h2>5.</h2>

```js
var x = 10;

function foo() {
  console.log(x); // Output: undefined
  var x = 20;
}

foo();
```

---

<h2>6.</h2>

```js
foo(); // Calls the function foo and logs "Calling foo"

var foo = 10;
function foo() {
  console.log("Calling foo");
}

foo(); // This results in an error because foo is no longer a function
```

---

<h2>7.</h2>

```js
console.log("start"); // Output: start

setTimeout(() => {
  console.log("settiout"); // Output: settiout
}, 0);

console.log("end"); // Output: end
```

Output

```js
start;
end;
settiout;
```

---

<h2>8.</h2>

```js
for (var i = 0; i <= 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 1000);
}
```

in var case how output in

```js
for (var i = 0; i <= 3; i++) {
  (function (index) {
    setTimeout(() => {
      console.log(index);
    }, 1000 * index); // Delay each console.log by 1000 milliseconds multiplied by index
  })(i);
}
```

<h2>9. </h2>

```js
setTimeout(() => {
  console.log("timeout"); //timeout
}, 0);

Promise.resolve().then(() => console.log("Promise")); //Promise

console.log("end"); // end
```

Output

```
end
Promise
timeout

```

---

<h2>10.</h2>

```js
function abc() {
  console.log("hii"); // hii
}

const value = abc();
console.log(value); //undefined
```

output

```js
hii;
undefined;
```

---

<h2>11.</h2>

```js
console.log(a);
console.log(b);
var a = (b = 5);
```

---

<h2>12.</h2>

```js
console.log("4" + 6 * 5); // 430
```

---

<h2>13.</h2>

```js
console.log(typeof NaN); // number
```
---
<h2>14.</h2>

```js
console.log("5" - "3" + 4); // (2 + 4) => 6
```
---
<h2>15.</h2>

```js
console.log(NaN == NaN); //false
console.log(NaN == NaN); //false
```
---
