
---

# Node.js Interview Question

### Question:

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

