
# 🚀 JavaScript Interview Preparation — Complete 1-Hour Crash Course

## ⏰ Your 60-Minute Study Plan

| Time | Topic | What you will learn |
|---|---|---|
| 0–5 min | JavaScript Fundamentals | What JavaScript is and how it works |
| 5–12 min | Variables and Data Types | `var`, `let`, `const`, types, operators |
| 12–20 min | Conditions and Loops | `if`, `else`, `switch`, `for`, `while` |
| 20–30 min | Functions and Arrays | Functions, arrow functions, array methods |
| 30–38 min | Strings and Coding Problems | Reverse strings, palindrome, largest number |
| 38–45 min | Objects and Advanced Basics | Objects, scope, hoisting, closures |
| 45–52 min | DOM, Events, and Async JavaScript | Browser interaction, promises, `async/await` |
| 52–60 min | Mock Interview | Coding questions and technical questions |

**Your main goal:** Learn how to convert a question into working code without depending on memorized programs.

---

# 1. What Is JavaScript? (0–5 Minutes)

## 1.1 Definition

JavaScript is a high-level programming language primarily used to make websites interactive.

For example:
- HTML creates the structure of a webpage.
- CSS controls the appearance.
- JavaScript adds behavior and interactivity.

Consider a login page.

- HTML creates the username and password fields.
- CSS styles the fields and login button.
- JavaScript validates the input and responds when the user clicks the button.
- A backend API can authenticate the user.

JavaScript can also run outside browsers using environments such as Node.js.

### Interview Question: What is JavaScript?

**Answer:**

JavaScript is a high-level, dynamically typed programming language used to create interactive web applications. It runs in web browsers and can also run on servers using environments such as Node.js.

## 1.2 How to Write JavaScript

You can write JavaScript inside an HTML file.

```html
<!DOCTYPE html>
<html>
<head>
    <title>JavaScript Practice</title>
</head>
<body>

    <h1>My First JavaScript Program</h1>

    <script>
        console.log("Hello World");
    </script>

</body>
</html>
```

Output in the browser console:

```text
Hello World
```

### Understand This Line

```javascript
console.log("Hello World");
```

- `console`: Provides access to the browser's developer console.
- `log()`: Prints information.
- `"Hello World"`: The text to print.

You can also use:

```javascript
alert("Hello World");
```

This displays a browser alert dialog.

**Interview tip:** `console.log()` is commonly used to inspect values and debug JavaScript programs.

---

# 2. Variables and Data Types (5–12 Minutes)

A variable stores a value that you can use in your program.

JavaScript has three commonly discussed variable declarations:

- `var`
- `let`
- `const`

## 2.1 Difference Between `var`, `let`, and `const`

```javascript
var name = "Abirami";
let age = 22;
const country = "India";
```

### Comparison Table

| Feature | `var` | `let` | `const` |
|---|---|---|---|
| Can reassign the variable? | Yes | Yes | No |
| Can redeclare in the same scope? | Yes | No | No |
| Scope | Function or global scope | Block scope | Block scope |
| Must initialize at declaration? | No | No | Yes |

### Example

```javascript
let age = 22;

age = 23;

console.log(age);
```

Output:

```text
23
```

Now consider:

```javascript
const country = "India";

country = "Canada";
```

This produces a `TypeError` because you cannot reassign a `const` variable.

### Important Interview Question

**Which should you use: `var`, `let`, or `const`?**

A good answer:

I generally use `const` when a variable does not need reassignment and `let` when its value needs to change. I avoid `var` in modern JavaScript because its function-scoping behavior can cause unexpected issues.

**Important:** A `const` object can still have its properties modified. `const` prevents reassignment of the variable, not all changes to the referenced object.

---

## 2.2 JavaScript Data Types

JavaScript has seven primitive types and the object type.

| Type | Example |
|---|---|
| String | `"Hello"` |
| Number | `100`, `10.5` |
| Boolean | `true`, `false` |
| Undefined | `let x;` |
| Null | `let x = null;` |
| BigInt | `12345678901234567890n` |
| Symbol | `Symbol("id")` |
| Object | `{ name: "Abirami" } |

Arrays and functions are also objects in JavaScript, although functions have their own special behavior.

### Example

```javascript
let name = "Abirami";
let age = 22;
let isWorking = true;
let salary;
let address = null;

console.log(typeof name);
console.log(typeof age);
console.log(typeof isWorking);
console.log(typeof salary);
console.log(typeof address);
```

Output:

```text
string
number
boolean
undefined
object
```

**Interview trap:** `typeof null` returns `"object"`. This is a longstanding JavaScript behavior.

### Difference Between `undefined` and `null`

- `undefined`: A value has not been assigned or is missing.
- `null`: Represents an intentional absence of a value.

```javascript
let a;
let b = null;

console.log(a); // undefined
console.log(b); // null
```

---

## 2.3 Operators

Operators perform operations on values.

| Operator | Meaning | Example |
|---|---|---|
| `+` | Addition or string concatenation | `5 + 3` |
| `-` | Subtraction | `5 - 3` |
| `*` | Multiplication | `5 * 3` |
| `/` | Division | `10 / 2` |
| `%` | Remainder | `10 % 3` |
| `===` | Strict equality | `5 === 5` |
| `!==` | Strict inequality | `5 !== "5"` |
| `>` | Greater than | `10 > 5` |
| `&&` | Logical AND | `true && false` |
| `||` | Logical OR | `true || false` |
| `!` | Logical NOT | `!true` |

### Difference Between `==` and `===`

This is one of the most frequently asked JavaScript questions.

```javascript
console.log(5 == "5");
console.log(5 === "5");
```

Output:

```text
true
false
```

Why?

- `==` performs equality comparison with type coercion where applicable.
- `===` compares without converting the operands to make their types match.

**Interview answer:** I generally prefer `===` because it avoids unexpected type coercion.

### Try Predicting the Output

```javascript
console.log(10 + 5);
console.log("10" + 5);
console.log("10" - 5);
```

Answer:

```text
15
105
5
```

The `+` operator can concatenate strings, while subtraction converts suitable string operands to numbers.

---

# 3. Conditions and Loops (12–20 Minutes)

Conditions allow your program to make decisions. Loops allow it to repeat operations.

## 3.1 If-Else

Let's write a program to determine whether a number is even or odd.

```javascript
let number = 7;

if (number % 2 === 0) {
    console.log("Even");
} else {
    console.log("Odd");
}
```

Output:

```text
Odd
```

### How Does It Work?

1. `number` contains `7`.
2. `7 % 2` produces `1`.
3. The condition checks whether the remainder equals `0`.
4. The condition is false, so the `else` block runs.

### How to Write This Yourself

When an interviewer gives you a coding question:

1. Understand what input you have.
2. Identify the condition.
3. Decide what should happen when the condition is true.
4. Decide what should happen when it is false.
5. Write the code.
6. Test it using different inputs.

This process is more valuable than memorizing the program.

## 3.2 Find the Largest of Three Numbers

```javascript
let a = 10;
let b = 25;
let c = 15;

if (a >= b && a >= c) {
    console.log("A is largest");
} else if (b >= a && b >= c) {
    console.log("B is largest");
} else {
    console.log("C is largest");
}
```

Output:

```text
B is largest
```

Notice that `&&` requires both conditions to be true.

## 3.3 Switch Statement

A `switch` statement selects a code block based on a matching value.

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log("Monday");
        break;

    case 2:
        console.log("Tuesday");
        break;

    case 3:
        console.log("Wednesday");
        break;

    default:
        console.log("Invalid day");
}
```

Output:

```text
Tuesday
```

`break` prevents execution from continuing into subsequent cases.

---

## 3.4 For Loop

A loop repeats a block of code.

```javascript
for (let i = 1; i <= 5; i++) {
    console.log(i);
}
```

Output:

```text
1
2
3
4
5
```

Understand the structure:

```javascript
for (initialization; condition; update)
```

In this example:

- Initialization: `let i = 1`
- Condition: `i <= 5`
- Update: `i++`

The loop stops when `i` becomes `6`.

### Question: What Does `i++` Mean?

It increments `i` by one.

```javascript
let i = 5;
i++;
console.log(i);
```

Output: `6`.

## 3.5 While Loop

```javascript
let i = 1;

while (i <= 5) {
    console.log(i);
    i++;
}
```

This produces the same output.

Use a `while` loop when repetition depends on a condition.

## 3.6 Coding Question: Sum of Numbers from 1 to N

Suppose `n = 5`.

The answer is:

`1 + 2 + 3 + 4 + 5 = 15`

```javascript
let n = 5;
let sum = 0;

for (let i = 1; i <= n; i++) {
    sum = sum + i;
}

console.log(sum);
```

Output:

```text
15
```

### How to Build the Logic

Start with:

```javascript
let sum = 0;
```

Why zero? Because you haven't added any numbers yet.

Then:

```javascript
sum = sum + i;
```

This adds the current number to the accumulated total.

| Iteration | `i` | `sum` |
|---|---:|---:|
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |
| 5 | 5 | 15 |

This pattern appears in many interview questions involving sums and totals.

---

# 4. Functions (20–25 Minutes)

A function is a reusable block of code that performs a task.

Functions are essential because they let you divide a large program into smaller, manageable pieces.

## 4.1 Function Declaration

```javascript
function greet() {
    console.log("Hello Abirami");
}

greet();
```

Output:

```text
Hello Abirami
```

Here:

- `function` declares the function.
- `greet` is the function name.
- `()` contains parameters, if any.
- `{}` contains the function body.
- `greet()` calls the function.

## 4.2 Function With Parameters

Parameters let a function receive values.

```javascript
function greet(name) {
    console.log("Hello " + name);
}

greet("Abirami");
greet("Priya");
```

Output:

```text
Hello Abirami
Hello Priya
```

The function receives a different name each time.

## 4.3 Function With a Return Value

```javascript
function add(a, b) {
    return a + b;
}

let result = add(10, 20);

console.log(result);
```

Output:

```text
30
```

### What Is the Difference Between `return` and `console.log()`?

`console.log()` displays information in the console.

`return` sends a value back to the code that called the function.

For example:

```javascript
function add(a, b) {
    return a + b;
}

let answer = add(5, 3);
console.log(answer * 2);
```

Output:

```text
16
```

The function returns `8`, which is then multiplied by `2`.

---

## 4.4 Arrow Functions

Arrow functions provide a shorter syntax for writing functions.

Traditional function:

```javascript
function multiply(a, b) {
    return a * b;
}
```

Arrow function:

```javascript
const multiply = (a, b) => {
    return a * b;
};

console.log(multiply(4, 5));
```

Output:

```text
20
```

For a single expression, you can shorten it further:

```javascript
const multiply = (a, b) => a * b;
```

### Interview Question: What Is an Arrow Function?

An arrow function is a shorter way to define a function using the `=>` syntax. Unlike regular functions, arrow functions do not have their own `this` binding.

This difference becomes important when working with objects and callbacks.

---

# 5. Arrays and Array Methods (25–30 Minutes)

An array stores multiple values in a single variable.

```javascript
let numbers = [10, 20, 30, 40, 50];
```

Array indexes start at zero.

```javascript
console.log(numbers[0]);
console.log(numbers[2]);
```

Output:

```text
10
30
```

The array's length is:

```javascript
console.log(numbers.length);
```

Output:

```text
5
```

## 5.1 Loop Through an Array

```javascript
let numbers = [10, 20, 30];

for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}
```

Output:

```text
10
20
30
```

Notice the condition:

```javascript
i < numbers.length
```

If the array contains three elements, its valid indexes are `0`, `1`, and `2`.

## 5.2 Important Array Methods

These methods are particularly useful in interviews.

| Method | Purpose |
|---|---|
| `push()` | Adds an element to the end |
| `pop()` | Removes the last element |
| `shift()` | Removes the first element |
| `unshift()` | Adds an element to the beginning |
| `map()` | Transforms each element into a new array |
| `filter()` | Creates an array of elements matching a condition |
| `find()` | Returns the first matching element |
| `includes()` | Checks whether a value is present |
| `reduce()` | Accumulates array values into one result |
| `forEach()` | Executes a callback for each element |

### Example 1: `push()`

```javascript
let numbers = [10, 20, 30];

numbers.push(40);

console.log(numbers);
```

Output:

```text
[10, 20, 30, 40]
```

### Example 2: `map()`

Suppose you need to double every number.

```javascript
let numbers = [1, 2, 3, 4];

let result = numbers.map(num => num * 2);

console.log(result);
```

Output:

```text
[2, 4, 6, 8]
```

**How it works:**

- `map()` visits each array element.
- `num => num * 2` describes the transformation.
- The resulting values are collected into a new array.

The original array remains unchanged.

### Example 3: `filter()`

Find all even numbers.

```javascript
let numbers = [1, 2, 3, 4, 5, 6];

let result = numbers.filter(num => num % 2 === 0);

console.log(result);
```

Output:

```text
[2, 4, 6]
```

The callback returns `true` for even numbers and `false` for odd numbers.

### Example 4: `reduce()`

Find the sum of an array.

```javascript
let numbers = [10, 20, 30, 40];

let sum = numbers.reduce((total, num) => total + num, 0);

console.log(sum);
```

Output:

```text
100
```

Here:

- `total` is the accumulated result.
- `num` is the current element.
- `0` is the initial value.

### Remember the Difference

Given:

```javascript
let numbers = [1, 2, 3, 4, 5];
```

- `map()` transforms elements.
- `filter()` selects elements.
- `reduce()` combines elements into a result.

This is a very common interview topic.

---

# 6. Strings and Coding Questions (30–38 Minutes)

Strings represent text.

```javascript
let text = "JavaScript";
```

Useful properties and methods:

| Operation | Example |
|---|---|
| Length | `text.length` |
| Uppercase | `text.toUpperCase()` |
| Lowercase | `text.toLowerCase()` |
| Character at an index | `text[0]` |
| Check for text | `text.includes("Script")` |
| Extract a section | `text.slice(0, 4)` |
| Remove surrounding whitespace | `text.trim()` |
| Split into parts | `text.split("")` |

## Coding Question 1: Reverse a String

**Input:** `"hello"`

**Expected output:** `"olleh"`

### Solution

```javascript
function reverseString(str) {
    let reversed = "";

    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }

    return reversed;
}

console.log(reverseString("hello"));
```

Output:

```text
olleh
```

### Understand the Logic

The string `"hello"` has five characters.

Their indexes are:

| Index | Character |
|---:|---|
| 0 | h |
| 1 | e |
| 2 | l |
| 3 | l |
| 4 | o |

Start from index `4` and move backward to index `0`.

The statement:

```javascript
reversed += str[i];
```

adds each character to the end of the new string.

### Alternative Solution

```javascript
function reverseString(str) {
    return str.split("").reverse().join("");
}
```

This works as follows:

1. `split("")` converts the string into an array of characters.
2. `reverse()` reverses the array.
3. `join("")` combines the characters into a string.

For coding interviews, understand the loop solution first because it demonstrates your logic.

---

## Coding Question 2: Check for a Palindrome

A palindrome reads the same forward and backward.

Examples: `madam`, `level`, `racecar`.

```javascript
function isPalindrome(str) {
    let reversed = "";

    for (let i = str.length - 1; i >= 0; i--) {
        reversed += str[i];
    }

    return str === reversed;
}

console.log(isPalindrome("madam"));
console.log(isPalindrome("hello"));
```

Output:

```text
true
false
```

### How to Think

1. Receive a string.
2. Reverse the string.
3. Compare the original and reversed strings.
4. Return `true` if they match.

This version is case-sensitive and considers spaces and punctuation.

---

## Coding Question 3: Find the Largest Number in an Array

Given:

```javascript
let numbers = [10, 50, 20, 80, 30];
```

Expected output:

```text
80
```

### Solution

```javascript
function findLargest(numbers) {
    let max = numbers[0];

    for (let i = 1; i < numbers.length; i++) {
        if (numbers[i] > max) {
            max = numbers[i];
        }
    }

    return max;
}

console.log(findLargest([10, 50, 20, 80, 30]));
```

### Understand the Logic

Start with `max = 10`.

Compare every remaining number with `max`.

Whenever a larger number is found, update `max`.

At the end, `max` contains `80`.

This solution assumes the array is non-empty.

---

## Coding Question 4: Count Vowels in a String

```javascript
function countVowels(str) {
    let count = 0;

    for (let i = 0; i < str.length; i++) {
        let ch = str[i].toLowerCase();

        if ("aeiou".includes(ch)) {
            count++;
        }
    }

    return count;
}

console.log(countVowels("JavaScript"));
```

Output:

```text
3
```

The vowels in `"JavaScript"` are `a`, `a`, and `i`.

### How to Solve Similar Questions

Use this pattern:

```javascript
let count = 0;

for (let i = 0; i < text.length; i++) {
    // Check a condition.
    // Increase count if it matches.
}
```

This is useful for counting vowels, digits, particular characters, or other elements.

---

## Coding Question 5: FizzBuzz

This classic interview problem checks your understanding of conditions and loops.

Print numbers from `1` to `15`.

- Multiples of `3`: Print `Fizz`.
- Multiples of `5`: Print `Buzz`.
- Multiples of both: Print `FizzBuzz`.
- Otherwise: Print the number.

```javascript
for (let i = 1; i <= 15; i++) {
    if (i % 3 === 0 && i % 5 === 0) {
        console.log("FizzBuzz");
    } else if (i % 3 === 0) {
        console.log("Fizz");
    } else if (i % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(i);
    }
}
```

**Important interview tip:** Check the condition for multiples of both numbers first. Otherwise, a number such as `15` will match the condition for `3` before reaching the condition for both.

---

# 7. Objects, Scope, Hoisting, and Closures (38–45 Minutes)

These concepts frequently appear in JavaScript technical interviews.

## 7.1 Objects

An object stores data as key-value pairs.

```javascript
let student = {
    name: "Abirami",
    age: 22,
    course: "Computer Science"
};

console.log(student.name);
console.log(student.age);
```

Output:

```text
Abirami
22
```

You can also use bracket notation:

```javascript
console.log(student["course"]);
```

Output:

```text
Computer Science
```

You can modify a property:

```javascript
student.age = 23;
```

You can add a property:

```javascript
student.city = "Chennai";
```

### Interview Question: What Is an Object?

An object is a collection of properties, where each property associates a key with a value. Objects can also contain methods.

Example:

```javascript
let calculator = {
    add: function(a, b) {
        return a + b;
    }
};

console.log(calculator.add(10, 20));
```

Output: `30`.

---

## 7.2 Scope

Scope determines where a variable can be accessed.

The three common concepts are:

- Global scope
- Function scope
- Block scope

### Example

```javascript
let a = 10;

function test() {
    let b = 20;
    console.log(a);
    console.log(b);
}

test();

console.log(a);
// console.log(b); // ReferenceError
```

The variable `a` is available inside the function because it is defined in the outer scope.

The variable `b` exists only within the function.

### What Is Block Scope?

```javascript
if (true) {
    let x = 10;
    const y = 20;
}

console.log(x); // ReferenceError
```

Variables declared using `let` and `const` inside the block are not accessible outside it.

---

## 7.3 Hoisting

Hoisting describes how JavaScript processes declarations before executing the code.

Consider:

```javascript
console.log(a);

var a = 10;
```

Output:

```text
undefined
```

The declaration of `a` is processed before execution, but its assignment remains at the original location.

Now consider:

```javascript
console.log(a);

let a = 10;
```

This throws a `ReferenceError` because `a` is in its temporal dead zone before its declaration is initialized.

### Interview Answer

Hoisting is JavaScript's behavior of processing declarations before executing code. Variables declared with `var` are initialized to `undefined`, while `let` and `const` cannot be accessed before initialization.

Function declarations also have hoisting behavior, so a declared function can generally be called before its declaration appears in the source.

---

## 7.4 What Is a Closure?

A closure occurs when a function retains access to variables from its surrounding lexical scope, even after the outer function has finished executing.

This may sound complicated, so understand this example.

```javascript
function outer() {
    let count = 0;

    return function() {
        count++;
        console.log(count);
    };
}

const counter = outer();

counter();
counter();
counter();
```

Output:

```text
1
2
3
```

### How Does It Work?

1. `outer()` creates the variable `count`.
2. It returns an inner function.
3. The inner function retains access to `count`.
4. Each time you call `counter()`, the same variable is incremented.

### Interview Answer

A closure is created when a function retains access to variables from its lexical environment. Closures are useful for maintaining state, creating private variables, and implementing callbacks.

For your interview, understand the example rather than memorizing the definition alone.

---

# 8. DOM, Events, and Asynchronous JavaScript (45–52 Minutes)

## 8.1 What Is the DOM?

DOM stands for Document Object Model.

The browser represents an HTML document as a tree of objects. JavaScript can use the DOM to read or modify webpage content.

Suppose your HTML contains:

```html
<h1 id="title">Hello</h1>
<button id="btn">Click Me</button>
```

JavaScript can access and change the heading:

```javascript
const heading = document.getElementById("title");

heading.textContent = "Welcome to JavaScript";
```

The text displayed in the heading changes.

### Common DOM Methods

| Method or property | Purpose |
|---|---|
| `document.getElementById()` | Selects an element by its ID |
| `document.querySelector()` | Selects the first element matching a CSS selector |
| `document.querySelectorAll()` | Selects all matching elements |
| `element.textContent` | Reads or changes text |
| `element.innerHTML` | Reads or changes HTML markup |
| `element.style` | Accesses inline styles |
| `element.addEventListener()` | Registers an event listener |

**Important:** Avoid inserting untrusted user input with `innerHTML`, because it can introduce cross-site scripting vulnerabilities. Use `textContent` for plain text.

## 8.2 Events

An event is an action or occurrence, such as a button click, key press, or form submission.

HTML:

```html
<button id="btn">Click Me</button>
<p id="message"></p>
```

JavaScript:

```javascript
const button = document.getElementById("btn");
const message = document.getElementById("message");

button.addEventListener("click", function() {
    message.textContent = "Button clicked!";
});
```

When the user clicks the button, the paragraph displays:

```text
Button clicked!
```

### Interview Question: What Is an Event Listener?

An event listener executes a callback when a specified event occurs on an element or another event target.

---

## 8.3 Synchronous vs Asynchronous JavaScript

**Synchronous code** normally executes one step at a time, in order.

```javascript
console.log("First");
console.log("Second");
console.log("Third");
```

Output:

```text
First
Second
Third
```

Asynchronous operations allow certain work, such as timers or network requests, to complete later without blocking the current JavaScript execution in the same way.

### Example: `setTimeout()`

```javascript
console.log("First");

setTimeout(function() {
    console.log("Second");
}, 1000);

console.log("Third");
```

Output:

```text
First
Third
Second
```

The timer callback is scheduled to run later. The other statements execute first.

---

## 8.4 Promises

A Promise represents the eventual result of an asynchronous operation.

A promise can be:

- Pending
- Fulfilled
- Rejected

Example:

```javascript
const promise = new Promise((resolve, reject) => {
    resolve("Task completed");
});

promise.then(result => {
    console.log(result);
});
```

Output:

```text
Task completed
```

Here, `resolve()` fulfills the promise, and `.then()` handles the fulfilled result.

### Interview Question: What Is a Promise?

A Promise is an object representing the eventual completion or failure of an asynchronous operation.

---

## 8.5 Async and Await

`async` and `await` provide a convenient way to work with promises.

```javascript
function getData() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve("Data received");
        }, 1000);
    });
}

async function displayData() {
    const result = await getData();

    console.log(result);
}

displayData();
```

Output after approximately one second:

```text
Data received
```

### Understand the Code

- `getData()` returns a promise.
- The promise resolves after the timer.
- `async` declares an asynchronous function.
- `await` waits for the promise's result within that function.
- `console.log()` prints the resolved value.

`await` pauses the execution of that async function while the promise is pending; it does not block the entire JavaScript runtime.

---

# 9. Frequently Asked JavaScript Interview Questions

Read these questions aloud and try to answer each in your own words.

| No. | Interview question | Key point to remember |
|---:|---|---|
| 1 | What is JavaScript? | Programming language for interactive applications |
| 2 | What is the difference between `var`, `let`, and `const`? | Scope and reassignment |
| 3 | What is the difference between `==` and `===`? | Type coercion |
| 4 | What are JavaScript data types? | Primitive types and objects |
| 5 | What is `undefined`? | Missing or unassigned value |
| 6 | What is `null`? | Intentional absence of a value |
| 7 | What is a function? | Reusable block of code |
| 8 | What is an arrow function? | Shorter function syntax; different `this` behavior |
| 9 | What is an array? | Indexed collection |
| 10 | What is an object? | Key-value collection |
| 11 | What is the difference between `map()` and `filter()`? | Transform versus select |
| 12 | What is `reduce()`? | Accumulate values |
| 13 | What is hoisting? | Declaration processing before execution |
| 14 | What is a closure? | Function retains lexical access |
| 15 | What is the DOM? | Object representation of an HTML document |
| 16 | What is an event listener? | Responds to events |
| 17 | What is a Promise? | Represents an asynchronous result |
| 18 | What is `async/await`? | Syntax for working with promises |
| 19 | What is the difference between `forEach()` and `map()`? | Iteration versus a new transformed array |
| 20 | What is the difference between `let` and `const`? | Reassignment is allowed only with `let` |

---

# 10. How to Approach Coding Questions in Your Interview

You mentioned that you have some coding knowledge but want to be able to write code when the interviewer gives you a problem.

This is the skill you should practise most.

Use this five-step method.

### Step 1: Understand the Input and Output

Question: Find the sum of all numbers in an array.

Input:

```javascript
[10, 20, 30]
```

Expected output:

```text
60
```

### Step 2: Explain Your Logic Before Coding

You can tell the interviewer:

"I will initialize a variable called `sum` to zero. Then I will loop through the array and add every element to `sum`. Finally, I will return the total."

This shows that you understand the problem.

### Step 3: Write the Code

```javascript
function sumArray(numbers) {
    let sum = 0;

    for (let i = 0; i < numbers.length; i++) {
        sum += numbers[i];
    }

    return sum;
}

console.log(sumArray([10, 20, 30]));
```

Output:

```text
60
```

### Step 4: Test Your Code

Test different inputs:

| Input | Expected output |
|---|---:|
| `[10, 20, 30]` | `60` |
| `[5]` | `5` |
| `[-1, 1]` | `0` |
| `[]` | `0` |

### Step 5: Explain the Complexity

For this solution:

- **Time complexity:** `O(n)` because each array element is visited once.
- **Space complexity:** `O(1)` auxiliary space because only a fixed number of extra variables are used.

Complexity analysis is especially useful for software developer interviews.

---

# 11. Final Revision: The Most Important Coding Patterns

These are the patterns I want you to recognize quickly.

### Pattern 1: Counting

```javascript
let count = 0;

for (let i = 0; i < array.length; i++) {
    if (condition) {
        count++;
    }
}
```

Useful for counting even numbers, vowels, or matching elements.

### Pattern 2: Accumulating a Sum

```javascript
let sum = 0;

for (let i = 0; i < array.length; i++) {
    sum += array[i];
}
```

Useful for calculating totals.

### Pattern 3: Finding a Maximum

```javascript
let max = array[0];

for (let i = 1; i < array.length; i++) {
    if (array[i] > max) {
        max = array[i];
    }
}
```

Useful for finding the largest number.

Remember to check that the array is not empty before using this pattern.

### Pattern 4: Reversing a String

```javascript
let reversed = "";

for (let i = str.length - 1; i >= 0; i--) {
    reversed += str[i];
}
```

Useful for reversing strings and checking simple palindromes.

### Pattern 5: Filtering Values

```javascript
const result = array.filter(item => item > 10);
```

Useful for selecting elements based on a condition.

---

# Your Interview Preparation Checklist

Before your interview, make sure you can:

- [ ] Explain `var`, `let`, and `const`.
- [ ] Explain `==` versus `===`.
- [ ] Write an `if-else` statement.
- [ ] Write a `for` loop and a `while` loop.
- [ ] Create a function with parameters and a return value.
- [ ] Reverse a string.
- [ ] Check whether a string is a palindrome.
- [ ] Find the largest number in an array.
- [ ] Calculate the sum of an array.
- [ ] Explain `map()`, `filter()`, and `reduce()`.
- [ ] Explain objects and closures.
- [ ] Describe the DOM and event listeners.
- [ ] Explain promises and `async/await`.

If you have only a little time left, prioritize **variables, conditions, loops, functions, arrays, strings, and coding practice** before studying advanced concepts.

For further reference, use the official [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide?utm_source=chatgpt.com).

---

## 🎯 Now Let's Practise Like a Real Interview

Abirami, reading explanations is useful, but you need to try writing the code yourself.

I'll ask you one question at a time, just as an interviewer would. You can write your answer even if you're unsure.

### Interview Question 1 — Basic Coding

**Write a JavaScript program to find whether a given number is even or odd.**

Example:

Input:
```text
8
```

Expected output:
```text
Even
```

**Your task:** Write the code yourself. Don't worry about making mistakes. I'll correct your code, explain what went wrong if necessary, and then move to the next question.