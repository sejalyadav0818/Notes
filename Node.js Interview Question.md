
---

# Node.js Interview Question

## Questions & Answers

### 1. **What is Node.js?**
   - **Answer**: Node.js is a runtime environment built on Chrome's V8 JavaScript engine, enabling server-side execution of JavaScript.
   - **Example**: Traditional client-side scripting with JavaScript manipulates DOM elements, but with Node.js, you can create a web server using JavaScript.

### 2. **What is the event loop in Node.js?**
   - **Answer**: The event loop facilitates asynchronous operations, allowing Node.js to achieve non-blocking I/O operations, even with JavaScript being single-threaded.
   - **Example**: When reading a file, Node doesn't wait for the operation to complete. Instead, it continues executing other code and processes the file when ready.

### 3. **What is NPM?**
   - **Answer**: NPM (Node Package Manager) is Node.js's default package manager, used for installing and managing packages or modules for Node.js applications.
   - **Example**: Running `npm install express` installs the Express.js framework.

### 4. **Explain Callback in Node.js.**
   - **Answer**: A callback is a function passed to another, invoked after the latter's completion, aiding in asynchronous operations.
   - **Example**:
     ```javascript
     fs.readFile('input.txt', function (err, data) {
       if (err) return console.error(err);
       console.log(data.toString());
     });
     ```

### 5. **Differences between `async/await` and Promises in Node.js?**
   - **Answer**: Both are asynchronous handling techniques. Promises symbolize the completion or failure of an operation. In contrast, `async/await` provides a cleaner syntax, making asynchronous code resemble synchronous ones.
   - **Example**:
     - Promise:
       ```javascript
       doSomethingAsync()
         .then(result => console.log(result))
         .catch(error => console.log(error));
       ```
     - async/await:
       ```javascript
       async function exampleFunction() {
         try {
           let result = await doSomethingAsync();
           console.log(result);
         } catch (error) {
           console.log(error);
         }
       }
       ```

### 6. **How can you prevent callback hell in Node.js?**
   - **Answer**: Callback hell, or "Pyramid of Doom", can be tamed through code modularization, using named functions, and implementing Promises or `async/await`.
   - **Example**: Opting for `async/await` over nested callbacks offers cleaner and more legible code.

### 7. **What is Express.js?**
   - **Answer**: Express.js is a minimal yet powerful Node.js web application framework, offering a suite of tools for web and mobile applications.
   - **Example**:
     ```javascript
     const express = require('express');
     const app = express();
     app.get('/', (req, res) => res.send('Hello World!'));
     app.listen(3000, () => console.log('Server up on port 3000'));
     ```

### 8. **Handling errors in Node.js?**
   - **Answer**: Error management in Node.js can be achieved using callbacks, events, middleware (like in Express.js), and try-catch (primarily with async/await).
   - **Example** (in Express.js):
     ```javascript
     app.use((err, req, res, next) => {
       console.error(err.stack);
       res.status(500).send('Oops! Something went wrong.');
     });
     ```

### 9. **Creating a RESTful API using Node.js?**
   - **Answer**: With frameworks such as Express.js, you can define routes in line with the HTTP methods (GET, POST, PUT, DELETE) to fashion a RESTful API.
   - **Example**:
     ```javascript
     const express = require('express');
     const app = express();

     app.get('/items', (req, res) => {
       // List items
     });

     app.post('/items', (req, res) => {
       // Add an item
     });

     app.listen(3000);
     ```

### 10. **What's middleware in Express.js?**
   - **Answer**: Middleware functions are intermediary operations with access to the request (`req`), response (`res`), and the next function in Express's request-response lifecycle.
   - **Example**: A logging middleware:
     ```javascript
     app.use((req, res, next) => {
       console.log('Time:', Date.now());
       next();
     });
     ```

---


**Explain the difference between `async/await` and `Promises` in Node.js. Provide an example for each.**

### Answer:

In Node.js, both `async/await` and `Promises` are used to handle asynchronous operations, but they differ in their usage and handling.

#### 1. Promises:

- Introduced as part of ES6.
- A Promise represents a value that might be available now, or in the future, or never.
- It provides methods like `.then()` for callback execution once the Promise resolves and `.catch()` for error handling.

##### Example:

```javascript
const promiseFunction = () => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('Data from Promise');
        }, 1000);
    });
}

promiseFunction()
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error(error);
    });
```

#### 2. async/await:

- Introduced in ES8.
- It's built on top of Promises and provides a more synchronous-looking way to write asynchronous code.
- Using `async/await` makes it easier to read and write, especially for complex asynchronous operations.

##### Example:

```javascript
const asyncFunction = async () => {
    return 'Data from async/await';
}

const callAsyncFunction = async () => {
    try {
        const data = await asyncFunction();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}

callAsyncFunction();
```

#### Comparison:

1. **Readability**: `async/await` often results in cleaner and more readable code, especially for sequences of asynchronous operations.
2. **Error Handling**: With `async/await`, you can use traditional `try/catch` blocks, whereas with Promises, you would use `.catch()`.
3. **Underlying Mechanism**: `async/await` is built on top of Promises, so it's essentially syntactic sugar, providing a new way to work with Promises.
4. **Return Value**: An `async` function always returns a Promise.

---

