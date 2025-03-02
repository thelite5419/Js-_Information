# JavaScript Information README

# JavaScript Data Types

JavaScript has **8 data types**:

1. **String**
2. **Number**
3. **BigInt**
4. **Boolean**
5. **Undefined**
6. **Null**
7. **Symbol**
8. **Object**

## The Object Data Type
The `Object` data type can contain both **built-in objects** and **user-defined objects**:

### Built-in Objects
- Objects
- Arrays
- Dates
- Maps
- Sets
- Typed Arrays (IntArrays, FloatArrays, etc.)
- Promises

### Examples
```javascript
// Numbers:
let length = 16;
let weight = 7.5;

// Strings:
let color = "Yellow";
let lastName = "Johnson";

// Booleans:
let x = true;
let y = false;

// Object:
const person = {firstName: "John", lastName: "Doe"};

// Array object:
const cars = ["Saab", "Volvo", "BMW"];

// Date object:
const date = new Date("2022-03-25");
```

## The Concept of Data Types
Data types are important in programming as they determine how variables are handled.

Example:
```javascript
let x = 16 + "Volvo";
```
JavaScript will treat the number as a string:
```javascript
let x = "16" + "Volvo"; // Output: "16Volvo"
```

JavaScript evaluates expressions from left to right, which can affect the results:
```javascript
let x = 16 + 4 + "Volvo"; // Output: "20Volvo"
let x = "Volvo" + 16 + 4; // Output: "Volvo164"
```

## JavaScript Dynamic Types
JavaScript has **dynamic types**, meaning variables can hold different data types:
```javascript
let x;       // x is undefined
x = 5;       // x is now a number
x = "John";  // x is now a string
```

## JavaScript Data Types in Detail

### Strings
```javascript
let carName1 = "Volvo XC60"; // Double quotes
let carName2 = 'Volvo XC60'; // Single quotes
```

### Numbers
```javascript
let x1 = 34.00; // With decimals
let x2 = 34;    // Without decimals
let y = 123e5;  // 12300000 (Scientific notation)
let z = 123e-5; // 0.00123
```
JavaScript numbers are always **64-bit floating-point**.

### BigInt
```javascript
let x = BigInt("123456789012345678901234567890");
```
BigInt is used to store integers larger than **2^53 - 1**.

### Booleans
```javascript
let x = 5;
let y = 5;
let z = 6;
(x == y); // true
(x == z); // false
```
Booleans are commonly used in **conditional statements**.

### Arrays
```javascript
const cars = ["Saab", "Volvo", "BMW"];
```
Array indexes are **zero-based** (`cars[0]` is the first element).

### Objects
```javascript
const person = {firstName: "John", lastName: "Doe", age: 50, eyeColor: "blue"};
```
Objects store properties as **key-value pairs**.

### The `typeof` Operator
The `typeof` operator returns the type of a variable:
```javascript
typeof "John"; // "string"
typeof 3.14;   // "number"
typeof true;   // "boolean"
typeof {};     // "object"
typeof [];     // "object" (Arrays are objects)
typeof null;   // "object" (Special case)
typeof undefined; // "undefined"
```

### Undefined
A variable without a value is `undefined`:
```javascript
let car;
console.log(car); // undefined
```
Setting a variable to `undefined` explicitly:
```javascript
car = undefined;
```

### Empty Values vs. Undefined
An **empty string** is different from `undefined`:
```javascript
let car = ""; // The value is "", the typeof is "string"
```

---

# JavaScript String Manipulation and Methods

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

# Stack and Heap Memory in JavaScript

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

# Numbers Fundamentals

### 📌 Basics of Numbers in JavaScript

### Declaring a Number
You can declare a number variable in JavaScript using `const`, `let`, or `var`:
```js
const score = 400;
console.log(score);
```
**Output:**
```
400
```

### Creating a Number Object  
You can explicitly create a number using the `Number` constructor:
```js
const balance = new Number(90);
console.log(balance);
```
**Output:**
```
[Number: 90]
```

## 🛠️ Useful Number Methods

### Converting a Number to a String
To convert a number into a string, use `.toString()`:
```js
const balance = 90;
console.log(balance.toString());  // "90"
console.log(typeof balance.toString());  // "string"
```

### Fixing Decimal Places (`toFixed()`)
The `toFixed(n)` method rounds a number to `n` decimal places and returns it as a string:
```js
const amount = 69.456;
console.log(amount.toFixed(1));  // "69.5"
console.log(amount.toFixed(2));  // "69.46"
```

### Finding the Length of a Number  
A number itself does not have a `.length` property like a string, but you can convert it to a string and then check its length:
```js
const num = 12345;
console.log(num.toString().length);  // 5
```

### Precision Control (`toPrecision()`)
The `toPrecision(n)` method formats a number to a specified total number of **significant** digits:
```js
const num = 123.456;
console.log(num.toPrecision(3));  // "123"
console.log(num.toPrecision(5));  // "123.46"
console.log(num.toPrecision(2));  // "1.2e+2" (Scientific notation)
```

### Formatting Numbers as Locale-Specific Strings (`toLocaleString()`)
The `toLocaleString()` method converts a number into a localized string representation, useful for formatting currency or large numbers:
```js
const salary = 1000000;
console.log(salary.toLocaleString());  // "1,000,000" (in US format)
console.log(salary.toLocaleString("de-DE"));  // "1.000.000" (in German format)
console.log(salary.toLocaleString("en-IN"));  // "10,00,000" (Indian format)
```

---


# JavaScript Math Library 

### 📌 Introduction to `Math` Object  
The `Math` object in JavaScript is a **built-in library** that provides mathematical constants and functions. Unlike other objects, `Math` is **not a constructor**, so you don't need to create an instance of it.

---

## 🛠️ Useful Math Methods

### 1️⃣ **Absolute Value (`Math.abs()`)**
Converts a negative number to positive:
```js
console.log(Math.abs(-4));  // Output: 4
console.log(Math.abs(10));  // Output: 10
```

---

### 2️⃣ **Rounding Methods**  

| Method          | Description                     | Example  | Output |
|---------------|--------------------------------|---------|--------|
| `Math.round()` | Rounds to the nearest integer | `Math.round(3.6)` | `4` |
| `Math.ceil()`  | Rounds up to the nearest integer | `Math.ceil(4.2)`  | `5` |
| `Math.floor()` | Rounds down to the nearest integer | `Math.floor(4.9)` | `4` |

Example:
```js
console.log(Math.round(3.6));  // 4
console.log(Math.ceil(4.2));   // 5
console.log(Math.floor(4.9));  // 4
```

---

### 3️⃣ **Generating Random Numbers (`Math.random()`)**
Generates a random number between `0` and `1`:
```js
console.log(Math.random());  // Example output: 0.53423
```

**Generating a Random Number Between a Range (10 to 20)**:
```js
const min = 10;
const max = 20;
console.log(Math.floor(Math.random() * (max - min + 1)) + min);
```
✅ **Explanation**:
1. `Math.random()` generates a value between `0` and `1`.
2. Multiplying it by `(max - min + 1)` scales it to the range.
3. `Math.floor()` ensures the final value is an integer.
4. Adding `min` shifts the range from `0 to (max-min)` → `min to max`.

---

### 4️⃣ **Finding Minimum & Maximum Values**
- **`Math.min()`** → Returns the smallest value from a list of numbers.
- **`Math.max()`** → Returns the largest value from a list of numbers.

Example:
```js
console.log(Math.min(3, 5, 1, 8, 2));  // Output: 1
console.log(Math.max(3, 5, 1, 8, 2));  // Output: 8
```

---

### 5️⃣ **Square Root (`Math.sqrt()`)**
The `Math.sqrt()` method returns the square root of a number.
```js
console.log(Math.sqrt(16));  // Output: 4
console.log(Math.sqrt(25));  // Output: 5
console.log(Math.sqrt(2));   // Output: 1.414
```

---

# Dates In JavaScript

## 📌 Introduction to `Date` Object  
In JavaScript, the `Date` object is used to work with dates and times. You can create a date object using `new Date()`.  

---

## 🛠️ Initializing a Date Object

### 1️⃣ **Current Date and Time**
The `new Date()` constructor creates a date object with the current date and time.
```js
let myDate = new Date();
console.log(myDate.toString());  
```
**Output Example:**
```
Wed Feb 28 2024 12:34:56 GMT+0530 (India Standard Time)
```

### 2️⃣ **Formatted Date Strings**
| Method | Description | Example Output |
|--------|------------|----------------|
| `.toString()` | Returns the full date & time as a string | `Wed Feb 28 2024 12:34:56 GMT+0530 (IST)` |
| `.toDateString()` | Returns only the date in a readable format | `Wed Feb 28 2024` |
| `.toLocaleString()` | Returns date & time formatted based on the user's locale | `2/28/2024, 12:34:56 PM` |
| `.toLocaleDateString()` | Returns only the date in a locale-specific format | `2/28/2024` |
| `.toISOString()` | Returns the date in ISO 8601 format (useful for databases) | `2024-02-28T07:04:56.789Z` |

Example:
```js
console.log(myDate.toDateString());      // "Wed Feb 28 2024"
console.log(myDate.toLocaleString());    // "2/28/2024, 12:34:56 PM"
console.log(myDate.toISOString());       // "2024-02-28T07:04:56.789Z"
```

---

## 📆 Creating Specific Dates  

### 1️⃣ **Creating a Date with Year, Month, and Day**
```js
const newDate = new Date(2024, 1, 5);  // February 5, 2024 (Month starts from 0)
console.log(newDate.toLocaleString());  // "2/5/2024, 12:00:00 AM"
console.log(newDate.toDateString());    // "Mon Feb 05 2024"
```
✅ **Note:**  
- Months in JavaScript start from `0` (January = `0`, February = `1`, etc.).

### 2️⃣ **Creating a Date from a String (YYYY-MM-DD)**
```js
const newDateIndia = new Date("2004-01-05"); // January 5, 2004
console.log(newDateIndia.toLocaleString());  // "1/5/2004, 12:00:00 AM"
console.log(newDateIndia.toDateString());    // "Mon Jan 05 2004"
```

---

## 📌 Extracting Date Components  

### 1️⃣ **Getting Specific Parts of a Date**
```js
let singleDate = new Date();

console.log(singleDate.getTime());        // Returns timestamp (milliseconds since 1970)
console.log(singleDate.getDay());         // Returns day of the week (0 = Sunday, 1 = Monday, ..., 6 = Saturday)
console.log(singleDate.getMonth() + 1);   // Returns month (Add 1 since months start from 0)
console.log(singleDate.getFullYear());    // Returns full year
console.log(singleDate.getTimezoneOffset()); // Returns the difference between UTC and local time in minutes
```

### 2️⃣ **Displaying a Custom Date Format**
```js
console.log(`Today's date is ${singleDate.getDate()} and the current month is ${singleDate.getMonth() + 1}`);
```
**Example Output:**
```
Today's date is 28 and the current month is 2
```


---


# Working with Arrays in JavaScript

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

# Working with Objects in JavaScript

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


## 🛠️ Defining an Object  

```js
const sym = Symbol("mykey"); // Creating a unique symbol

const course = {
  name: "The JavaScript Course",
  id: 101,
  [sym]: "myvalue" // Using a symbol as a key
};
```

✅ **Notes:**  
- `"name"` is a **string key**, so it must be accessed with dot or bracket notation (`course.name` or `course["name"]`).  
- **Symbols** cannot be accessed using dot notation (`course.sym` is incorrect). Instead, use bracket notation (`course[sym]`).  

---

## 🔍 Accessing Object Properties  

```js
console.log(course.name);  // ✅ Correct: "The JavaScript Course"
console.log(course["name"]); // ✅ Correct: "The JavaScript Course"

console.log(course[sym]); // ✅ Correct: "myvalue"
console.log(course.sym);  // ❌ Incorrect: `undefined` (Symbols must be accessed with brackets)
```

---

## 📌 Adding Methods to an Object  

We can add functions (methods) to an object after its creation.

```js
course.greet = function() {
  console.log("Hello, welcome to the course!");
};

// Calling the function
console.log(course.greet);   // ✅ Prints function definition
course.greet();              // ✅ Output: "Hello, welcome to the course!"
```

---

## 📌 Using `this` in an Object Method  

Using `this` refers to the current object, allowing us to access properties dynamically.

```js
course.greet = function() {
  console.log(`Hello, welcome to ${this.name}!`);
};

console.log(course.greet); // ✅ Prints function definition
course.greet();            // ✅ Output: "Hello, welcome to The JavaScript Course!"
```

---


# JSON in JavaScript

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

# Functions in JavaScript

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

# Scopes in JavaScript

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
# Hoisting in JavaScript

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

# Immediately Invoked Function Expressions (IIFE)

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

# Execution & Call Stack  

## 📌 JavaScript Execution Model  

JavaScript follows a **single-threaded** execution model, meaning it can execute only **one task at a time**. The execution happens in a structured manner using **Execution Contexts** and the **Call Stack**.

---

## 🔥 Execution Context  

An **Execution Context** is an environment in which JavaScript code is executed. There are two types:  

1️⃣ **Global Execution Context (GEC)**  
   - Created when the script starts running.  
   - It is associated with the `this` keyword (in browsers, `this` refers to the `window` object).  

2️⃣ **Function Execution Context (FEC)**  
   - Created when a function is called.  
   - Each function has its own execution context, which gets pushed onto the Call Stack.  

---

## 🛠️ Execution Process  

JavaScript execution happens in **two phases**:  

### 1️⃣ Memory Creation Phase  
   - Allocates memory for variables and functions.  
   - Variables are initialized with `undefined`.  
   - Functions are stored with their full definitions.  

### 2️⃣ Execution Phase  
   - Executes the code line by line.  
   - Updates variable values as per their assignments.  
   - When a function is called, a **new Execution Context** is created.  
   - When a function finishes execution, its context is removed from the Call Stack.  

---

## 📌 Call Stack  

The **Call Stack** is a **stack data structure** that manages execution contexts.  

✅ **How it Works:**  
1. The **Global Execution Context (GEC)** is placed at the bottom of the stack.  
2. When a function is called, its execution context is **pushed** onto the stack.  
3. If the function calls another function, the new function's context is **pushed** on top.  
4. When a function finishes execution, its context is **popped** off the stack.  
5. The stack clears when all functions finish executing.  

🔹 **Example:**  

```js
function first() {
  console.log("First function");
  second();
}

function second() {
  console.log("Second function");
  third();
}

function third() {
  console.log("Third function");
}

first();
```

✅ **Call Stack Flow:**  

1️⃣ `first()` is called → Pushed onto stack  
2️⃣ `first()` calls `second()` → `second()` is pushed onto stack  
3️⃣ `second()` calls `third()` → `third()` is pushed onto stack  
4️⃣ `third()` finishes execution → **Popped off stack**  
5️⃣ `second()` finishes execution → **Popped off stack**  
6️⃣ `first()` finishes execution → **Popped off stack**  


---

# Event Handling in JavaScript

An **event** is an action that occurs in the browser, like a user clicking a button. Events can be handled using **event listeners** and functions.

### Example of Event Listener:
```javascript
document.getElementById("myButton").addEventListener("click", function() {
  alert("Button clicked!");
});
```

> **Common events**: `click`, `mouseover`, `keydown`, `submit`, etc.

---

# Loops in JavaScript

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


🔹 **Example of an Object:**  

```js
const myObj = {
  js: "JavaScript",
  r: "Ruby",
  cpp: "C++"
};

console.log(myObj.js); // Output: JavaScript
console.log(myObj["cpp"]); // Output: C++
```

---


The `for...in` loop is used to **iterate over the keys** of an object.  

🔹 **Syntax:**  
```js
for (const key in object) {
  // Code to execute
}
```

✅ **Example:**  

```js
const myObj = {
  js: "JavaScript",
  r: "Ruby",
  cpp: "C++"
};

for (const key in myObj) {
  console.log(`${key} is the shortcut for ${myObj[key]}`);
}
```

🔹 **Output:**  
```
js is the shortcut for JavaScript
r is the shortcut for Ruby
cpp is the shortcut for C++
```


## 🔄 `forEach` Method in JavaScript  
`forEach` is a method that runs a function for each array element.
```javascript
let loop = [1, 2, 3, 4];
loop.forEach(function(item) {
  console.log(item);  // Output: 1, 2, 3, 4
});
```

The `.forEach()` method is used to **iterate** over an array and **execute a function** for each element.  

🔹 **Syntax:**  
```js
array.forEach((element, index, array) => {
  // Code to execute for each element
});
```

### ❗ Important Notes about `.forEach()`
- It does **not return a new array** (unlike `.map()`).
- It **always returns `undefined`**.
- It is used when we just want to **perform an action on each item**, rather than create a new array.

---

## 🔥 Return Statement

1. **Expecting `forEach()` to return a value:**  
   ```js
   const value = myArray.forEach((item) => {
     return item;
   });
   console.log(value);
   ```
   - **Issue:** `.forEach()` **always returns `undefined`**.
   - **alternative:** Use `.map()` if you need a return value.

2. **Correcting the Usage of `.forEach()`:**  
   - If we only want to **perform an action** (like logging values), `.forEach()` is correct.

---

## ✅ example

### 🎯 Example 1: Using `forEach()` (No Return Value)
```js
const myArray = [1, 2, 3, 4, 5, 6];

myArray.forEach((item) => {
  console.log(item);
});
```
🔹 **Output:**
```
1
2
3
4
5
6
```

👉 If you **need to return a new array**, use `.map()` instead:
```js
const newArray = myArray.map((item) => item);
console.log(newArray); // Output: [1, 2, 3, 4, 5, 6]
```

---

### 🎯 Example 2: Using `forEach()` with Objects  
```js
const objArr = [
  { name: "Prathamesh", department: "CSE" },
  { name: "Gauri", department: "CSE" },
  { name: "Omkar", department: "MECH" },
];

objArr.forEach((item) => {
  console.log(`${item.department} has ${item.name} student`);
});
```
🔹 **Output:**
```
CSE has Prathamesh student
CSE has Gauri student
MECH has Omkar student
```

---


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