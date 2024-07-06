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
<h3></h3>
</summary>
</details>
<details>
<summary>
<h3></h3>
</summary>
</details>
