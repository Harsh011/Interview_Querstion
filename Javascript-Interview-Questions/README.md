<details>
<summary><h3>1. Explain Call, Apply, and Bind</h3></summary>
In JavaScript, `call`, `apply`, and `bind` are methods used to control the this context when invoking functions. Here's a detailed explanation of each:

**call**

The `call` method calls a function with a given `this` value and arguments provided individually.

**Syntax:**

```js
function.call(thisArg, arg1, arg2, ...)

```

Example:

```js
function greet(greeting, punctuation) {
  console.log(greeting + ", " + this.name + punctuation);
}

const person = { name: "Alice" };

greet.call(person, "Hello", "!"); // Output: Hello, Alice!
```

**apply**

The `apply` method is similar to `call`, but it takes an array (or array-like object) of arguments instead of listing them individually.

**Syntax:**

```js
function.apply(thisArg, [argsArray])

```

Example:

```js
function greet(greeting, punctuation) {
  console.log(greeting + ", " + this.name + punctuation);
}

const person = { name: "Alice" };

greet.apply(person, ["Hello", "!"]); // Output: Hello, Alice!
```

**bind**

The `bind` method creates a new function that, when called, has its `this` keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

Syntax:

```js
const boundFunction = function.bind(thisArg, arg1, arg2, ...)

```

Example:

```js
function greet(greeting, punctuation) {
  console.log(greeting + ", " + this.name + punctuation);
}

const person = { name: "Alice" };

const boundGreet = greet.bind(person, "Hello");
boundGreet("!"); // Output: Hello, Alice!
```

**Summary**

- `call`: Invokes the function with the specified `this` context and individual arguments.
- `apply`: Invokes the function with the specified `this` context and arguments as an array.
- `bind`: Returns a new function with the specified `this` context and optionally prepends arguments.

These methods are essential for controlling the execution context of functions, especially in scenarios where the `this` keyword needs to reference a specific object.

</details>

<details>
<summary>
<h3>2. Explain Var, Let, Const</h3>
</summary>
In JavaScript, `var`, `let`, and `const` are used to declare variables, but they have different scopes, hoisting behavior, and reassignability. Here's a detailed explanation of each:

**var**

- **Scope**: Function-scoped. If declared within a function, it is only accessible within that function. If declared outside any function, it is globally scoped.
- **Hoisting**: Variables declared with `var` are hoisted to the top of their scope, but their initialization remains in place.
- **Reassignability**: Can be reassigned.
  Example:

```js
function varExample() {
  if (true) {
    var x = 10;
  }
  console.log(x); // 10
}

varExample();

console.log(y); // undefined due to hoisting
var y = 5;
```

**`let`**
**Scope**: Block-scoped. It is only accessible within the block (e.g., { }, loops, conditionals) where it is declared.
**Hoisting**: Variables declared with `let` are hoisted to the top of their block, but they are not initialized until the declaration is encountered (temporal dead zone).
**Reassignability**: Can be reassigned.
Example

```js
function letExample() {
  if (true) {
    let x = 10;
    console.log(x); // 10
  }
  // console.log(x); // ReferenceError: x is not defined
}

letExample();

let y = 5;
// let y = 6; // SyntaxError: Identifier 'y' has already been declared
```

**`const`**

**Scope**: Block-scoped. It is only accessible within the block where it is declared.
**Hoisting**: Variables declared with `const` are hoisted to the top of their block, but they are not initialized until the declaration is encountered (temporal dead zone).
**Reassignability**: Cannot be reassigned. The value must be assigned at the time of declaration.
Example:

```js
function constExample() {
  if (true) {
    const x = 10;
    console.log(x); // 10
  }
  // console.log(x); // ReferenceError: x is not defined
}

constExample();

const y = 5;
// y = 6; // TypeError: Assignment to constant variable
// const z; // SyntaxError: Missing initializer in const declaration
```

**Summary**

**`var`**:

- Function-scoped
  Hoisted with initialization undefined
- Can be reassigned

**`let`**:

- Block-scoped
  H- oisted but not initialized until the declaration is encountered (temporal dead zone)
- Can be reassigned
- **`const`**:

- Block-scoped
- Hoisted but not initialized until the declaration is encountered (temporal dead zone)
- Cannot be reassigned (constant value)

Using `let` and `const` is generally preferred over `var` due to their block-scoping, which reduces the chances of bugs related to variable scope and hoisting.

</details>

<details>
<summary>
<h3>3. Explain Primitive Data Types.</h3>
</summary>
Primitive data types in JavaScript are the most basic types of data, which are immutable and not objects. They are directly accessible at the language level and have no methods or properties (except through type coercion where JavaScript temporarily wraps them in their object counterparts). Here are the primitive data types in JavaScript:

1. **`Number`**

   - **Description**: Represents both integer and floating-point numbers.
   - **Examples**:

   ```js
   let intNumber = 42;
   let floatNumber = 3.14;
   ```

2. **`String`**

   - **Description**: Represents a sequence of characters.
   - **Examples**:

   ```js
   let singleQuoteString = "Hello, world!";
   let doubleQuoteString = "Hello, world!";
   let templateLiteral = `Hello, world!`;
   ```

3. **`Boolean`**
   - Description: Represents a logical entity and can have two values: true and false.
   - Examples:
   ```js
   let isTrue = true;
   let isFalse = false;
   ```
4. **`null`**
   - Description: Represents the intentional absence of any object value. It is a special keyword and can be assigned to a variable to indicate that the variable is empty or has an unknown value.
   - Example:
   ```js
   let emptyValue = null;
   ```
5. **`undefined`**

   - **Description**: Indicates that a variable has been declared but has not yet been assigned a value.
   - **Example**:

   ```js
   let undefinedValue;
   console.log(undefinedValue); // undefined
   ```

6. **`Symbol`**

   - **Description**: Represents a unique and immutable primitive value, often used to identify object properties uniquely. Each `Symbol` value is unique.
   - **Example**:

   ```js
   const uniqueSymbol = Symbol("description");
   const anotherSymbol = Symbol("description");
   console.log(uniqueSymbol === anotherSymbol); // false
   ```

7. **`BigInt`**

   - **Description**: Represents integers with arbitrary precision. It is useful for handling large integers that are beyond the safe integer limit for `Number` (which is )
   - **Example**:

   ```js
   const bigIntValue = BigInt(123456789012345678901234567890);
   const anotherBigInt = 123456789012345678901234567890n; // Using the "n" suffix
   console.log(bigIntValue === anotherBigInt); // true
   ```

**Characteristics of Primitive Data Types**

- **Immutability**: Once a primitive value is created, it cannot be altered. Any operation on a primitive value creates a new value.
- **Direct Access:** Primitive values are accessed directly by their value, unlike objects, which are accessed by reference.
- **Type Coercion:** JavaScript can temporarily wrap primitive values in their object counterparts (e.g., `String`, `Number`) to allow access to methods.

**Examples Demonstrating Characteristics**

**Immutability Example:**

```js
let str = "hello";
str[0] = "H"; // This has no effect
console.log(str); // "hello"
```

**Type Coercion Example:**

```js
let str = "hello";
console.log(str.toUpperCase()); // "HELLO" - String primitive is temporarily wrapped in a String object
```

Understanding these primitive data types and their characteristics is fundamental to mastering JavaScript and using its type system effectively.

</details>

<details>
<summary>
<h3>4. Explain  sets, weaksets, map and weakmaps </h3>
</summary>
In JavaScript, Set, WeakSet, Map, and WeakMap are collection objects that provide unique ways to store and manage data. Each has distinct characteristics and use cases. Here's an explanation of each:

1. **Set**

A `Set` is a collection of unique values, meaning no duplicates are allowed.

- **Characteristics**:

  - Stores any type of values, whether primitive or object references.
  - Maintains insertion order of the elements.

- **Methods**:

      - `add(value)`: Adds a new element to the set.
      - `delete(value)`: Removes an element from the set.
      - `has(value):` Checks if an element is in the set.
      - `clear():` Removes all elements from the set.
      - `size`: Returns the number of elements in the set.

  Example:

```js
const mySet = new Set();

mySet.add(1);
mySet.add(5);
mySet.add(5); // Duplicate values are not added
mySet.add("text");
mySet.add({ key: "value" });

console.log(mySet.has(1)); // true
console.log(mySet.size); // 4

mySet.delete(5);
console.log(mySet.has(5)); // false

mySet.clear();
console.log(mySet.size); // 0
```

2. **WeakSet**
   A `WeakSet` is a collection of objects only, and the references are weak.

- **Characteristics**:

  - Only stores objects (not primitive values).
  - References are weak, meaning objects in a `WeakSet` can be garbage collected if there are no other references to them.
  - Does not have a `size` property or a method to iterate over its items (like `forEach`).

- **Methods**:

      - `add(value)`: Adds a new object to the set.
      - `delete(value)`: Removes an object from the set.
      - `has(value)`: Checks if an object is in the set.

  Example:

```js
const myWeakSet = new WeakSet();

const obj1 = { a: 1 };
const obj2 = { b: 2 };

myWeakSet.add(obj1);
myWeakSet.add(obj2);

console.log(myWeakSet.has(obj1)); // true

myWeakSet.delete(obj2);
console.log(myWeakSet.has(obj2)); // false

// obj1 and obj2 will be garbage collected if no other references exist
```

3. **Map**

A `Map` is a collection of key-value pairs where keys can be of any type.

- **Characteristics**:

  - Keys can be any type (primitive values or object references).
  - Maintains the insertion order of key-value pairs.

- **Methods**:

      - `set(key, value):` Adds or updates a key-value pair.
      - `get(key)`: Retrieves the value for a given key.
      - `has(key)`: Checks if a key exists in the map.
      - `delete(key)`: Removes a key-value pair.
      - `clear()`: Removes all key-value pairs.
      - `size`: Returns the number of key-value pairs.
      - `Iteration methods`: `keys()`, `values()`, `entries()`, `forEach()`.

  Example:

```js
const myMap = new Map();

myMap.set("key1", "value1");
myMap.set(2, "value2");
myMap.set({ key: "objectKey" }, "value3");

console.log(myMap.get("key1")); // "value1"
console.log(myMap.has(2)); // true
console.log(myMap.size); // 3

myMap.delete(2);
console.log(myMap.has(2)); // false

myMap.clear();
console.log(myMap.size); // 0
```

4. **WeakMap**
   A `WeakMap` is a collection of key-value pairs where keys are objects and the references to the keys are weak.

- **Characteristics**:

  - Keys must be objects (not primitive values).
  - References to key objects are weak, meaning they can be garbage collected if there are no other references to them.
  - Does not have a `size` property or methods to iterate over its items.

- **Methods**:

      - `set(key, value)`: Adds or updates a key-value pair.
      - `get(key)`: Retrieves the value for a given key.
      - `has(key)`: Checks if a key exists in the map.
      - `delete(key)`: Removes a key-value pair.

  Example:

```js
const myWeakMap = new WeakMap();

const obj1 = { a: 1 };
const obj2 = { b: 2 };

myWeakMap.set(obj1, "value1");
myWeakMap.set(obj2, "value2");

console.log(myWeakMap.get(obj1)); // "value1"
console.log(myWeakMap.has(obj2)); // true

myWeakMap.delete(obj2);
console.log(myWeakMap.has(obj2)); // false

// obj1 and obj2 will be garbage collected if no other references exist
```

**Summary**

- **Set**: Stores unique values of any type and maintains insertion order.
- **WeakSet**: Stores objects only with weak references, allowing garbage collection of objects no longer referenced elsewhere.
- **Map**: Stores key-value pairs with keys of any type and maintains insertion order.
- **WeakMap**: Stores key-value pairs with object keys and weak references, allowing garbage collection of keys no longer referenced elsewhere.

These collection types provide flexibility and efficiency for various use cases in JavaScript programming.

</details>
<details>
<summary>
<h3>5. what is session storage and local storage</h3>
</summary>
Session Storage and Local Storage are both web storage APIs provided by HTML5 to store data on the client's browser. They allow you to save data in key/value pairs and are designed to hold data in a more persistent way compared to cookies, but they differ in terms of scope and duration of storage.

**Session Storage**

**Scope and Duration:**

- Scope: Data is stored only for the duration of the page session. A page session lasts as long as the browser is open, and survives over page reloads and restores.
- Duration: Data is lost when the page session ends, which means when the browser or tab is closed.

**Usage**:

- It is used for storing data that needs to be available for the duration of a page session, such as temporary states and user inputs.

**Example**:

```js
// Save data to sessionStorage
sessionStorage.setItem("key", "value");

// Retrieve data from sessionStorage
let data = sessionStorage.getItem("key");

// Remove data from sessionStorage
sessionStorage.removeItem("key");

// Clear all data from sessionStorage
sessionStorage.clear();
```

**Local Storage**

**Scope and Duration:**

- Scope: Data is stored with no expiration time and is accessible from any page on the same domain.
- Duration: Data persists even after the browser is closed and reopened. It remains until it is explicitly deleted by the user or the application.

**Usage**:

- It is used for storing data that needs to persist across sessions, such as user preferences, settings, and other application state information.
  Example:

```js
// Save data to localStorage
localStorage.setItem("key", "value");

// Retrieve data from localStorage
let data = localStorage.getItem("key");

// Remove data from localStorage
localStorage.removeItem("key");

// Clear all data from localStorage
localStorage.clear();
```

**Key Differences**

1. **Lifetime:**

   - Session Storage: Data is cleared when the page session ends.
   - Local Storage: Data persists until explicitly deleted.

1. **Scope:**

   - Session Storage: Data is specific to the current tab or window.
   - Local Storage: Data is shared across all tabs and windows within the same origin.

1. **Use Cases:**

   - Session Storage: Temporary data, form data during navigation, session-specific settings.
   - Local Storage: User preferences, application settings, persistent state data.

Both storage types offer a straightforward way to manage client-side data without server communication, enhancing performance and user experience by reducing server load and latency.

</details>
<details>
<summary>
<h3>6. when did you use in call apply bind in practical</h3>
</summary>
The `call`, `apply`, and `bind` methods are used to control the context (this value) in which a function executes in JavaScript. They are particularly useful in various practical scenarios, such as:

1. **Function Borrowing**

Sometimes, you might want to borrow a method from another object and use it as if it belonged to your object.

Example with `call` and `apply`:

```js
const person1 = {
  name: "Alice",
  greet: function (greeting) {
    console.log(`${greeting}, my name is ${this.name}`);
  },
};

const person2 = {
  name: "Bob",
};

person1.greet.call(person2, "Hello"); // Hello, my name is Bob
person1.greet.apply(person2, ["Hi"]); // Hi, my name is Bob
```

2. **Invoking Functions with Different this Values**
   You may need to invoke a function with a specific `this` value.

Example with bind:

```js
const module = {
  x: 42,
  getX: function () {
    return this.x;
  },
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // undefined, because `this` is not bound

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX()); // 42
```

3. **Setting this in Callback Functions**

When passing a method as a callback, you might want to ensure it has the correct `this` value.

Example:

```js
function Button() {
  this.clicked = false;
  this.click = function () {
    this.clicked = true;
    console.log("Button clicked:", this.clicked);
  };
}

const button = new Button();
document
  .getElementById("myButton")
  .addEventListener("click", button.click.bind(button));
// Ensures `this` in `button.click` refers to the button instance, not the DOM element.
```

4.**Partial Application**

Using `bind` to create a function with pre-filled arguments.

Example

```js
function multiply(a, b) {
  return a * b;
}

const double = multiply.bind(null, 2); // Creates a new function that multiplies any number by 2
console.log(double(5)); // 10
```

5. **Mimicking Array Methods**

Borrowing array methods to apply them to array-like objects (e.g., arguments object in functions).

Example:

```js
function printArgs() {
  Array.prototype.forEach.call(arguments, function (arg) {
    console.log(arg);
  });
}

printArgs(1, 2, 3, 4); // 1, 2, 3, 4
```

**Summary**

- **`call`**: Invokes a function with a specified `this` value and arguments provided individually.
- **`apply`**: Invokes a function with a specified `this` value and arguments provided as an array.
- **`bind`**: Creates a new function with a specified `this` value and optionally prepends arguments.

These methods are powerful tools for controlling the execution context of functions, allowing for flexible and reusable code in various practical scenarios.

```js

```

</details>
<details>
<summary>
<h3>7. Difference between map and forEach</h3>
</summary>
Both `map` and `forEach` are array methods in JavaScript, but they serve different purposes and have distinct characteristics. Here are the key differences between them:

**`forEach`**

1. **Purpose:**

   - `forEach` is used to execute a provided function once for each array element. It is typically used for performing side effects (e.g., modifying external variables, logging to the console, etc.) rather than transforming the array.

1. **Return Value:**

   - `forEach` does not return a new array. It returns undefined.

1. **Usage:**

   - It is used when you want to iterate over an array and perform actions for each element without needing a new array of transformed values.

1. **Example:**

```js
const arr = [1, 2, 3];
arr.forEach((num) => {
  console.log(num * 2);
});
// Output: 2, 4, 6
```

**`map`**

1. **Purpose:**

   - `map` is used to create a new array by applying a provided function to each element of the original array. It is typically used for transforming the elements of the array.

1. **Return Value:**

   - `map` returns a new array containing the results of applying the provided function to each element of the original array.

1. **Usage:**

   - It is used when you want to transform each element of an array and get a new array with the transformed values.

1. **Example:**

```js
const arr = [1, 2, 3];
const doubled = arr.map((num) => num * 2);
console.log(doubled); // Output: [2, 4, 6]
```

**Key Differences**

1. **Return Value:**

   - `forEach`: Returns `undefined`.
   - `map`: Returns a new array with transformed elements.

1. **Intent:**

   - `forEach`: Used for side effects, not for creating a new array.
   - `map`: Used for transforming array elements and creating a new array.

1. **Chaining:**

   - forEach: Cannot be chained because it returns `undefined`.
   - map: Can be chained with other array methods (like `filter`, `reduce`, etc.) because it returns a new array.

1. **Side Effects:**

   - `forEach`: Commonly used when you need to perform side effects (e.g., modifying external variables, logging, etc.).
   - `map`: Designed for pure functions that produce new data without side effects.

**Choosing Between forEach and map**

- Use `forEach` when you need to perform an action for each element of the array and don't need a new array as the result.
- Use `map` when you need to transform each element of the array and get a new array with the transformed values.
</details>
<details>
<summary>
<h3>8. what is hoisting</h3>
</summary>
"Hoisting" in JavaScript is a behavior in which variable and function declarations are moved to the top of their containing scope during the compile phase, before the code execution. This means that a variable or function can be used before it has been declared.

**Hoisting with Variables**

In JavaScript, variables declared with `var` are hoisted to the top of their containing function or global scope. However, only the declaration is hoisted, not the initialization.

```js
console.log(x); // Output: undefined
var x = 5;
console.log(x); // Output: 5
```

The above code is interpreted as:

```js
var x;
console.log(x); // Output: undefined
x = 5;
console.log(x); // Output: 5
```

Variables declared with `let` and `const` are also hoisted, but they are not initialized. This means that if you try to access them before their declaration, you will get a `ReferenceError`.

```js
console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;

console.log(z); // ReferenceError: Cannot access 'z' before initialization
const z = 20;
```

**Hoisting with Functions**

Function declarations are completely hoisted, including their definitions.

```js
hoistedFunction(); // Output: "This function has been hoisted."

function hoistedFunction() {
  console.log("This function has been hoisted.");
}
```

Function expressions are not hoisted.

```js
notHoistedFunction(); // TypeError: notHoistedFunction is not a function

var notHoistedFunction = function () {
  console.log("This function has not been hoisted.");
};
```

The above code is interpreted as:

```js
var notHoistedFunction;
notHoistedFunction(); // TypeError: notHoistedFunction is not a function

notHoistedFunction = function () {
  console.log("This function has not been hoisted.");
};
```

**Summary**

- Variable declarations with `var` are hoisted but not initialized.
- Variables declared with `let` and `const` are hoisted but not initialized and will result in a `ReferenceError` if accessed before declaration.
- Function declarations are hoisted along with their definitions.
- Function expressions are not hoisted.

Understanding hoisting helps in writing more predictable and error-free JavaScript code.

</details>
<details>
<summary>
<h3>9. How the js engine works</h3>
</summary>
The JavaScript engine is responsible for executing JavaScript code. It performs a series of steps to convert human-readable code into machine-executable instructions. Let's explore the core components and the process:

**Components of a JavaScript Engine**

1. **Parser**: Converts the code into an Abstract Syntax Tree (AST).
1. **Interpreter**: Executes the code line by line.
1. **Just-In-Time (JIT) Compiler**: Optimizes and compiles frequently executed code into machine code.
1. **Garbage Collector:** Manages memory allocation and deallocation.

**Execution Process**

1. **Parsing**

The JavaScript engine starts by parsing the code to check for syntax errors and to create an Abstract Syntax Tree (AST). This involves two steps:

- Lexical Analysis: Converts the code into tokens.
- Syntax Analysis: Converts tokens into an AST.
  Example:

```js
let x = 10;
```

The AST might look like:

```js
Program
  └── VariableDeclaration
        ├── VariableDeclarator
        │     ├── Identifier: x
        │     └── Literal: 10

```

2. **Compilation**

JavaScript engines use a Just-In-Time (JIT) compiler to optimize the code. Modern engines like V8 (used in Chrome and Node.js) use two main compilers:

- **Baseline Compiler**: Quickly generates machine code for initial execution.
- **Optimizing Compiler**: Recompiles and optimizes frequently executed code paths (hot code).

3. **Execution**

The interpreter or the compiled machine code runs the program. If the JIT compiler has optimized some parts of the code, it will run those optimized sections instead.

4. **Memory Management**

JavaScript has automatic memory management through a garbage collector, which reclaims memory allocated to objects that are no longer in use.

**Example: Hoisting and Execution**

Consider the following code:

```js
function foo() {
  console.log(x);
  var x = 10;
  console.log(x);
}
foo();
```

**Parsing**

The parser generates an AST for the function `foo`.

**Hoisting**

During the compilation phase, the engine hoists variable declarations to the top of their scope:

```js
function foo() {
  var x; // Declaration hoisted
  console.log(x); // undefined
  x = 10;
  console.log(x); // 10
}
foo();
```

**Execution**

The interpreter executes the code step by step:

1. The declaration `var x;` is hoisted.
1. `console.log(x);` outputs `undefined` because `x` is declared but not initialized.
1. `x = 10;` initializes the variable.
1. `console.log(x);` outputs `10`.

**Optimizations**

Modern engines perform various optimizations:

- **Inline Caching:** Caches the types of frequently accessed objects to speed up property access.
- **Hidden Classes:** Dynamically generate classes to optimize object property access.
- **Garbage Collection:** Uses algorithms like Mark-and-Sweep and Generational Garbage Collection to manage memory efficiently.

By combining interpretation and JIT compilation, JavaScript engines achieve a balance between fast startup times and high execution performance.

</details>
<details>
<summary>
<h3>10. What is callbackHell</h3>
</summary>
Callback hell, also known as "pyramid of doom," refers to the situation in JavaScript where multiple nested callbacks make the code difficult to read and maintain. This happens when asynchronous operations are chained together in a way that each subsequent operation depends on the result of the previous one, leading to deeply nested and hard-to-follow code structure.

Here's an example of callback hell:

```js
doSomething(function (result1) {
  doSomethingElse(result1, function (result2) {
    doAnotherThing(result2, function (result3) {
      doFinalThing(result3, function (result4) {
        console.log("All done");
      });
    });
  });
});
```

In this example, each operation depends on the completion of the previous one, leading to multiple levels of nesting. This makes the code difficult to read, understand, and maintain. It can also be challenging to handle errors properly.

**Solutions to Callback Hell**

1.  **Promises**

    Promises provide a cleaner way to handle asynchronous operations by chaining them together using `.then()` and `.catch()` methods.

    ```js
    doSomething()
      .then((result1) => doSomethingElse(result1))
      .then((result2) => doAnotherThing(result2))
      .then((result3) => doFinalThing(result3))
      .then((result4) => {
        console.log("All done");
      })
      .catch((error) => {
        console.error("Error:", error);
      });
    ```

1.  **Async/Await**

    The `async` and `await` keywords provide a more synchronous-looking way to handle asynchronous operations. This approach makes the code more readable and easier to follow

    ```js
    async function doAllThings() {
      try {
        const result1 = await doSomething();
        const result2 = await doSomethingElse(result1);
        const result3 = await doAnotherThing(result2);
        const result4 = await doFinalThing(result3);
        console.log("All done");
      } catch (error) {
        console.error("Error:", error);
      }
    }

    doAllThings();
    ```

1.  **Modularization**

        Breaking down the code into smaller, reusable functions can also help manage complexity.
        ```js
        function handleError(error) {
            console.error('Error:', error);
        }

        function doAllThings() {
            doSomething()
                .then(result1 => doSomethingElse(result1))
                .then(result2 => doAnotherThing(result2))
                .then(result3 => doFinalThing(result3))
                .then(result4 => {
                    console.log('All done');
                })
                .catch(handleError);
        }

        doAllThings();

        ```

    By using these techniques, you can avoid callback hell and write more maintainable, readable, and error-resistant code.
    </details>
    <details>
    <summary>
    <h3>11. What is Promise</h3>
    </summary>
    In JavaScript, a Promise is an object that represents the eventual completion (or failure) of an asynchronous operation and its resulting value. Promises provide a cleaner and more robust way to handle asynchronous operations compared to traditional callbacks. They allow you to write asynchronous code in a more synchronous-looking fashion, making it easier to read and maintain.

**States of a Promise**

A Promise can be in one of three states:

1. **Pending**: The initial state, neither fulfilled nor rejected.
1. **Fulfilled**: The operation completed successfully, and the promise has a resulting value.
1. **Rejected**: The operation failed, and the promise has a reason for the failure (an error).

**Creating a Promise**

You can create a promise using the `Promise` constructor, which takes a function (called the executor) with two parameters: `resolve` and `reject`. These parameters are functions that you call to transition the promise from the pending state to either fulfilled or rejected.

```js
let promise = new Promise((resolve, reject) => {
  // Asynchronous operation
  let success = true; // Simulating success/failure

  if (success) {
    resolve("Operation was successful");
  } else {
    reject("Operation failed");
  }
});
```

**Consuming a Promise**

You consume a promise using the `.then()` and `.catch()` methods. The `.then()` method is called when the promise is fulfilled, and the `.catch()` method is called when the promise is rejected.

```js
promise
  .then((result) => {
    console.log(result); // Output: Operation was successful
  })
  .catch((error) => {
    console.error(error); // This won't run in this example
  });
```

**Chaining Promises**

Promises can be chained together, allowing you to perform a sequence of asynchronous operations. Each `.then()` returns a new promise, which you can use to chain subsequent operations.

```js
doSomething()
  .then((result1) => {
    return doSomethingElse(result1);
  })
  .then((result2) => {
    return doAnotherThing(result2);
  })
  .then((result3) => {
    console.log(result3); // Final result
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

**Example: Using Promises**

Let's look at a complete example where we simulate a series of asynchronous operations using promises.

```js
function doSomething() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Result of doSomething");
    }, 1000);
  });
}

function doSomethingElse(result) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(result + " -> Result of doSomethingElse");
    }, 1000);
  });
}

function doAnotherThing(result) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(result + " -> Result of doAnotherThing");
    }, 1000);
  });
}

doSomething()
  .then((result1) => {
    return doSomethingElse(result1);
  })
  .then((result2) => {
    return doAnotherThing(result2);
  })
  .then((result3) => {
    console.log(result3); // Output the final result
  })
  .catch((error) => {
    console.error("Error:", error);
  });
```

In this example, each function returns a promise that resolves after a delay, simulating an asynchronous operation. The promises are chained together, and the final result is logged to the console. If any of the operations fail, the error will be caught by the `.catch()` method.

**Summary**

Promises provide a powerful and flexible way to handle asynchronous operations in JavaScript. They help avoid callback hell and make your code more readable and maintainable. By using promises, you can chain asynchronous operations, handle errors gracefully, and write cleaner and more predictable code.

</details>
<details>
<summary>
<h3>12. What is Higher Order Function</h3>
</summary>
A higher-order function is a function that either takes one or more functions as arguments, returns a function as its result, or both. Higher-order functions are a fundamental concept in functional programming and are widely used in JavaScript.

Here are some common examples of higher-order functions in JavaScript:

1. **Functions as Arguments**

   A higher-order function can accept other functions as arguments. This is often used for callbacks, event handlers, or in array methods like `map`, `filter`, and `reduce`.

   **Example: Using `map` with a Function as an Argument**

   ```js
   const numbers = [1, 2, 3, 4, 5];
   const doubled = numbers.map(function (number) {
     return number * 2;
   });
   console.log(doubled); // Output: [2, 4, 6, 8, 10]
   ```

   In this example, `map` is a higher-order function because it takes a function as an argument and applies it to each element in the array.

2. **Functions as Return Values**

   A higher-order function can return another function. This is often used for function composition or creating partially applied functions (currying).

   **Example: Function Returning a Function**

   ```js
   function createMultiplier(multiplier) {
     return function (number) {
       return number * multiplier;
     };
   }

   const double = createMultiplier(2);
   console.log(double(5)); // Output: 10

   const triple = createMultiplier(3);
   console.log(triple(5)); // Output: 15
   ```

   In this example, `createMultiplier` is a higher-order function because it returns a function that multiplies a number by a given multiplier.

3. **Combining Both Concepts**

   A higher-order function can both take functions as arguments and return a function.

   **Example: Using `filter` with a Function as an Argument and Returning a Function**

   ```js
   function isGreaterThan(n) {
     return function (m) {
       return m > n;
     };
   }

   const numbers = [1, 2, 3, 4, 5];
   const greaterThanTwo = numbers.filter(isGreaterThan(2));
   console.log(greaterThanTwo); // Output: [3, 4, 5]
   ```

   In this example, `isGreaterThan` is a higher-order function because it returns a function. The `filter` method is also a higher-order function because it takes a function as an argument.

**Benefits of Higher-Order Functions**

1. **Code Reusability**: Higher-order functions allow you to write more reusable and modular code.
1. **Abstraction**: They help abstract common patterns in your code, making it more readable and maintainable.
1. **Function Composition**: They enable function composition, allowing you to build complex functionality from smaller, simpler functions.

Higher-order functions are a powerful tool in JavaScript and functional programming, enabling more expressive and concise code. By leveraging higher-order functions, you can write more abstract and reusable code, which can lead to improved maintainability and readability.

</details>
<details>
<summary>
<h3>13. What  is prototype</h3>
</summary>
In JavaScript, prototypes are a fundamental concept that enables inheritance and the sharing of properties and methods between objects. Every JavaScript object has a prototype, which is another object that the original object inherits properties and methods from. This mechanism is known as prototype-based inheritance.

**The Prototype Chain**

When you try to access a property or method on an object, JavaScript first looks at the object itself. If it doesn't find the property or method there, it looks at the object's prototype. If it still doesn't find it, it continues to look up the prototype chain until it reaches the top-level Object.prototype. If the property or method is not found anywhere in the prototype chain, JavaScript returns undefined.

**Example: Simple Prototype Chain**

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayHello = function () {
  console.log(`Hello, my name is ${this.name}`);
};

const alice = new Person("Alice");
alice.sayHello(); // Output: Hello, my name is Alice

console.log(alice.hasOwnProperty("name")); // Output: true
console.log(alice.hasOwnProperty("sayHello")); // Output: false
```

In this example:

- `Person` is a constructor function.
- `Person.prototype` is the prototype object that contains the sayHello method.
- alice is an instance of `Person` and inherits the sayHello method from `Person.prototype.`
  **Understanding `__proto__` and `prototype`**

- `__proto__`: Every object instance has a `__proto__` property, which points to its prototype. This is also known as the "dunder proto" (double underscore proto). It is a reference to the object’s prototype (the object from which it inherits properties and methods).
- `prototype`: The `prototype` property is available only on functions (specifically constructor functions). This is the object that will be used as the prototype for all instances created with that constructor.

**Example: Relationship between **proto** and prototype**

```js
function Animal(type) {
  this.type = type;
}

Animal.prototype.getType = function () {
  return this.type;
};

const dog = new Animal("Dog");

console.log(dog.__proto__ === Animal.prototype); // Output: true
console.log(dog.getType()); // Output: Dog
```

**In this example:**

- `Animal` is a constructor function.
- `Animal.prototype` is the prototype object for instances created by `Animal`.
- dog is an instance of `Animal` and its `__proto__ `points to` Animal.prototype.`

**Adding Properties and Methods to Prototypes**

You can add properties and methods to an object's prototype even after the object has been created. This allows you to extend the functionality of all instances of a constructor.

**Example: Adding Methods to a Prototype**

```js
function Car(make, model) {
  this.make = make;
  this.model = model;
}

Car.prototype.getDetails = function () {
  return `${this.make} ${this.model}`;
};

const myCar = new Car("Toyota", "Corolla");
console.log(myCar.getDetails()); // Output: Toyota Corolla

// Adding a new method to the prototype
Car.prototype.startEngine = function () {
  console.log("Engine started");
};

myCar.startEngine(); // Output: Engine started
```

In this example, the `startEngine` method is added to `Car.prototype `after `myCar` has been created. As a result, `myCar` and any other instances of `Car` can use the `startEngine` method.

**Prototypal Inheritance**

JavaScript uses prototypal inheritance to allow objects to inherit properties and methods from other objects. This can be achieved by setting one object's prototype to another object.

**Example: Prototypal Inheritance**

```js
const parent = {
  greet: function () {
    console.log("Hello from parent");
  },
};

const child = Object.create(parent);
child.greet(); // Output: Hello from parent

console.log(child.__proto__ === parent); // Output: true
```

In this example:

- `parent` is an object with a `greet` method.
- `child` is an object created with `Object.create(parent)`, which sets `child.__proto__` to `parent`.
- child inherits the `greet` method from `parent`.

Prototypes provide a powerful and flexible mechanism for object-oriented programming in JavaScript, enabling code reuse and inheritance without the need for classical inheritance models.

</details>
</details>
<details>
<summary>
<h3>14. what is cookie</h3>
</summary>
Cookies are small pieces of data that are stored on the user's device by the web browser. They are used to remember information about the user between HTTP requests and can be used for various purposes, such as session management, personalization, and tracking.

**Types of Cookies**

1. **Session Cookies**: These cookies are temporary and are deleted once the user closes their web browser.
1. **Persistent Cookies**: These cookies remain on the user's device for a set period or until they are deleted. They are used to remember information across multiple sessions.
1. **Secure Cookies**: These cookies can only be transmitted over secure HTTPS connections.
1. **HttpOnly Cookies**: These cookies cannot be accessed through JavaScript, helping to mitigate cross-site scripting (XSS) attacks.
1. **SameSite Cookies**: These cookies prevent cross-site request forgery (CSRF) attacks by allowing developers to declare if a cookie should be restricted to a first-party or same-site context.

**Setting Cookies**

Cookies can be set from both the client-side (using JavaScript) and the server-side (using HTTP headers).

**Setting Cookies with JavaScript**

```js
// Set a cookie
document.cookie =
  "username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT; path=/";

// Get all cookies
console.log(document.cookie);

// Function to set a cookie
function setCookie(name, value, days) {
  const date = new Date();
  date.setTime(date.getTime() + days * 24 * 60 * 60 * 1000);
  const expires = "expires=" + date.toUTCString();
  document.cookie = name + "=" + value + ";" + expires + ";path=/";
}

// Function to get a cookie
function getCookie(name) {
  const cname = name + "=";
  const decodedCookie = decodeURIComponent(document.cookie);
  const ca = decodedCookie.split(";");
  for (let i = 0; i < ca.length; i++) {
    let c = ca[i];
    while (c.charAt(0) == " ") {
      c = c.substring(1);
    }
    if (c.indexOf(cname) == 0) {
      return c.substring(cname.length, c.length);
    }
  }
  return "";
}

// Example usage
setCookie("username", "JohnDoe", 365);
console.log(getCookie("username")); // Output: JohnDoe
```

**Setting Cookies with HTTP Headers (Server-Side)**

HTTP response headers can be used to set cookies from the server:

```js
HTTP/1.1 200 OK
Set-Cookie: username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT; path=/; HttpOnly; Secure

```

**Example: Node.js and Express**

```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.cookie("username", "JohnDoe", { maxAge: 900000, httpOnly: true });
  res.send("Cookie is set");
});

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

**Deleting Cookies**

To delete a cookie, you can set its expiration date to a past date:

**Using JavaScript**

```js
function deleteCookie(name) {
  document.cookie = name + "=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
}

// Example usage
deleteCookie("username");
```

**Using HTTP Headers (Server-Side)**

```js
HTTP/1.1 200 OK
Set-Cookie: username=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/;

```

**Cookie Attributes**

- **expires**: Sets the expiration date for the cookie. -** max-age:** Sets the maximum age of the cookie in seconds.
- **path**: Specifies the URL path the cookie is valid for.
- **domain**: Specifies the domain the cookie is valid for.
- **secure**: Indicates that the cookie should only be sent over HTTPS.
- **HttpOnly**: Indicates that the cookie cannot be accessed through JavaScript.
- **SameSite**: Controls whether the cookie is sent with cross-site requests.

**Example: Cookie with Attributes**

```js
document.cookie =
  "username=JohnDoe; expires=Fri, 31 Dec 2024 23:59:59 GMT; path=/; domain=example.com; secure; HttpOnly; SameSite=Strict";
```

Cookies play a crucial role in web development for maintaining stateful information about users, enhancing user experience, and providing necessary security measures. Understanding how to set, get, and manage cookies effectively is essential for building robust and secure web applications.

</details>
</details>
<details>
<summary>
<h3>15. what is polyfill</h3>
</summary>
In JavaScript, a polyfill is a piece of code (usually a function or script) that provides functionality to ensure that newer features of the language or web APIs work in older browsers that do not natively support them. Polyfills are essential for maintaining cross-browser compatibility and allowing developers to use modern JavaScript features without worrying about older browser support.

**Why Use Polyfills?**

As the JavaScript language evolves, new features are added to the language specification (ECMAScript), and new web APIs are introduced. However, not all browsers implement these features at the same time. Polyfills help bridge this gap by providing fallback implementations of these features.

**Example: Array.prototype.includes Polyfill**

The `Array.prototype.includes` method was introduced in ECMAScript 2016 (ES7). It determines whether an array includes a certain value among its entries. Here's how you can write a polyfill for it:

```js
if (!Array.prototype.includes) {
  Array.prototype.includes = function (valueToFind, fromIndex) {
    if (this == null) {
      throw new TypeError('"this" is null or not defined');
    }

    // Convert the object to an array-like structure
    var o = Object(this);

    // Get the length of the array
    var len = o.length >>> 0;

    // If the length is 0, return false
    if (len === 0) {
      return false;
    }

    // Start searching from the specified index or from 0
    var n = fromIndex | 0;
    var k = Math.max(n >= 0 ? n : len - Math.abs(n), 0);

    // Loop through the array to find the value
    while (k < len) {
      if (o[k] === valueToFind) {
        return true;
      }
      k++;
    }

    // Return false if the value is not found
    return false;
  };
}
```

**Using the Polyfill**

Once the polyfill is defined, you can use the `includes` method in your code, and it will work in all browsers, even those that do not natively support it:

```js
const array = [1, 2, 3];
console.log(array.includes(2)); // Output: true
console.log(array.includes(4)); // Output: false
```

**Common Polyfills**

Some common JavaScript features that often require polyfills include:

1.** ECMAScript Methods**: Methods like `Array.prototype.includes`, `Array.prototype.find`, `String.prototype.startsWith`,` Object.assig`n, etc.

1. **Web APIs:** APIs like `fetch`, `Promise`, `URL`, etc.

**Example: `fetch` Polyfill**

The `fetch` API is a modern way to make HTTP requests, but it is not supported in older browsers. Here’s how you can include a polyfill for `fetch`:

```js
<script src="https://cdnjs.cloudflare.com/ajax/libs/fetch/3.0.0/fetch.min.js"></script>
<script>
    // Now you can use fetch in your code
    fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => console.log(data))
        .catch(error => console.error('Error:', error));
</script>

```

**Using Polyfill Libraries**

There are libraries and services that provide a collection of polyfills for various JavaScript features and APIs. Some popular ones include:

- **core-js**: A modular standard library for JavaScript that includes polyfills for ECMAScript features.
- **Polyfill**.io: A service that automatically serves polyfills based on the user’s browser.

**Example: Using `core-js`**

```js
import "core-js/stable";
import "regenerator-runtime/runtime";

// Now you can use modern JavaScript features
const array = [1, 2, 3];
console.log(array.includes(2)); // Output: true
```

**Summary**

Polyfills are a crucial tool for ensuring that modern JavaScript features and web APIs work across all browsers, including older ones. By using polyfills, developers can write cleaner and more modern code without worrying about compatibility issues. Polyfill libraries and services make it easier to include the necessary polyfills in your projects, ensuring broad compatibility and a better user experience.

</details>
</details>
<details>
<summary>
<h3>16. type="module"</h3>
</summary>

In JavaScript, `type='module'` is an attribute used in HTML `<script>` tags to indicate that the script file should be treated as a module. Modules are a way to structure JavaScript code and manage dependencies between different parts of a program.

**Understanding Modules in JavaScript**

JavaScript modules allow you to:

- **Encapsulate Code**: Modules encapsulate code into separate files, making it easier to manage and maintain large codebases.
- **Export and Import**: Modules allow you to export functions, objects, or variables from one module and import them into another, enabling code reuse and organization.
- **Control Scope**: Each module has its own scope, meaning variables and functions defined in a module are private by default unless explicitly exported.

**Using `type='module'`**

When you include a script in your HTML file with `type='module'`, it informs the browser that the script file should be treated as a module. Here's how you can use it:

HTML Example

```js
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Module Example</title>
  <!-- Include a JavaScript module -->
  <script type="module" src="main.js"></script>
</head>
<body>
  <!-- Your HTML content -->
</body>
</html>

```

JavaScript Module Example (main.js)

```js
// Exporting variables and functions from a module
export const message = "Hello, World!";

export function greet(name) {
  console.log(`Hello, ${name}!`);
}

// Importing variables and functions from another module
import { message, greet } from "./utils.js";

console.log(message); // Output: Hello, World!
greet("Alice"); // Output: Hello, Alice!
```

**Notes**:

- **Exporting**: Use `export` keyword to make variables, functions, or classes available for use in other modules.
- **Importing**: Use `import` keyword to bring exported items from other modules into the current module.
- **Relative Paths**: Modules are referenced using relative paths ('./utils.js' in the example) to specify the location of the module file.

**Browser Support**

Support for ES Modules (ECMAScript modules) with `type='module'` is widely available in modern browsers. Older browsers may not fully support this feature, so transpilation or polyfills may be necessary for compatibility.

**Summary**

- `type='module'`: Indicates that a `<script>` tag is loading an ES module.
- `Modules in JavaScript`: Provide a way to organize code into reusable components with clear boundaries of encapsulation.
- `Benefits`: Encourage modular and maintainable code, facilitate code reuse, and improve dependency management.

Using modules with `type='module'` is a standard practice in modern JavaScript development for building scalable and maintainable applications.

</details>
</details>
<details>
<summary>
<h3>17. What is DOM</h3>
</summary>

DOM stands for Document Object Model. It is a programming interface for web documents. When a web page is loaded, the browser creates a Document Object Model of the page, which is an object-oriented representation of the page structure that JavaScript can manipulate.

**Key Concepts of DOM:**

1. **Document**: The entire HTML document is represented as a tree structure of objects.
1. **Object**: Each element, attribute, and text node in the HTML document becomes an object in the DOM.
1. **Model**: The DOM provides a structured representation of the document, allowing programming languages like JavaScript to manipulate the structure, style, and content of the web pages.

**Example of DOM Structure:**

Consider the following simple HTML document:

```js
<!DOCTYPE html>
<html>
<head>
  <title>DOM Example</title>
</head>
<body>
  <h1>Hello, DOM!</h1>
  <p>This is a paragraph.</p>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
</body>
</html>

```

When this document is loaded into a web browser, it creates a structured representation like this:

- Document (html): Represents the entire HTML document.
  - Element (head): Represents the `<head>` element.
    - Element (title): Represents the `<title>` element.
      - Text Node: Represents the text "DOM Example".
  - Element (body): Represents the `<body>` element.
    - Element (h1): Represents the `<h1>` element.
      - Text Node: Represents the text "Hello, DOM!".
    - Element (p): Represents the `<p>` element.
      - Text Node: Represents the text "This is a paragraph.".
    - Element (ul): Represents the `<ul>` element.
      - Element (li): Represents the first `<li>` element.
        - Text Node: Represents the text "Item 1".
      - Element (li): Represents the second `<li>` element.
        - Text Node: Represents the text "Item 2".

**Manipulating the DOM with JavaScript**

JavaScript can interact with the DOM to:

- **Access Elements**: Find and manipulate elements in the document.
- **Modify Content**: Change text, attributes, or styles of elements.
- **Respond to Events**: Add event listeners to elements for interactivity.

**Example of DOM Manipulation in JavaScript:**

```js
// Accessing elements
let heading = document.querySelector("h1");
let paragraph = document.querySelector("p");

// Modifying content
heading.textContent = "Hello, DOM Manipulation!";
paragraph.textContent = "This paragraph is updated by JavaScript.";

// Adding event listener
heading.addEventListener("click", function () {
  alert("You clicked the heading!");
});
```

**Benefits of Using the DOM**

- **Dynamic Updates**: Allows web pages to change content dynamically based on user actions or other events.
- **Interactivity**: Enables user interaction through forms, buttons, and other elements.
- **Cross-platform**: Provides a standardized way for web browsers and programming languages to interact with web documents.

In summary, the Document Object Model (DOM) is a crucial concept in web development, providing a structured representation of HTML documents that can be manipulated and interacted with using programming languages like JavaScript.

</details>
</details>
<details>
<summary>
<h3>18. Why need DOM</h3>
</summary>

The Document Object Model (DOM) is essential in web development for several reasons, primarily due to its role in enabling interactive, dynamic web applications. Here are the main reasons why the DOM is needed:

1. **Structured Representation of the Document**

The DOM provides a structured, hierarchical representation of the web document, allowing developers to understand and manipulate the structure, style, and content of web pages. This hierarchical structure is represented as a tree of objects, making it easier to navigate and interact with the various elements of the document.

2. **Dynamic Content Manipulation**

With the DOM, developers can dynamically change the content of a web page without reloading it. This capability is crucial for creating interactive and user-friendly web applications. For example, you can:

- Add or remove elements (e.g., buttons, images, sections).
- Modify the content of existing elements (e.g., text within a paragraph).
- Change attributes of elements (e.g., updating the src attribute of an image).

3. **Interactivity and Event Handling**

The DOM allows developers to respond to user actions such as clicks, form submissions, key presses, and other events. By adding event listeners to DOM elements, developers can create interactive applications that react to user input. For example:

- Showing a message when a button is clicked.
- Validating form input in real-time.
- Animating elements when the user scrolls.

4. **Styling and CSS Manipulation**

Through the DOM, developers can manipulate the styles of elements programmatically. This includes changing CSS properties dynamically to reflect changes in the application state. For example:

- Highlighting a menu item when it is hovered over.
- Expanding or collapsing sections based on user interaction.
- Changing themes (e.g., from light mode to dark mode).

5. **Access and Update Elements Easily**

The DOM provides methods to easily access and update elements in the document. Methods like `getElementById, getElementsByClassName, querySelector,` and `querySelectorAll` allow developers to find and manipulate elements efficiently.

6. **API for Other Technologies**

The DOM serves as an API for other web technologies, enabling seamless integration with JavaScript, CSS, and other frameworks and libraries. Many modern JavaScript frameworks (e.g., React, Angular, Vue) rely on the DOM to update the user interface efficiently and provide a declarative way to manage the UI.

**Example**

Here's a simple example demonstrating some of the DOM capabilities:

```js
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>DOM Example</title>
<style>
  #dynamic-content {
    color: blue;
  }
</style>
</head>
<body>
  <h1 id="title">Welcome to the DOM Example</h1>
  <p id="dynamic-content">This text will change.</p>
  <button id="change-text-button">Change Text</button>

  <script>
    // Accessing elements
    const title = document.getElementById('title');
    const dynamicContent = document.getElementById('dynamic-content');
    const button = document.getElementById('change-text-button');

    // Changing the content of the paragraph
    button.addEventListener('click', () => {
      dynamicContent.textContent = 'The text has been changed!';
      dynamicContent.style.color = 'red'; // Changing the style
    });

    // Changing the title text on page load
    title.textContent = 'DOM Manipulation Example';
  </script>
</body>
</html>

```

**In this example:**

- The `title` and `dynamic-content` elements are accessed and manipulated to change their text content.
- An event listener is added to the button to change the text and style of the paragraph when the button is clicked.

**Conclusion**

The DOM is fundamental to web development because it provides the means to dynamically interact with and manipulate the web document. It enables the creation of interactive, dynamic, and responsive web applications, making it an essential concept for web developers to understand and utilize effectively.

</details>
</details>
<details>
<summary>
<h3>19. What is Event Bubbling and Event Capturing</h3>
</summary>

Event bubbling and event capturing are two phases in the event propagation process in the DOM. Understanding these concepts is crucial for effectively managing events in web development.

**Event Propagation**

When an event occurs in the DOM (e.g., a click), it doesn't just trigger the event handler on the target element. Instead, it goes through a three-phase process:

1. **Event Capturing (or Trickling)**: The event starts from the root of the document and travels down to the target element.
1. **Target Phase:** The event reaches the target element.
1. **Event Bubbling**: The event bubbles up from the target element back to the root.

**Event Capturing**

In the capturing phase, also known as trickling, the event moves from the root of the document to the target element. Handlers registered for this phase will be triggered first, before the target element itself handles the event.

**Event Bubbling**

In the bubbling phase, the event propagates from the target element back up to the root of the document. Handlers registered for this phase will be triggered after the target element handles the event.

**Example to Illustrate Event Bubbling and Capturing**

Consider the following HTML structure:

```js
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Event Bubbling and Capturing</title>
</head>
<body>
  <div id="outer">
    <div id="inner">
      <button id="button">Click Me</button>
    </div>
  </div>

  <script>
    const outer = document.getElementById('outer');
    const inner = document.getElementById('inner');
    const button = document.getElementById('button');

    // Event listener for capturing phase
    outer.addEventListener('click', () => {
      console.log('Outer DIV (Capturing)');
    }, true);

    inner.addEventListener('click', () => {
      console.log('Inner DIV (Capturing)');
    }, true);

    button.addEventListener('click', () => {
      console.log('Button (Capturing)');
    }, true);

    // Event listener for bubbling phase
    outer.addEventListener('click', () => {
      console.log('Outer DIV (Bubbling)');
    });

    inner.addEventListener('click', () => {
      console.log('Inner DIV (Bubbling)');
    });

    button.addEventListener('click', () => {
      console.log('Button (Bubbling)');
    });
  </script>
</body>
</html>

```

**Explanation**

- Event Capturing Phase: The third argument in addEventListener is true, indicating that the event listener should be invoked during the capturing phase.
- Event Bubbling Phase: The default phase when the third argument is false or omitted, indicating that the event listener should be invoked during the bubbling phase.

When you click the button, the console output will be:

1. Capturing Phase:

   - Outer DIV (Capturing)
   - Inner DIV (Capturing)
   - Button (Capturing)

1. Target Phase:

   - Button (Triggered during capturing or bubbling, depending on the listener)

1. Bubbling Phase:

   - Button (Bubbling)
   - Inner DIV (Bubbling)
   - Outer DIV (Bubbling)

**Event Propagation Control**

You can control event propagation using the following methods:

- `event.stopPropagation():` Stops the event from propagating further in both capturing and bubbling phases.
- `event.stopImmediatePropagation():` Stops the event from propagating further and prevents other listeners on the same element from being called.
- `event.preventDefault()`: Prevents the default action associated with the event (e.g., navigating to a link's href).

**Example with Propagation Control**

```js
button.addEventListener("click", (event) => {
  console.log("Button Clicked");
  event.stopPropagation(); // Stops the event from bubbling up
});
```

**Conclusion**

Understanding event bubbling and event capturing is essential for managing complex event interactions in web applications. These concepts allow you to control how events are propagated through the DOM, giving you more flexibility and control over your event handling logic

</details>
</details>
<details>
<summary>
<h3>20. What is Closure</h3>
</summary>

In JavaScript, a closure is a feature that allows a function to retain access to its lexical scope, even when that function is executed outside of its original scope. This means that a function defined inside another function (an inner function) retains access to the variables and parameters of its outer function, even after the outer function has finished executing.

**How Closures Work**

Closures are created whenever a function is defined inside another function, allowing the inner function to access variables from the outer function's scope. This captured environment is referred to as the closure.

**Example of a Closure**

Here’s a simple example to illustrate closures:

```js
function outerFunction() {
  let outerVariable = "I am an outer variable";

  function innerFunction() {
    console.log(outerVariable); // Can access outerVariable
  }

  return innerFunction;
}

const closure = outerFunction();
closure(); // Output: 'I am an outer variable'
```

In this example:

- `outerFunction` defines a variable `outerVariable` and an inner function `innerFunction`.
- `innerFunction` has access to `outerVariable` because it is defined within the same `lexical scope`.
- `outerFunction` returns `innerFunction`, which is then assigned to the variable `closure`.
- Even though `outerFunction` has finished executing, `innerFunction` retains access to `outerVariable` when it is called.

**Practical Use Cases of Closures**

1.  `Data Privacy:` Closures can create private variables that cannot be accessed directly from outside the function.

    ```js
    function createCounter() {
      let count = 0;

      return {
        increment: function () {
          count++;
          return count;
        },
        decrement: function () {
          count--;
          return count;
        },
      };
    }

    const counter = createCounter();
    console.log(counter.increment()); // Output: 1
    console.log(counter.increment()); // Output: 2
    console.log(counter.decrement()); // Output: 1
    ```

1.  `Function Factories`: Closures can generate specific functions based on given parameters.

    ```js
    function createMultiplier(multiplier) {
      return function (number) {
        return number * multiplier;
      };
    }

    const double = createMultiplier(2);
    const triple = createMultiplier(3);

    console.log(double(5)); // Output: 10
    console.log(triple(5)); // Output: 15
    ```

1.  `Maintaining State`: Closures can maintain the state across multiple function calls.

    ````js
    function makeAdder(x) {
    return function(y) {
    return x + y;
    };
    }

        const add5 = makeAdder(5);
        const add10 = makeAdder(10);

        console.log(add5(2)); // Output: 7
        console.log(add10(2)); // Output: 12

        ```

    **Advantages of Closures**
    ````

- `Encapsulation`: Closures provide a way to encapsulate and protect variables from being accessed or modified directly.
- `State Preservation`: Closures allow functions to retain and manage state over multiple invocations.
- `Modular Code:` Closures help in creating modular and maintainable code by promoting function factories and private variables.

**Common Pitfalls and Considerations**

- **Memory Leaks:** Closures can inadvertently cause memory leaks if they retain references to large objects or DOM elements.
- **Performanc**: Excessive use of closures can lead to performance issues due to the increased memory consumption for maintaining the outer scope.
- **Debuggin**: Debugging closures can be challenging, especially when dealing with asynchronous code or complex nesting.

**Conclusion**

Closures are a fundamental and powerful feature of JavaScript, enabling sophisticated patterns for encapsulating and managing state, creating private variables, and generating functions dynamically. Understanding and mastering closures is essential for writing effective and maintainable JavaScript code.

</details>
</details>
<details>
<summary>
<h3>21. What is use-strict</h3>
</summary>

In JavaScript, "use strict" is a directive that enables strict mode, a way to opt into a restricted variant of JavaScript. Strict mode helps catch common coding errors, prevents the use of certain potentially problematic language features, and generally improves the robustness of your code.

**Enabling Strict Mode**

Strict mode can be enabled in two ways:

1.  **Globally in a Script**: To enable strict mode for an entire script, place "use strict"; at the beginning of the file.

    ```js
    "use strict";

    // Entire script is in strict mode
    var x = 3.14;
    ```

1.  **Locally in a Function**: To enable strict mode only within a specific function, place "use strict"; at the beginning of the function body.

    ````js
    function myFunction() {
    "use strict";

          // Function body is in strict mode
          var y = 3.14;
        }

        ```

    **Benefits of Using Strict Mode**

    ````

1.  **Eliminates Silent Errors**: Strict mode converts silent errors into explicit errors. This helps catch bugs early in the development process.

    ```js
    "use strict";
    x = 3.14; // ReferenceError: x is not defined
    ```

1.  **Prevents Accidental Globals**: Variables must be declared with var, let, or const. Assigning to an undeclared variable will throw an error.

    ```js
    "use strict";
    y = 3.14; // ReferenceError: y is not defined
    ```

1.  **Disallows Duplicates**: Duplicate parameter names in functions are not allowed.

    ```js
    "use strict";
    function sum(a, a, c) {
      // SyntaxError: Duplicate parameter name not allowed in this context
      return a + a + c;
    }
    ```

1.  **Secures this Context:** In strict mode, the value of this is undefined in functions that are not called as methods.

    ```js
    "use strict";
    function showThis() {
      console.log(this); // undefined
    }
    showThis();
    ```

1.  **Disallows Octal Syntax**: Octal literals (numbers prefixed with 0) are not allowed.

    ```js
    "use strict";
    var num = 010; // SyntaxError: Octal literals are not allowed in strict mode
    ```

1.  **Restricts eval and arguments**: The use of eval and arguments are more restricted, preventing certain modifications that could lead to difficult-to-debug issues.

    ````js
    "use strict";
    eval("var z = 2");
    console.log(z); // ReferenceError: z is not defined

        arguments.callee; // TypeError: 'arguments.callee' is not allowed in strict mode

        ```

    **Potential Issues and Considerations**
    ````

- `Legacy Code`: Adding strict mode to legacy code may cause it to break if the code contains patterns that are disallowed in strict mode.
- `Third-Party Libraries`: Ensure that third-party libraries you use are compatible with strict mode.
- `Global Scope`: Enabling strict mode globally in a script affects all code within the script, including third-party libraries that may not expect strict mode.

**Example**

```js
"use strict";

function strictFunction() {
  var x = 3.14;
  console.log(x); // 3.14

  // The following line will throw an error because y is not declared
  // y = 2.72; // ReferenceError: y is not defined
}

strictFunction();
```

In this example, strict mode is enabled globally for the script. The `strictFunction` works correctly when `x` is declared, but would throw an error if `y` is assigned without declaration.

**Conclusion**

Strict mode is a valuable feature in JavaScript that helps developers write cleaner, more robust code by catching common errors and preventing certain problematic language features. It is highly recommended to use strict mode in modern JavaScript development to improve code quality and maintainability.

</details>
</details>
<details>
<summary>
<h3>22. What is Destructuring </h3>
</summary>

Destructuring in JavaScript is a convenient way of extracting values from arrays or properties from objects and assigning them to variables. It allows for more concise and readable code by directly unpacking values from data structures.

**Array Destructuring**

Array destructuring allows you to unpack values from arrays into distinct variables.

**Basic Example**

```js
const fruits = ["Apple", "Banana", "Cherry"];

const [first, second, third] = fruits;

console.log(first); // Output: Apple
console.log(second); // Output: Banana
console.log(third); // Output: Cherry
```

**Skipping Elements**

You can skip elements in the array by leaving gaps in the destructuring pattern.

```js
const colors = ["Red", "Green", "Blue"];

const [, , third] = colors;

console.log(third); // Output: Blue
```

**Default Values**

You can provide default values in case the array doesn't have enough elements.

```js
const numbers = [1, 2];

const [a, b, c = 3] = numbers;

console.log(c); // Output: 3
```

**Swapping Variables**

Destructuring can be used to swap variables without using a temporary variable.

```js
let x = 1;
let y = 2;

[x, y] = [y, x];

console.log(x); // Output: 2
console.log(y); // Output: 1
```

**Object Destructuring**

Object destructuring allows you to unpack properties from objects into distinct variables.

Basic Example

```js
const person = {
  name: "John Doe",
  age: 30,
  profession: "Developer",
};

const { name, age, profession } = person;

console.log(name); // Output: John Doe
console.log(age); // Output: 30
console.log(profession); // Output: Developer
```

**Renaming Variables**

You can rename the variables while destructuring.

```js
const person = {
  name: "Jane Doe",
  age: 25,
};

const { name: fullName, age: years } = person;

console.log(fullName); // Output: Jane Doe
console.log(years); // Output: 25
```

**Default Values**

You can provide default values for variables if the property doesn't exist in the object.

```js
const person = {
  name: "Alice",
};

const { name, age = 20 } = person;

console.log(age); // Output: 20
```

**Nested Object Destructuring**

You can destructure nested objects by specifying the structure.

```js
const user = {
  id: 1,
  profile: {
    firstName: "Bob",
    lastName: "Smith",
  },
};

const {
  profile: { firstName, lastName },
} = user;

console.log(firstName); // Output: Bob
console.log(lastName); // Output: Smith
```

**Mixed Destructuring**

You can combine array and object destructuring.

```js
const user = {
  id: 1,
  info: ["Alice", "Developer", 30],
};

const {
  info: [name, profession, age],
} = user;

console.log(name); // Output: Alice
console.log(profession); // Output: Developer
console.log(age); // Output: 30
```

**Function Parameters**

Destructuring can be used directly in function parameters to unpack values from arguments.

**Array Parameters**

```js
function greet([firstName, lastName]) {
  console.log(`Hello, ${firstName} ${lastName}`);
}

greet(["John", "Doe"]); // Output: Hello, John Doe
```

**Object Parameters**

```js
function display({ name, age }) {
  console.log(`Name: ${name}, Age: ${age}`);
}

display({ name: "Jane Doe", age: 28 }); // Output: Name: Jane Doe, Age: 28
```

**Conclusion**

Destructuring in JavaScript is a powerful feature that makes it easier to work with arrays and objects by allowing you to extract values and assign them to variables in a concise and readable manner. It simplifies code and reduces the need for multiple lines of assignments, making your code more maintainable and expressive.

</details>

<details>
<summary>
<h3>23. What is Currying</h3>
</summary>

Currying is a functional programming technique where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument. In JavaScript, currying allows functions to be more flexible and reusable.

**Example of Currying in JavaScript**

Let's start with a simple example of a function that adds three numbers:

```js
function add(a, b, c) {
  return a + b + c;
}

console.log(add(1, 2, 3)); // Output: 6
```

To convert this add function to a curried version, we transform it so that it takes one argument at a time:

```js
function curryAdd(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}

console.log(curryAdd(1)(2)(3)); // Output: 6
```

**Practical Example: Currying for Configuration**

Currying can be particularly useful for creating functions that require configuration or for handling partial application of functions.

**Scenario: Creating a Curried Logging Function**

Consider a logging function that logs messages with different levels (info, warn, error). Using currying, we can create a configurable logger:

```js
function createLogger(level) {
  return function (message) {
    console.log(`[${level}] ${message}`);
  };
}

const infoLogger = createLogger("INFO");
const warnLogger = createLogger("WARN");
const errorLogger = createLogger("ERROR");

infoLogger("This is an informational message.");
warnLogger("This is a warning message.");
errorLogger("This is an error message.");
```

**Explanation:**

1. Curried Function: createLogger is a curried function that takes a level argument and returns another function that takes a message argument.
1. Creating Loggers: By calling createLogger with different levels, we create specific logging functions (infoLogger, warnLogger, errorLogger).
1. Logging Messages: These specific logging functions can be used to log messages with their respective levels.

**More Advanced Currying: General Utility Function**

We can create a general-purpose currying function that can transform any function into its curried form:

```js
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    } else {
      return function (...nextArgs) {
        return curried.apply(this, args.concat(nextArgs));
      };
    }
  };
}

// Example function to curry
function multiply(a, b, c) {
  return a * b * c;
}

const curriedMultiply = curry(multiply);

console.log(curriedMultiply(2)(3)(4)); // Output: 24
console.log(curriedMultiply(2, 3)(4)); // Output: 24
console.log(curriedMultiply(2)(3, 4)); // Output: 24
```

**Explanation:**

1. **General `curry` Function:** The `curry` function takes any function `fn` and returns its curried version.
1. **Curried Function:** The `curried` function checks if the number of provided arguments is sufficient to call the original function `fn`. If so, it calls `fn` with all arguments. Otherwise, it returns a new function that continues to collect arguments.
1. **Example Usage:** We use `curry` to transform the `multiply` function into a curried version, allowing us to call it with arguments one at a time or in groups.

Currying can significantly enhance the flexibility and reusability of functions in JavaScript, making it a powerful tool in functional programming.

</details>
<details>
<summary>
<h3>24. What is difference between Arrow and Normal Function</h3>
</summary>
Arrow functions and normal (traditional) functions in JavaScript have several differences in syntax and behavior. Here are the key differences:

Syntax
Arrow Function Syntax:

```js
const add = (a, b) => a + b;
```

Normal Function Syntax:

```js
function add(a, b) {
  return a + b;
}
```

`this` Binding

**Arrow Functions:**

- Do not have their own `this` context. They inherit `this` from the parent scope (lexical scoping).
- Cannot be used as constructors (i.e., they can't be used with the `new` keyword).

```js
const obj = {
  value: 42,
  arrowFunc: () => console.log(this.value), // 'this' is inherited from the surrounding scope
  normalFunc() {
    console.log(this.value); // 'this' refers to the obj context
  },
};

obj.arrowFunc(); // undefined (or global object's `value` in non-strict mode)
obj.normalFunc(); // 42
```

**Normal Functions:**

- Have their own `this` context, which is determined by how the function is called.
- Can be used as constructors.

```js
function NormalFunction() {
  this.value = 42;
}

const instance = new NormalFunction();
console.log(instance.value); // 42
```

**Arguments Object**

Arrow Functions:

- Do not have their own `arguments` object. They inherit `arguments` from the parent scope.

```js
const arrowFunc = () => {
  console.log(arguments); // References arguments of the enclosing scope, not the arrow function itself
};
arrowFunc(1, 2, 3); // Throws a ReferenceError if no arguments object exists in the parent scope
```

**Normal Functions:**

- Have their own `arguments` object, which contains all the arguments passed to the function.

```js
function normalFunc() {
  console.log(arguments); // [1, 2, 3]
}
normalFunc(1, 2, 3);
```

**Constructor Usage**

Arrow Functions:

- Cannot be used as constructors and will throw an error if used with the `new` keyword.

```js
const ArrowFunc = () => {};
const instance = new ArrowFunc(); // TypeError: ArrowFunc is not a constructor
```

**Normal Functions:**

- Can be used as constructors with the `new` keyword.

```js
function NormalFunc() {}
const instance = new NormalFunc(); // Works fine
```

**Implicit Return**

Arrow Functions:

- Can have an implicit return, meaning if the function body is a single expression, it can be returned without the `return` keyword.

```js
const add = (a, b) => a + b;
```

**Normal Functions:**

Require the `return` keyword to return a value.

```js
function add(a, b) {
  return a + b;
}
```

**Methods**

Arrow Functions:

- Not suitable for defining methods in an object due to their `this` binding behavior.

```js
const obj = {
  value: 42,
  arrowFunc: () => console.log(this.value), // `this` is not obj's context
};
obj.arrowFunc(); // undefined
```

**Normal Functions:**

- Suitable for defining methods in an object since `this` refers to the object itself.

```js
const obj = {
  value: 42,
  normalFunc() {
    console.log(this.value); // `this` is obj's context
  },
};
obj.normalFunc(); // 42
```

**Summary**

- **Syntax**: Arrow functions have a more concise syntax.
- **`this` Binding**: Arrow functions inherit `this` from the parent scope; normal functions have their own `this`.
- **Arguments Object**: Arrow functions do not have their own `arguments` object.
- **Constructor**: Arrow functions cannot be used as constructors.
- **Implicit Return**: Arrow functions can have implicit return for single expressions.
- **Methods**: Arrow functions are not suitable for object methods due to their `this` behavior.

Choosing between arrow functions and normal functions depends on the specific use case, particularly with regard to how `this` is handled and whether the function needs to be used as a constructor or have its own arguments object.

</details>
<details>
<summary>
<h3>25. `this` keyword</h3>
</summary>

The `this` keyword in JavaScript is a reference to the current execution context of a function. Its value depends on how the function is called, and it can behave differently in various scenarios. Here are the key points to understand about `this` in JavaScript:

**Global Context**

In the global execution context (outside any function), this refers to the global object.

- In a browser, the global object is window.
- In Node.js, the global object is global.

```js
console.log(this); // In a browser: window, in Node.js: global
```

**Function Context**

In a regular function, the value of this depends on how the function is called.

**Simple Function Call**

When a function is called in the global context, this refers to the global object (in non-strict mode) or is undefined (in strict mode).

```js
function myFunction() {
  console.log(this);
}
myFunction(); // In non-strict mode: window (or global in Node.js), in strict mode: undefined
```

**Method Call**

When a function is called as a method of an object, this refers to the object that owns the method.

```js
const obj = {
  value: 42,
  myMethod: function () {
    console.log(this.value);
  },
};
obj.myMethod(); // 42
```

**Constructor Call**

When a function is used as a constructor (called with the new keyword), this refers to the newly created instance.

```js
function MyConstructor() {
  this.value = 42;
}

const instance = new MyConstructor();
console.log(instance.value); // 42
```

`call`, `apply`, and `bind` Methods
The `call` and `apply` methods can explicitly set the value of this.

```js
function myFunction() {
  console.log(this.value);
}

const obj = { value: 42 };
myFunction.call(obj); // 42
myFunction.apply(obj); // 42
```

The bind method creates a new function with a bound this value.

```js
const boundFunction = myFunction.bind(obj);
boundFunction(); // 42
```

**Arrow Functions**

Arrow functions do not have their own this context. Instead, this is lexically inherited from the enclosing execution context.

```js
const obj = {
  value: 42,
  arrowFunc: () => {
    console.log(this.value); // 'this' refers to the enclosing context, not the obj
  },
};

obj.arrowFunc(); // undefined (or window/global in non-strict mode)
```

**Event Handlers**

In event handlers, this refers to the element that received the event.

```js
const button = document.querySelector("button");
button.addEventListener("click", function () {
  console.log(this); // 'this' refers to the button element
});
```

**Summary of `this` Behavior**

- **Global Context:** `this` refers to the global object (`window` in browsers, `global` in Node.js).
- **Simple Function Call:** `this` refers to the global object (non-strict mode) or undefined (strict mode).
- **Method Call:** `this` refers to the object that owns the method.
- **Constructor Call:** `this` refers to the newly created instance.
- **call, apply, bind:** These methods explicitly set the value of this.
- **Arrow Functions:** `this` is lexically inherited from the enclosing scope.
- **Event Handlers:** `this` refers to the element that received the event.

Understanding how `this` works in different contexts is crucial for writing correct and efficient JavaScript code.

</details>
<details>
<summary>
<h3>26. What is Debouncing</h3>
</summary>

Debouncing in JavaScript is a technique used to limit the rate at which a function gets executed. It ensures that a function is only called after a certain period of inactivity. This is particularly useful for optimizing performance in scenarios where a function might be triggered multiple times in rapid succession, such as during user input events, resizing, or scrolling.

**How Debouncing Works**

When you debounce a function, you delay its execution until a specified amount of time has passed since the last time it was invoked. If the debounced function is called again before the delay period ends, the previous timer is canceled and a new timer is set. This ensures that the function is only executed once after the user has stopped triggering the event for the specified delay period.

**Example Implementation of Debouncing**

Here's how you can implement a debounce function in JavaScript:

```js
function debounce(func, delay) {
  let timeoutId;
  return function (...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => {
      func.apply(this, args);
    }, delay);
  };
}
```

**Usage Example**

Suppose you have an input field where you want to perform a search operation only after the user has stopped typing for 300 milliseconds. You can use the debounce function to achieve this:

```js
<input type="text" id="searchInput" placeholder="Type to search...">

<script>
  const searchInput = document.getElementById('searchInput');

  function performSearch(query) {
    console.log('Searching for:', query);
    // Perform search operation
  }

  const debouncedSearch = debounce(function(event) {
    performSearch(event.target.value);
  }, 300);

  searchInput.addEventListener('input', debouncedSearch);
</script>

```

**Explanation**

1. **Debounce Function:** The debounce function takes two arguments: the function to debounce (func) and the delay in milliseconds (delay). It returns a new debounced function.

1. **Timeout Variable:** A timeoutId variable is used to keep track of the timer. This ensures that the timer is cleared and reset whenever the debounced function is called again before the delay period has elapsed.

1. **Clear Timeout:** The clearTimeout function is called to reset the timer whenever the debounced function is invoked again before the delay period has elapsed.

1. **Set Timeout:** The setTimeout function is used to set a new timer. If the debounced function is not called again within the delay period, the original function (func) is executed.

1. **Event Listener:** An event listener is added to the input field to listen for the input event. The debounced function is called whenever the input event is triggered, ensuring that the performSearch function is only executed once the user has stopped typing for 300 milliseconds.

**Benefits of Debouncing**

- \***\*Performance\*\***: Reduces the number of times a function is called, improving the performance of your application.
- \***\*Efficiency\*\***: Ensures that the function is only executed when necessary, after user input has settled.
- \***\*Better User Experience:\*\*** Prevents unnecessary function calls and potential lag, leading to a smoother user experience.

**Common Use Cases**

1. **Search Boxes:** Delaying search queries until the user has finished typing.
1. **Resize Events:** Handling window resize events without triggering multiple times per second.
1. **Scrolling:** Managing scroll events efficiently to improve performance.

Debouncing is a powerful technique for optimizing event handling in JavaScript and is especially useful in scenarios where events are triggered frequently in a short period.

</details>
<details>
<summary>
<h3>27. What is Critical Rendering path</h3>
</summary>

The Critical Rendering Path (CRP) is a concept in web development that refers to the sequence of steps the browser takes to convert HTML, CSS, and JavaScript into pixels on the screen. Understanding the CRP helps optimize web performance by minimizing the time it takes for a web page to become visible and interactive to users. Here are the main stages involved:

1. Document Object Model (DOM) Construction:

   - The browser parses HTML and builds the DOM tree, which represents the structure of the web page.

1. CSS Object Model (CSSOM) Construction:

   - The browser parses CSS and constructs the CSSOM tree, representing the styles of the elements in the web page.

1. Render Tree Construction:

   - The browser combines the DOM and CSSOM trees to create the Render Tree. The Render Tree only includes the nodes required for rendering the page (e.g., hidden elements are excluded).

1. Layout (Reflow):

   - The browser calculates the position and size of each element in the Render Tree. This step is also known as reflow.

1. Painting:

   - The browser converts the Render Tree into actual pixels on the screen, painting the elements in their calculated positions and styles.

**Optimization Techniques**

To optimize the Critical Rendering Path, web developers can focus on the following:

1. Minimize Critical Resources:

   - Reduce the number of critical resources that block rendering, such as CSS and JavaScript files.
   - Use asynchronous loading for non-critical JavaScript.

1. Optimize Resource Delivery:

   - Compress and minify CSS and JavaScript files to reduce their size.
   - Use caching strategies to store frequently used resources locally.

1. Reduce Render-Blocking CSS and JavaScript:

   - Inline critical CSS and defer non-critical CSS.
   - Defer or asynchronously load JavaScript that is not critical for initial rendering.

1. Prioritize Visible Content:

   - Optimize the above-the-fold content to ensure that the critical parts of the web page load and render first.

By understanding and optimizing the Critical Rendering Path, developers can significantly improve the performance and user experience of their web pages.

</details>
<details>
<summary>
<h3></h3>
</summary>
</details>
