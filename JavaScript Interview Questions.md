

# JavaScript Interview Questions

## Questions & Answers

# Why Use JavaScript?

JavaScript enables dynamic and interactive web content, transforming static pages into engaging user experiences.

## Example:

Imagine a web page where a user submits a form to sign up for a newsletter. Without JavaScript, every form submission would require a full page refresh. With JavaScript:

- Immediate alerts can be given for incorrect email inputs.
- Asynchronous requests allow form submission without refreshing the whole page.
- Immediate feedback can be provided to the user upon submission.

```javascript
document.getElementById("signupForm").addEventListener("submit", function(event) {
    event.preventDefault();  // Prevents the default form submission behavior

    let email = document.getElementById("emailInput").value;

    if (isValidEmail(email)) {
        // Simulating an asynchronous request to a server
        setTimeout(() => {
            alert("Thank you for signing up!");
        }, 1000);
    } else {
        alert("Please enter a valid email.");
    }
});

function isValidEmail(email) {
    let regex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
    return regex.test(email);
}
```

---

### 1. **What is the difference between `==` and `===`?**
   - **Answer**: `==` checks for loose equality and performs type coercion, while `===` checks for strict equality without type coercion.
   - **Example**:
     ```javascript
     "5" == 5;   // true
     "5" === 5;  // false
     ```

### 2. **Explain closures in JavaScript.**
   - **Answer**: A closure is a function that has access to the parent scope's variables, even after the parent function has completed execution.
   - **Example**:
     ```javascript
     function outer() {
       let count = 0;
       return function() { return count++; }
     }
     const increment = outer();
     increment();  // 0
     increment();  // 1
     ```

### 3. **What are promises in JavaScript?**
   - **Answer**: A promise represents a value that might be available now, in the future, or never. It's an object with three states: pending, resolved (fulfilled), or rejected.
   - **Example**:
     ```javascript
     let promise = new Promise((resolve, reject) => {
       setTimeout(() => {
         resolve("Promise resolved!");
       }, 1000);
     });
     ```

### 4. **What is the difference between `var`, `let`, and `const`?**
   - **Answer**: `var` is function-scoped and can be redeclared. `let` is block-scoped, can be reassigned but not redeclared. `const` is block-scoped, cannot be reassigned or redeclared.
   - **Example**:
     ```javascript
     if (true) {
       var varVar = "var";   // function-scoped
       let letVar = "let";   // block-scoped
       const constVar = "const"; // block-scoped, immutable binding
     }
     ```

### 5. **What is the 'this' keyword in JavaScript?**
   - **Answer**: `this` refers to the object it belongs to. Its value can change depending on the context in which it's used (global scope, object, function, or ES6 arrow functions).
   - **Example**:
     ```javascript
     function exampleFunction() {
       console.log(this);
     }
     exampleFunction();  // Window (or global object in non-browser environments)
     ```

### 6. **What is hoisting in JavaScript?**
   - **Answer**: Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their containing scope (function or global) during the compile phase.
   - **Example**:
     ```javascript
     console.log(a);  // undefined
     var a = 5;
     console.log(a);  // 5
     ```

### 7. **What's the difference between a function declaration and a function expression?**
   - **Answer**: Function declarations are hoisted and can be called before they appear in code. Function expressions aren't hoisted, so they cannot be invoked before they're defined.
   - **Example**:
     ```javascript
     console.log(declaredFunction());  // "Declared"
     console.log(expressionFunction());  // TypeError

     function declaredFunction() {
       return "Declared";
     }

     var expressionFunction = function() {
       return "Expression";
     }
     ```

### 8. **What is an arrow function?**
   - **Answer**: Arrow functions are a shorthand way to create functions in ES6 and later. They don't have their own `this` value but inherit it from the enclosing scope.
   - **Example**:
     ```javascript
     const greet = name => `Hello, ${name}!`;
     greet('Alice');  // "Hello, Alice!"
     ```

### 9. **What are async/await and how do they work?**
   - **Answer**: `async/await` is a syntactic feature in ES8 (ES2017) that allows handling asynchronous code in a more synchronous fashion. It's built on top of promises.
   - **Example**:
     ```javascript
     async function fetchData() {
       let response = await fetch('https://api.example.com/data');
       let data = await response.json();
       return data;
     }
     ```

### 10. **How does the `prototype` chain work in JavaScript?**
   - **Answer**: Every object in JavaScript has a reference to its prototype, and can inherit properties and methods from it. This forms a chain leading up to `Object.prototype` at the top.
   - **Example**:
     ```javascript
     function Person(name) {
       this.name = name;
     }
     Person.prototype.sayHello = function() {
       return `Hello, ${this.name}!`;
     }
     const alice = new Person('Alice');
     alice.sayHello();  // "Hello, Alice!"
     ```

---

---

### 11. **How do you differentiate between `null` and `undefined`?**
   - **Answer**: Both represent the absence of value. However, `undefined` is a variable that has been declared but not assigned, whereas `null` is an assignment value that represents no value or no object.
   - **Example**:
     ```javascript
     let notAssigned;
     console.log(notAssigned);  // undefined

     let empty = null;
     console.log(empty);  // null
     ```

### 12. **What are JavaScript data types?**
   - **Answer**: JavaScript has two categories of data types: primitive (string, number, bigint, boolean, undefined, symbol, and null) and object (arrays, functions, and objects).
   - **Example**:
     ```javascript
     let str = "Hello";  // string
     let num = 10;       // number
     let isTrue = false; // boolean
     let obj = {};       // object
     ```

### 13. **Explain the concept of event delegation.**
   - **Answer**: Event delegation is the practice of adding event listeners to a parent element rather than adding them to the descendant elements individually. It leverages event bubbling.
   - **Example**:
     ```javascript
     document.querySelector('ul').addEventListener('click', function(e) {
       if(e.target.tagName === 'LI') {
         console.log(e.target.innerHTML);
       }
     });
     ```

### 14. **How does the JavaScript `map()` method work?**
   - **Answer**: The `map()` method creates a new array with the results of a provided function on every element in the calling array.
   - **Example**:
     ```javascript
     const numbers = [1, 2, 3];
     const doubled = numbers.map(num => num * 2); // [2, 4, 6]
     ```

### 15. **What is the `reduce()` method?**
   - **Answer**: The `reduce()` method processes an array's elements to reduce its values to a single value. It executes a provided function for each array value (from left-to-right) and stores the result.
   - **Example**:
     ```javascript
     const numbers = [1, 2, 3];
     const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0); // 6
     ```

### 16. **How can you deep clone an object?**
   - **Answer**: Deep cloning means creating a copy of an object where the copy also includes unique copies of nested objects. Simple methods like `Object.assign()` only create shallow copies.
   - **Example**:
     ```javascript
     const deepClone = obj => JSON.parse(JSON.stringify(obj));
     ```

### 17. **Explain the difference between synchronous and asynchronous programming.**
   - **Answer**: Synchronous programming runs code sequentially, blocking the next operation until the current one completes. Asynchronous programming allows operations to run in parallel without waiting for the previous one to complete.
   - **Example**:
     ```javascript
     console.log("Start");          // Synchronous
     setTimeout(() => {             // Asynchronous
       console.log("Middle");
     }, 0);
     console.log("End");            // Synchronous
     ```

### 18. **What are JavaScript decorators?**
   - **Answer**: Decorators are a design pattern primarily used to add new functionalities to objects or methods without modifying their structure. They are currently at the proposal stage for JavaScript but are used in TypeScript.
   - **Example**: Not applicable in vanilla JavaScript as of my last training data in 2021, but they are prevalent in TypeScript and other languages.

### 19. **Explain destructuring in ES6.**
   - **Answer**: Destructuring allows binding properties of an array or object into distinct variables.
   - **Example**:
     ```javascript
     let [a, b] = [1, 2];           // array destructuring
     let {x, y} = {x: 10, y: 20};  // object destructuring
     ```

### 20. **What are template literals in ES6?**
   - **Answer**: Template literals are string literals that can span multiple lines and have embedded expressions, denoted by `${expression}`.
   - **Example**:
     ```javascript
     let word = 'world';
     console.log(`Hello, ${word}!`);  // "Hello, world!"
     ```

---

