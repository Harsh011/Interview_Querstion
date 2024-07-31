<details>
<summary>
<h3>1. Counter Function</h3>
</summary>

```js
function counter() {
  let count = 0;
  return {
    increment: function () {
      count++;
      console.log(count);
    },
    decrement: function () {
      count--;
      console.log(count);
    },
  };
}

const mycounter = counter();
mycounter.increment();
mycounter.decrement();
```

The `counter` function you've provided is a classic example of a closure in JavaScript. Here's a detailed explanation of how it works:

**The counter Function**

```js
function counter() {
  let count = 0;
  return {
    increment: function () {
      count++;
      console.log(count);
    },
    decrement: function () {
      count--;
      console.log(count);
    },
  };
}
```

**Breakdown and Explanation**

1. **Function Declaration:**

   - The `counter` function is declared. It doesn't take any parameters.

1. **Local Variable:**

   - Inside the `counter` function, a local variable count is declared and initialized to `0`.

1. **Returning an Object:**

   - The counter function returns an object that contains two methods: increment and decrement.

1. Methods:

   - `increment`: This method increases the value of count by 1 and then logs the current value of `count` to the console.
   - `decrement`: This method decreases the value of count by 1 and then logs the current value of `count` to the console.

**Closures in Action**

When the `counter` function is called, it returns an object containing the `increment` and `decrement` methods. These methods form closures over the count variable. This means they have access to the `count` variable even after the `counter` function has finished executing.

Example Usage

```js
const myCounter = counter();

myCounter.increment(); // 1
myCounter.increment(); // 2
myCounter.decrement(); // 1
```

**Explanation:**

1.  **Calling counter:**

    - `const myCounter = counter();`
    - This calls the `counter` function and assigns the returned object to `myCounter`.

1.  **Increment Method:**

        - `myCounter.increment();` increments the count by `1` and logs 1.
        - `myCounter.increment();` increments the count by `1` again and logs `2`.

    1.** Decrement Method:**

        - `myCounter.decrement();` decrements the count by `1` and logs `1`.

**Why Use Closures?**

Closures are useful for creating private variables and methods. In this example, the count variable is private to the `counter` function and can't be accessed directly from the outside. It can only be modified using the `increment` and `decrement` methods, providing controlled access to the variable.

This pattern is often used to create modules or factory functions that encapsulate and manage state in a controlled manner.

</details>

<details>
<summary>
<h3>2. statements  executed</h3>
</summary>

```js
console.log("Start");
setTimeout(() => {
  console.log("settimeout");
}, 0);
Promise.resolve().then(() => {
  console.log("promise");
});
console.log("End");
```

**Step-by-Step Execution:**

1. **Synchronous Code Execution:**

   - JavaScript starts executing the code from top to bottom.

1. **First console.log("Start"):**

   - This is a synchronous operation. "Start" is logged to the console immediately.
   - Output: Start

1. **setTimeout with 0 ms delay:**

   - The setTimeout function is called with a delay of 0 milliseconds.
   - The callback function (() => { console.log("settimeout"); }) is scheduled to run after the current call stack is empty and after all the currently pending microtasks have been processed. It is placed in the task queue (or macro task queue).

1. **Promise.resolve().then(...):**

   - A resolved promise is created, and the .then method is called on it.
   - The callback function inside .then (() => { console.log("promise"); }) is scheduled to run as a microtask, which will be executed after the current synchronous code is finished but before any tasks from the task queue.

1. **Second console.log("End"):**

   - This is a synchronous operation. "End" is logged to the console immediately.
   - Output: End

1. **Microtasks Execution:**

   - After the synchronous code has finished executing, the JavaScript engine checks the microtask queue.
   - The callback function from the resolved promise is in the microtask queue, so it is executed next.
   - Output: `promise`

1. **Task Queue Execution:**

   - After the microtasks have been executed, the JavaScript engine checks the task queue.
   - The callback function from the `setTimeout` is in the task queue and is executed.
   - Output: `settimeout`

**Final Order of Output:**

1. `Start`
1. `End`
1. `promise`
1. `settimeout`

**Why This Order?**

- Synchronous code (`console.log` statements) is executed first.
- Microtasks (callbacks from promises) are executed after the synchronous code but before the task queue.
- Tasks (`callbacks from setTimeout`) are executed after all microtasks have been processed.

</details>
</details>
<details>
<summary>
<h3>3. Closure Example</h3>
</summary>

```js
var x = 1;
function outer() {
  console.log(x);
  function inner() {
    console.log(x);
  }
  var x = 10;
  inner();
}
outer();
```

**Step-by-Step Execution**

1. Global Scope:

   ```js
   var x = 1;
   ```

   - The variable x is declared and initialized with the value 1 in the global scope.

1. Function Declaration:

   ```js
   function outer() { ... }

   ```

   - The function outer is declared in the global scope.

1. Calling outer():

   ```js
   outer();
   ```

   - The outer function is called.

**Inside the outer Function**

1.  **Variable x Declaration (Hoisting):**

    ```js
    var x = 10;
    ```

    - Due to JavaScript's hoisting mechanism, the declaration of x is hoisted to the top of the function scope, but not its initialization. So, the code inside outer looks like this after hoisting:

    ```js
    function outer() {
      var x;
      console.log(x);
      function inner() {
        console.log(x);
      }
      x = 10;
      inner();
    }
    ```

1.  First console.log(x):

    ```js
    console.log(x);
    ```

    - At this point, x is declared but not yet initialized, so it is undefined.
    - Output: undefined

1.  Calling inner():

    ````js
    inner();

        ```

    **Inside the inner Function**

    ````

1.  console.log(x) in inner:

    ```js
    console.log(x);
    ```

    - inner function has access to the x variable declared in outer's scope due to lexical scoping.
    - By the time inner is called, x has been initialized to 10 in the outer function scope.
    - Output: 10

**Execution Summary**

- The global x is 1, but it is shadowed by the local x inside the outer function.
- When outer is called:
  - The first console.log(x) logs undefined because the local x is declared but not yet initialized.
  - The inner function logs 10 because by the time it is called, the local x in outer has been initialized to 10.

**Final Output**

The final output of the code is:

```js
undefined;
10;
```

This output demonstrates JavaScript's hoisting and scoping mechanisms, where variable declarations are hoisted to the top of their scope but initializations are not, and functions have access to variables in their lexical scope.

</details>

<details>
<summary>
<h3>4. Async function</h3>
</summary>

```js
async function foo() {
  return "Hello world";
}

const result = foo();
console.log(result);
```

**Explanation**:

1. async Function:

   - The async keyword before a function declaration (async function foo() { ... }) ensures that the function always returns a promise. In this case, foo() returns a promise that resolves with the value "Hello world".

1. Calling foo():

   - When foo() is called, it starts executing synchronously. However, because it's an async function, it immediately returns a promise.

1. Promise Returned by foo():

   - The expression const result = foo(); assigns the promise returned by foo() to the variable result.

1. Logging result:

   - console.log(result); logs the promise object itself, not the resolved value "Hello world".

**Output**:

When you run this code, the output logged to the console will be:

```js
Promise {<resolved>: "Hello world"}

```

**Understanding the Output:**

- `foo()` returns a promise immediately with the resolved value `"Hello world".`
- c`onsole.log(result)`; logs the promise object itself, which includes information about its state (`resolved`) and the resolved value `("Hello world").`
  **Accessing the Resolved Value:**

To access the resolved value `"Hello world"` from the promise returned by foo(), you need to use `.then()` or `async/await:`

- Using `.then()`:

```js
foo().then((result) => {
  console.log(result); // Output: Hello world
});
```

Using `async/await` (within an `async` function):

```js
async function example() {
  const result = await foo();
  console.log(result); // Output: Hello world
}

example();
```

**Summary**:

- `async` functions always return a promise.
- Calling an `async` function returns a promise immediately, even before the function completes execution.
- To get the resolved value from an `async` function, you typically use .`then()` or await within an async function.

</details>
<details>
<summary>
<h3>5. Without flat method solve</h3>
</summary>

To convert a nested array, such as `[[1, 2], [3, 4], [5]]`, into a single flat array without using the `Array.prototype.flat()` method, you can use various techniques. One common approach is to use the `Array.prototype.concat()` method along with the `spread` operator, `Array.prototype.reduce()`, or a simple loop.

**Using `concat()` with Spread Operator**

The spread operator `...` can be used to unpack elements from an array. By spreading the nested arrays into `concat()`, you can concatenate them into a single array.

```js
const arr = [[1, 2], [3, 4], [5]];
const flattenedArr = [].concat(...arr);

console.log(flattenedArr); // Output: [1, 2, 3, 4, 5]
```

**Using reduce()**

The `reduce()` method can also be used to accumulate the elements of the nested arrays into a single array.

```js
const arr = [[1, 2], [3, 4], [5]];
const flattenedArr = arr.reduce((acc, curr) => acc.concat(curr), []);

console.log(flattenedArr); // Output: [1, 2, 3, 4, 5]
```

Here, `acc` is the accumulator that starts as an empty array `[],` and curr represents the current sub-array being iterated over. The `concat()` method combines each sub-array (`curr`) into the accumulator (`acc`).

**Using a For Loop**

You can also flatten the array using a traditional `for` loop.

```js
const arr = [[1, 2], [3, 4], [5]];
const flattenedArr = [];

for (let i = 0; i < arr.length; i++) {
  for (let j = 0; j < arr[i].length; j++) {
    flattenedArr.push(arr[i][j]);
  }
}

console.log(flattenedArr); // Output: [1, 2, 3, 4, 5]
```

In this example, two nested loops iterate over the sub-arrays and push each element into the `flattenedArr` array.

Each of these methods effectively flattens the nested array `[[1, 2], [3, 4], [5]] `into `[1, 2, 3, 4, 5] `without using the `flat()` method. The choice of method can depend on personal preference or specific requirements related to performance or readability.

</details>
<details>
<summary>
<h3>6. Find the longest words in this sentence</h3>
</summary>


To find the longest word within a string in JavaScript, you can follow these steps:

  - Split the string into an array of words.
  - Iterate through the array to find the longest word.
  - Keep track of the longest word found.

Here’s an example of how you can implement this:
```js
function findLongestWord(str) {
  // Split the string into an array of words using spaces as the delimiter
  const words = str.split(' ');
  
  // Initialize a variable to keep track of the longest word
  let longestWord = '';

  // Iterate through the array of words
  for (const word of words) {
    // If the current word's length is greater than the longestWord's length, update longestWord
    if (word.length > longestWord.length) {
      longestWord = word;
    }
  }

  // Return the longest word found
  return longestWord;
}

// Example usage
const sentence = "Find the longest word in this sentence";
const longestWord = findLongestWord(sentence);
console.log(`The longest word is: ${longestWord}`);

```
**Explanation:**

1. **Splitting the String**: str.split(' ') splits the input string into an array of words, using space as the delimiter. If the input contains punctuation or other delimiters, you may want to adjust the split method accordingly (e.g., using a regular expression).

1. **Finding the Longest Word**: The` for...of` loop iterates through each word in the array. If a word's length is greater than the current longest word, `longestWord` is updated.

1. **Returning the Result:** The function returns the longest word found.

**Handling Edge Cases:**

- Empty String: The function will return an empty string if the input is empty.
- Multiple Words of the Same Longest Length: The function will return the first word encountered with the longest length. If you want to find all longest words, you can modify the logic to store all words of the maximum length found.

</details>
<details>
<summary>
<h3>7. Find the Factorial Number</h3>
</summary>

Iterative Approach

The iterative approach uses a loop to calculate the factorial:

```js
function factorialIterative(n) {
  if (n < 0) {
    return 'Factorial is not defined for negative numbers';
  }

  let result = 1;
  for (let i = 2; i <= n; i++) {
    result *= i;
  }
  return result;
}

// Example usage
console.log(factorialIterative(5)); // Output: 120

```
**Recursive Approach**

The recursive approach involves calling the function itself to calculate the factorial:
```js
function factorialRecursive(n) {
  if (n < 0) {
    return 'Factorial is not defined for negative numbers';
  }
  if (n === 0 || n === 1) {
    return 1;
  }
  return n * factorialRecursive(n - 1);
}

// Example usage
console.log(factorialRecursive(5)); // Output: 120

```
</details>
<details>
<summary>
<h3>8. How to data transfer child to parent components</h3>
</summary>

Parent.jsx
```js
import React, { useState } from 'react';
import ChildComponent from './ChildComponent';

function ParentComponent() {
  const [message, setMessage] = useState('');

  const receiveMessage = (newMessage) => {
    setMessage(newMessage);
  };

  return (
    <div>
      <h1>Parent Component</h1>
      <p>Message from child: {message}</p>
      <ChildComponent sendMessage={receiveMessage} />
    </div>
  );
}

export default ParentComponent;

```

child.jsx
```js
import React from 'react';

function ChildComponent({ sendMessage }) {
  const handleClick = () => {
    const newMessage = "Hello from Child!";
    sendMessage(newMessage); // Call the function passed from the parent
  };

  return (
    <div>
      <h2>Child Component</h2>
      <button onClick={handleClick}>Send Message to Parent</button>
    </div>
  );
}

export default ChildComponent;

```
</details>
<details>
<summary>
<h3>9. first letter is in available or not in array</h3>
</summary>

```js
const a = ["boy", "oy"];
const b = ["Mary", "Armay"];
const c = ["Aline", "line"];
const d = ["voddo", "nc"];

function abc(arr) {
  let firstItem = arr[0].toLowerCase();
  let secondItem = arr[1].toLowerCase();

  for (let i = 0; i < secondItem.length; i++) {
    let letter = secondItem[i];
    if (firstItem.indexOf(letter) === -1) {
      return false;
    }

    return true;
  }
}

console.log(abc(a));
console.log(abc(b));
console.log(abc(c));
console.log(abc(d));
```
</details>
<details>
<summary>
<h3>10. Output will be same </h3>
</summary>

Question:- 
```js
console.log(sum(5, 6));    
console.log(sum(5)(6)); 
```
Output:-
```js
console.log(sum(5, 6));    // Output: 11
console.log(sum(5)(6));    // Output: 11

function sum(x, y) {
  if (y === undefined) {
    return (z) => {
      return x + z;
    };
  }
  return x + y;
}

```
</details>

<details>
<summary>
<h3>11. merge two values</h3>
</summary>

```js
console.log(merge("abcdef", "123"));  // a1b2c3def
console.log(merge("abc", "123456"));  // a1b2c3456
function merge(num1, num2){
    let maxLength = Math.max(num1.length, num2.length)
    // console.log(maxLength)
    let result = ''

    for (let i = 0; i < maxLength; i++) {
        if(i < num1.length){
            result += num1[i]
        }

        if(i < num2.length){
            result += num2[i]
        }
        
    }

    return result
}
```
</details>
<details>
<summary>
<h3>12. Polyfill call, apply and bind</h3>
</summary>

polyfill Call
```js
const person1 = {
  name: "John",
};

const person2 = {
  name: "Sam",
};

function greet(age) {
  console.log(
    `Hello, my name is ${this.name} and I am ${age} years old `
  );
}

unction.prototype.myCall = function (obj = {}, ...args) {
  if (typeof this !== "function") {
    throw new Error("not capable to call");
  }

  obj.fn = this;
  obj.fn(...args);
};

greet.myCall(person1, 26);
greet.myCall(person2, 28);
```

polyfill apply
```js
const person1 = {
  name: "John",
};

const person2 = {
  name: "Sam",
};

function greet(age) {
  console.log(
    `Hello, my name is ${this.name} and I am ${age} years old `
  );
}
Function.prototype.myApply = function (obj = {}, ...args) {
  if (typeof this !== "function") {
    throw new Error("not capable to call");
  }

  if (!Array.isArray(...args)) {
    throw new Error("TypeError: CreateListFromArrayLike called on non-object");
  }
  obj.fn = this;
  obj.fn(...args);
};

greet.myApply(person1, [29]);
```

polyfill bind
```js
const person1 = {
  name: "John",
};

const person2 = {
  name: "Sam",
};

function greet(age, years) {
  console.log(
    `Hello, my name is ${this.name} and I am ${age} years old and ${years} born.`
  );
}

Function.prototype.myBind = function (obj = {}, ...args1) {
  if (typeof this !== "function") {
    throw new Error("not capable to call");
  }

  obj.fn = this;
  return function (...args2) {
    obj.fn(...args1, ...args2);
  };
};

const myFunc = greet.myBind(person1, 28);
myFunc(1998);
```
</details>
<details>
<summary>
<h3>13. Two Sum</h3>
</summary>

```js
function TwoSum(num1, target) {
  for (let i = 0; i < num1.length; i++) {
    for (let j = i + 1; j < num1.length; j++) {
      if (num1[i] + num1[j] === target) {
        return [i, j];
      }
    }
  }
  return null;
}
const nums1 = [2, 7, 11, 15];
const target1 = 9;
console.log(TwoSum(nums1, target1));  //[0, 1]
```
</details>
<details>
<summary>
<h3></h3>
</summary>
</details>
