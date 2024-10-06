## JavaScript String Manipulation and Methods

### 1\. String Interpolation (Template Literals)

In JavaScript, a modern way to concatenate strings and variables is by using **template literals**. This allows for more readable code and easier insertion of variables into strings.

Example:

```javascript
let variable = "JavaScript";
console.log(`This is the representation of the string: ${variable} &lt;- this is how we include variables in the string.`);
```

The `${variable}` syntax inside backticks (`` ` ``) allows you to embed expressions directly into the string.

### 2\. Common String Methods

JavaScript offers several useful methods to manipulate strings. Here are some commonly used methods:

`variable.length`: Returns the length of the string.

`variable.toUpperCase()`: Converts the entire string to uppercase.

`variable.toLowerCase()`: Converts the entire string to lowercase.

`variable.charAt(index)`: Returns the character at the specified index (0-based).

`variable.substring(start, end)`: Extracts characters from the string starting at `start` and up to (but not including) the `end` index.

`variable.slice(start, end)`: Similar to `substring()`, but also supports negative indices, allowing you to slice from the end of the string.

`variable.trim()`: Removes leading and trailing white spaces, which is especially useful for cleaning input data in forms.

`variable.replace('oldValue', 'newValue')`: Replaces a specified substring or character with a new one in the string.

`variable.includes('substring')`: Checks if the string contains the given substring. Returns `true` or `false`.

`variable.split(separator)`: Splits the string into an array of substrings based on the specified separator. Example:

### 3\. Removing Leading and Trailing White Spaces and Reducing Multiple Spaces

In some cases, you may want to not only remove leading and trailing white spaces but also reduce any extra spaces within the string to a single space. This can be achieved by combining `trim()` with `replace()` using a regular expression.

Example:

```javascript
let str = "   Hello   World!   ";
let cleanedStr = str.trim().replace(/\s+/g, ' ');
console.log(cleanedStr);  // Output: "Hello World!"
```

In this example, `trim()` removes leading and trailing spaces, and `replace(/\s+/g, ' ')` replaces multiple spaces within the string with a single space.

```javascript
let str = "my-name-is";
let result = str.split('-');  // ['my', 'name', 'is']
```
---

## Stack and Heap Memory in JavaScript

In JavaScript, memory is managed using two main types of storage: **stack** and **heap**. Each plays a critical role in how variables are stored and accessed, depending on whether the data is primitive or non-primitive.

### 1. Stack
The **stack** is used to store **primitive values** like numbers, strings, booleans, `null`, and `undefined`. The key feature of stack memory is that it stores copies of the values directly. This means that each variable has its own separate copy, and changing one variable does not affect the others.

Example (Stack memory):
```javascript
let myEmail = "prathameshpise6@gmail.com";
let newEmail = myEmail;
```
In the above code, both `myEmail` and `newEmail` store their values separately in the stack. Even though `newEmail` is initially assigned the value of `myEmail`, it gets its own copy of the value.

```javascript
newEmail = "theprathamesh07@gmail.com";
console.log(myEmail);  // Output: "prathameshpise6@gmail.com"
console.log(newEmail);  // Output: "theprathamesh07@gmail.com"
```
Here, changing `newEmail` does not affect `myEmail` because primitive data types are stored independently in the stack.

### 2. Heap
The **heap** is used for storing **non-primitive values** like objects and arrays. When you assign an object to a variable, only the **reference** to the object is stored in the stack, while the actual object is stored in the heap. Multiple variables can reference the same object in heap memory, meaning that changes made through one reference will affect the others.

Example (Heap memory):
```javascript
let firstVal = {
    id: 101,
    name: 'abc',
};

let secVal = firstVal;  // Both variables reference the same object in heap memory
```
In this example, both `firstVal` and `secVal` reference the same object in the heap, so any changes made to one will reflect in the other.

```javascript
secVal.id = 102;
console.log(firstVal);  // Output: { id: 102, name: 'abc' }
console.log(secVal);    // Output: { id: 102, name: 'abc' }
```
Since both variables point to the same object in the heap, modifying `secVal` also modifies `firstVal`. They share the same reference, so both log the same object.

### Key Differences
- **Stack memory** is used for primitive values (like numbers and strings) and stores actual values.
- **Heap memory** is used for non-primitive values (like objects and arrays) and stores references to these values.
- **Primitive types** do not affect each other because they are stored independently.
- **Non-primitive types** (such as objects) share the same reference, so changes to one variable can affect others referencing the same object.

---
## Working with Arrays in JavaScript

Arrays in JavaScript are dynamic and can hold multiple values of different types, such as numbers, strings, and booleans. They allow for storing, manipulating, and accessing a list of elements in a single variable.

### 1. Array Initialization

There are different ways to initialize arrays in JavaScript:

- Using square brackets `[]` (literal notation):
  ```javascript
  const myArr = [1, 2, 3, 'a', true];
  console.log(myArr);  // Output: [1, 2, 3, "a", true]
  ```
  This method allows an array to store mixed data types (numbers, strings, booleans, etc.).

- Using the `Array` constructor:
  ```javascript
  const myArray2 = new Array(1, 2, 3, 4);
  console.log(myArray2);  // Output: [1, 2, 3, 4]
  ```

Arrays in JavaScript are **dynamic**, meaning their size can change, and you can add or remove elements at runtime.

### 2. Shallow Copy (Stack and Heap Reference)

JavaScript arrays are stored in heap memory, meaning when you assign an array to another variable, you’re copying the **reference** (not the actual array). This can lead to unintended behavior when modifying arrays.

Example:
```javascript
let originalArr = [1, 2, 3];
let copiedArr = originalArr;  // Shallow copy, both point to the same array in heap memory
copiedArr.push(4);
console.log(originalArr);  // Output: [1, 2, 3, 4] (modified)
console.log(copiedArr);    // Output: [1, 2, 3, 4] (same)
```

### 3. Array Methods

JavaScript provides several built-in methods to work with arrays:

1. **`push(value)`**: Adds a value to the end of the array.
   ```javascript
   myArr.push(7);
   console.log(myArr);  // Output: [1, 2, 3, "a", true, 7]
   ```

2. **`pop()`**: Removes the last value from the array.
   ```javascript
   myArr.pop();
   console.log(myArr);  // Output: [1, 2, 3, "a", true]
   ```

3. **`unshift(value)`**: Inserts a value at the start of the array.
   ```javascript
   myArr.unshift(9);
   console.log(myArr);  // Output: [9, 1, 2, 3, "a", true]
   ```
   Note: This operation can be time-consuming because it shifts all elements.

4. **`shift()`**: Removes the first value from the array.
   ```javascript
   myArr.shift();
   console.log(myArr);  // Output: [1, 2, 3, "a", true]
   ```

5. **`join()`**: Joins the elements of an array into a string.
   ```javascript
   let joinedArr = myArr.join('-');
   console.log(joinedArr);  // Output: "1-2-3-a-true"
   ```

6. **`slice(start, end)`**: Returns a shallow copy of a portion of an array.
   ```javascript
   let slicedArr = myArr.slice(1, 3);
   console.log(slicedArr);  // Output: [2, 3]
   ```

7. **`splice(index, numToDelete)`**: Adds/removes elements to/from an array and modifies the original array.
   ```javascript
   myArr.splice(1, 2);  // Removes 2 elements starting from index 1
   console.log(myArr);  // Output: [1, "a", true]
   ```

8. **`concat(array)`**: Combines two or more arrays into one.
   ```javascript
   let arr1 = [1, 2];
   let arr2 = [3, 4];
   let combinedArr = arr1.concat(arr2);
   console.log(combinedArr);  // Output: [1, 2, 3, 4]
   ```

9. **`flat(depth)`**: Flattens nested arrays to the specified depth.
   ```javascript
   let nestedArr = [1, [2, [3, [4]]]];
   console.log(nestedArr.flat(2));  // Output: [1, 2, 3, [4]]
   ```

10. **`Array.from(string)`**: Converts a string into an array.
    ```javascript
    let str = "hello";
    let arrFromString = Array.from(str);
    console.log(arrFromString);  // Output: ['h', 'e', 'l', 'l', 'o']
    ```

### 4. Passing Arrays Inside Arrays

You can nest arrays within other arrays, which results in a multi-dimensional array:
```javascript
let nestedArray = [[1, 2], [3, 4]];
console.log(nestedArray);  // Output: [[1, 2], [3, 4]]
```
To flatten such nested arrays, you can use the `flat()` method as shown earlier.

---
## Working with Objects in JavaScript

In JavaScript, **objects** are a fundamental way to group and store data. They are used to represent entities, where properties (key-value pairs) hold information related to that entity.

### 1. Ways to Initialize an Object

There are two primary ways to initialize an object in JavaScript:

#### 1.1 Literal Notation
This is the most common and straightforward way to create an object. You define the object using curly braces `{}`.

```javascript
const JsUser = {
  Fname: 'Prathamesh',
  id: 101,
  age: 20,
  email: 'prathameshpise6@gmail.com',
  "name IS": "thelite"  // Using quotes for keys with spaces
};
```

#### 1.2 Singleton/Object Constructor
A **singleton** object is created using the `new Object()` constructor.

```javascript
const instaUser = new Object();  // Creates an empty singleton object
const anotherUser = {};          // Creates an empty non-singleton object (literal notation)
```

### 2. Accessing Object Properties

You can access the properties of an object in two ways:

1. **Dot notation** (for standard keys):
   ```javascript
   console.log(JsUser.Fname);  // Output: "Prathamesh"
   ```

2. **Bracket notation** (for keys with spaces or symbols):
   ```javascript
   console.log(JsUser["name IS"]);  // Output: "thelite"
   ```

### 3. Modifying Object Properties

You can easily modify the properties of an object after initialization:

```javascript
instaUser.id = "thelite_editx";
instaUser.email = "theprathamesh07@gmail.com";
instaUser.isLoggedIn = false;

console.log(instaUser);  // Output: { id: "thelite_editx", email: "theprathamesh07@gmail.com", isLoggedIn: false }
```

### 4. Object Methods

JavaScript objects come with built-in methods. One useful method is `Object.freeze()`, which prevents the modification of object properties.

```javascript
Object.freeze(instaUser);  // instaUser is now immutable (cannot be modified)
```

### 5. Nested Objects

Objects can contain other objects as properties, forming a nested structure.

```javascript
const regularUser = {
  id: "thelite_code",
  name: {
    fname: "Prathamesh"
  }
};

console.log(regularUser.name.fname);  // Output: "Prathamesh"
```

### 6. Combining Objects

There are several ways to combine or merge objects in JavaScript:

- **Using `Object.assign()`**:
  ```javascript
  const obj3 = Object.assign({}, obj1, instaUser);  // Merges obj1 and instaUser into a new object obj3
  ```

- **Using the Spread Operator (`...`)**:
  ```javascript
  const mergedObj = { ...instaUser, ...obj3 };
  console.log(mergedObj);
  ```

### 7. Objects Inside Arrays

Objects can be stored inside arrays, and you can access them using array indices.

```javascript
const arr = [
  { id: 1, name: "Nam" },
  { lname: "Head" }
];

console.log(arr[0].name);  // Output: "Nam"
```

### 8. Checking if a Property Exists in an Object

The `hasOwnProperty()` method checks if a specific property exists in an object.

```javascript
const arrprop = {
  id: 101,
  email: "the"
};

console.log(arrprop.hasOwnProperty('id'));  // Output: true
console.log(arrprop.hasOwnProperty('name'));  // Output: false
```

### 9. Object Destructuring

**Destructuring** is a syntax used to unpack values from arrays or properties from objects into distinct variables. It’s particularly useful when working with APIs.

```javascript
const course = {
  name: "JavaScript Basics",
  id: 101
};

// Destructuring
const { name } = course;
console.log(name);  // Output: "JavaScript Basics"
```

---

## JSON in JavaScript

JSON (JavaScript Object Notation) is a lightweight data-interchange format. In JSON, all keys must be strings, and it supports data types like arrays, objects, numbers, strings, booleans, and `null`.

### JSON Example:
```json
{
  "name": "ABC",
  "id": "101"
}
```

### API Response in JSON Format:
APIs often return data in JSON format, which can be either an array of objects or a single object.
```json
[
  { "name": "John", "age": 25 },
  { "name": "Jane", "age": 30 }
]
```

---

## Functions in JavaScript

Functions are blocks of code designed to perform a specific task. They are executed when called.

### Function Example:
```javascript
function sum(a, b) {
  let c = a + b;
  return c;
}

console.log(sum(2, 5));  // Output: 7
```

### Functions Assigned to Variables:
```javascript
const result = sum(5, 5);
console.log(result);  // Output: 10
```

### Default Parameters in Functions:
You can assign default values to function parameters, which will be used if no argument is passed.
```javascript
function isLoggedIn(user = 'guest') {
  console.log(`${user} is logged in.`);
}

isLoggedIn();  // Output: "guest is logged in."
isLoggedIn('John');  // Output: "John is logged in."
```

### Working with Objects and Arrays in Functions:
```javascript
// Handling an Object
const user = { id: 101, name: "Prathamesh" };

function handleObject(any) {
  console.log(`${any.id} is the user ID.`);
}

handleObject(user);  // Output: "101 is the user ID."

// Handling an Array
const myArray = [1, 2, 6, 4];

function getTheArray(any) {
  return any[1];
}

console.log(getTheArray(myArray));  // Output: 2
```

---

## Rest Operator (`...`) in Functions

The **rest operator** (`...`) allows functions to accept an indefinite number of arguments as an array. It's useful when the number of arguments is unknown.

### Example:
```javascript
function shoppingList(...items) {
  console.log(items);
}

shoppingList('Milk', 'Bread', 'Eggs');  // Output: ['Milk', 'Bread', 'Eggs']
```

---

## Scopes in JavaScript

**Scope** refers to the accessibility of variables in different parts of the program. There are three main types of scopes in JavaScript:

1. **Block Scope** (`let`, `const`): Variables declared with `let` and `const` are only accessible within the block (i.e., within curly braces `{}`).
2. **Global Scope**: Variables declared with `var` are accessible throughout the entire program.
3. **Function Scope**: Variables declared inside a function are only accessible within that function.

### Scope Example:
```javascript
let a = 10;  // Block scope
var b = 50;  // Global scope (not recommended)
const c = 60;  // Block scope and immutable

if (true) {
  let a = 20;
  const c = 30;
  console.log(a, c);  // Output: 20 30 (inside block scope)
}

console.log(a, c);  // Output: 10 60 (outside block scope)
```

---

## `this` Keyword in JavaScript

The `this` keyword refers to the current execution context of a function or object. In an object method, `this` refers to the owner object. However, in global contexts, `this` refers to the global object (`window` in browsers).

### Example:
```javascript
const user = {
  userName: 'prathamesh07',
  id: 'thelite',
  
  welcomeMessage: function() {
    console.log(`Welcome ${this.userName} to the website`);
    console.log(this);
  }
};

user.welcomeMessage();

// Changing the context
user.userName = "venkatesh";
user.welcomeMessage();  // Output will use the updated userName
```

> **Note**: When `this` is used in the Node.js environment, it may behave differently compared to the browser, where `this` refers to the global context (`window`).

---

## Arrow Functions in JavaScript

Arrow functions are a shorter syntax for writing functions in JavaScript. They do not bind their own `this`, but instead inherit it from the parent scope (lexical `this`).

### Basic Arrow Function Syntax:
```javascript
const addTwo = (n1, n2) => {
  return n1 + n2;
};

console.log(addTwo(12, 25));  // Output: 37
```

### Arrow Functions and `this`:
Unlike regular functions, arrow functions do not have their own `this`. This can be useful when you want to inherit the `this` context from the surrounding code.

```javascript
const user = {
  userName: 'prathamesh07',
  id: 'thelite',

  welcomeMessage: () => {
    console.log(`Welcome ${this.userName} to the website`);  // 'this' does not refer to user
  }
};

user.welcomeMessage();  // Output: Welcome undefined to the website
```

> **Note**: Be careful when using arrow functions as methods inside objects, as they do not bind their own `this`.

---
## Hoisting in JavaScript

**Hoisting** refers to JavaScript's behavior of moving declarations (variables and functions) to the top of their scope before code execution. Only the declarations are hoisted, not the initializations.

### How Hoisting Works:
- **Variable hoisting:** Variables declared with `var` are initialized with `undefined`. However, variables declared with `let` and `const` are hoisted but not initialized, resulting in a **ReferenceError** if accessed before their declaration.
- **Function hoisting:** Function declarations are hoisted completely, making them callable before they are defined in the code.

### Example:
```javascript
console.log(x);  // Output: undefined (var is hoisted)
var x = 10;

console.log(greeting());  // Output: "Hello" (function is hoisted)
function greeting() {
  return "Hello";
}
```

> **Note:** It's best practice to declare variables at the top of their scope to avoid confusion.

---

## Immediately Invoked Function Expressions (IIFE)

An **IIFE** is a function that runs as soon as it is defined. It helps avoid polluting the global scope, which is particularly useful when working with larger applications.

### Example without IIFE:
```javascript
function one() {
  console.log("Without IIFE");
}
one();  // Output: "Without IIFE"
```

### Example with IIFE:
```javascript
(function two() {
  console.log("With IIFE");
})();  // Output: "With IIFE"
```

### IIFE with Parameters:
```javascript
((name) => {
  console.log(`This is the name: ${name}`);
})('Prathamesh');  // Output: "This is the name: Prathamesh"
```

---

## Event Handling in JavaScript

An **event** is an action that occurs in the browser, like a user clicking a button. Events can be handled using **event listeners** and functions.

### Example of Event Listener:
```javascript
document.getElementById("myButton").addEventListener("click", function() {
  alert("Button clicked!");
});
```

> **Common events**: `click`, `mouseover`, `keydown`, `submit`, etc.

---

## Loops in JavaScript

### **For Loop:**
Used for iterating over arrays or running a block of code a specific number of times.
```javascript
let myArray = [1, 2, 3, 4];
for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}
```

### **Break and Continue:**
- **Break**: Terminates the loop.
- **Continue**: Skips the current iteration and moves to the next one.

### **For Of Loop:**
Efficient for iterating over iterable objects like arrays and strings.
```javascript
let names = ['Prathamesh', 'Nikhil', 'Ajinkya'];
for (const name of names) {
  console.log(name);
}
```

### **For In Loop:**
Used for iterating over the properties of an object or the indexes of an array.
```javascript
let myArray = [10, 20, 30];
for (const index in myArray) {
  console.log(index);  // Output: 0, 1, 2 (index positions)
}
```

### **For Each Loop:**
`forEach` is a method that runs a function for each array element.
```javascript
let loop = [1, 2, 3, 4];
loop.forEach(function(item) {
  console.log(item);  // Output: 1, 2, 3, 4
});
```

> `forEach` does not return a new array, unlike `map` and `filter`.

---

## Maps in JavaScript

**Maps** are used to store key-value pairs and ensure that each key is unique.

### Example:
```javascript
let map = new Map();
map.set('name', 'Prathamesh');
map.set('id', 101);

console.log(map.get('name'));  // Output: "Prathamesh"
```

> Maps differ from objects because they can store objects as keys and preserve the order of insertion.

---

## Higher-Order Functions

### **Filter:**
The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.
```javascript
let myArray = [1, 2, 3, 4, 5, 6];
let newArr = myArray.filter(num => num < 4);
console.log(newArr);  // Output: [1, 2, 3]
```

### **Map:**
The `map()` method creates a new array by applying a function to each element of the original array.
```javascript
let numbers = [1, 2, 3, 4];
let doubled = numbers.map(num => num * 2);
console.log(doubled);  // Output: [2, 4, 6, 8]
```

### **Reduce:**
The `reduce()` method executes a reducer function on each element of the array, resulting in a single output value.
```javascript
let sum = [1, 2, 3, 4].reduce((accumulator, currentValue) => accumulator + currentValue, 0);
console.log(sum);  // Output: 10
```

---