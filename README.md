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

## Working with Numbers in JavaScript

In JavaScript, numbers are an essential data type, and there are several methods to manipulate them. Here, we explore how to handle numbers, convert them to strings, and format them with floating points.

### 1. Simple Number Declaration

You can declare numbers in JavaScript directly using the `const` or `let` keyword. For example:
```javascript
const score = 400;
console.log(score);  // Output: 400
```
Here, `score` is a simple number variable with a value of `400`.

### 2. Creating a Number Object

In JavaScript, you can also create a number using the `Number` constructor. This approach allows you to work with numbers as objects, which can provide access to certain methods. However, this is less common than directly declaring numbers.
```javascript
const balance = new Number(90);
console.log(balance);  // Output: [Number: 90]
```
The output shows the `Number` object representation, though the value itself is still `90`.

### 3. Converting a Number to a String

To convert a number to a string, you can use the `.toString()` method. This is useful when you need to treat numeric data as text.
```javascript
console.log(balance.toString());  // Output: "90"
```
Now, the number `90` has been converted to the string `"90"`.

### 4. Formatting Floating Point Numbers

If you need to control the number of decimal places for a floating-point number, the `.toFixed()` method can be used. This method rounds the number and formats it with a fixed number of decimal places.

Example:
```javascript
let value = 69;
console.log(value.toFixed(1));  // Output: "69.0"
```
In this case, `.toFixed(1)` ensures that the value is displayed with one decimal place, even though it's an integer.

---

## Math Library in JavaScript

JavaScript provides a built-in **Math** object that contains various methods to perform mathematical operations. It’s commonly used for tasks like rounding numbers, generating random values, and finding the minimum or maximum values.

### 1. Commonly Used Math Methods

Here’s a list of some of the most commonly used methods in the `Math` object:

- **`Math.abs(x)`**: Returns the absolute value of a number (i.e., converts negative numbers to positive).
  ```javascript
  console.log(Math.abs(-4));  // Output: 4
  ```

- **`Math.round(x)`**: Rounds a number to the nearest integer.
  ```javascript
  console.log(Math.round(3.6));  // Output: 4
  ```

- **`Math.ceil(x)`**: Rounds a number **up** to the next largest integer.
  ```javascript
  console.log(Math.ceil(4.2));  // Output: 5
  ```

- **`Math.floor(x)`**: Rounds a number **down** to the largest integer less than or equal to the given number.
  ```javascript
  console.log(Math.floor(4.2));  // Output: 4
  ```

- **`Math.random()`**: Generates a random decimal number between `0` and `1` (but not exactly `1`).
  ```javascript
  console.log(Math.random());  // Output: 0.345..., a random decimal
  ```

- **`Math.min(...numbers)`**: Returns the smallest value from a list of numbers.
  ```javascript
  console.log(Math.min(10, 20, 5, 7));  // Output: 5
  ```

- **`Math.max(...numbers)`**: Returns the largest value from a list of numbers.
  ```javascript
  console.log(Math.max(10, 20, 5, 7));  // Output: 20
  ```

### 2. Using `Math.random()` to Generate a Random Number Between a Range

The `Math.random()` method generates a number between `0` and `1`. To get a random number in a specific range (e.g., between 10 and 20), you can combine `Math.random()` with `Math.floor()` and adjust the result to the desired range.

Here’s how you can generate a random number between `10` and `20`:
```javascript
const min = 10;
const max = 20;
let randomNum = Math.floor(Math.random() * (max - min + 1)) + min;
console.log(randomNum);
```

In this code:
- `Math.random()` generates a random number between `0` and `1`.
- Multiplying by `(max - min + 1)` stretches that range to include numbers from `10` to `20`.
- `Math.floor()` rounds the result down to the nearest integer.
- Finally, adding `min` shifts the range to start from `10`.

---