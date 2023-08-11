
---

# Frontend State Management Interview Questions :

State management is a key part of frontend development, especially when building complex applications. Tools and libraries like Redux, Redux Toolkit, Context API, and Redux Saga are frequently used for this purpose. 

## Questions & Answers

### 1. **What is Redux? Why use it?**
   - **Answer**: Redux is a predictable state container for JavaScript apps. It helps you manage the global state of an application in an immutable fashion.
   - **Example**: When multiple components need to access the same state, Redux provides a centralized store to manage and update that state efficiently.

### 2. **What is Local Storage? How does it differ from Session Storage and Cookies?**
   - **Answer**: Local Storage is a web storage solution that allows scripts to store key-value pairs in a web browser with no expiration time. Session Storage is similar but has a data lifespan for a session duration. Cookies are small pieces of data stored by websites with an expiration date, often used for sessions and tracking.
   - **Example**:
     ```javascript
     localStorage.setItem("username", "JohnDoe");
     ```

### 3. **Explain Redux Toolkit and its benefits.**
   - **Answer**: Redux Toolkit is the official, opinionated, batteries-included toolset for efficient Redux development. It simplifies many Redux tasks, reduces boilerplate code, and integrates best practices.
   - **Example**: 
     ```javascript
     import { createSlice } from '@reduxjs/toolkit';
     
     const counterSlice = createSlice({
       name: 'counter',
       initialState: 0,
       reducers: {
         increment: state => state + 1,
         decrement: state => state - 1
       }
     });
     ```

### 4. **What is the Context API in React?**
   - **Answer**: Context API provides a way to share values (state or functions) between components without having to explicitly pass them via props.
   - **Example**:
     ```javascript
     const ThemeContext = React.createContext('light');

     // To use it:
     <ThemeContext.Provider value="dark">
       <ChildComponent />
     </ThemeContext.Provider>
     ```

### 5. **Explain the concept of Global Context.**
   - **Answer**: Global Context is a pattern where a single Context object manages state and methods that are accessible by any component in the application, ensuring a single source of truth and avoiding prop drilling.
   - **Example**:
     ```javascript
     const GlobalContext = React.createContext();

     function App() {
       return (
         <GlobalContext.Provider value={{ userName: "John", setUser: () => {/*...*/} }}>
           <ComponentA />
         </GlobalContext.Provider>
       );
     }
     ```

### 6. **What is Redux Saga? How does it differ from Redux Thunk?**
   - **Answer**: Redux Saga is a middleware library used to handle side effects in Redux apps using "sagas" (generators). It provides a cleaner and more testable solution compared to Redux Thunk, which handles side effects using thunks (functions).
   - **Example**:
     ```javascript
     import { call, put, takeEvery } from 'redux-saga/effects';

     function* fetchUser(action) {
       try {
         const user = yield call(Api.fetchUser, action.payload.userId);
         yield put({ type: "USER_FETCH_SUCCEEDED", user });
       } catch (e) {
         yield put({ type: "USER_FETCH_FAILED", message: e.message });
       }
     }

     function* mySaga() {
       yield takeEvery("USER_FETCH_REQUESTED", fetchUser);
     }
     ```

---

