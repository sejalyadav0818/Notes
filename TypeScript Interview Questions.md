----

# TypeScript Interview Questions :

## Questions & Answers

### 1. **What is TypeScript and why would you use it?**
   - **Answer**: TypeScript is a statically-typed superset of JavaScript that compiles to plain JavaScript. It provides type safety, improved developer tooling, and better code quality.
   - **Example**: No code example necessary for this conceptual question.

### 2. **How does TypeScript differ from JavaScript?**
   - **Answer**: The key difference is TypeScript's static type system. While JavaScript is dynamically-typed, TypeScript adds type annotations and interfaces to provide type checks at compile time.
   - **Example**:
     ```typescript
     let x: number = 5;  // TypeScript with type annotation
     let y = 5;          // JavaScript
     ```

### 3. **What is the purpose of the `any` type in TypeScript?**
   - **Answer**: The `any` type is a type that could represent any JavaScript value with no type-checking constraints. It's useful when you're unsure of a variable's type, but overusing it can negate the benefits of TypeScript.
   - **Example**:
     ```typescript
     let notSure: any = 4;
     notSure = "maybe a string";
     ```

### 4. **Explain interfaces in TypeScript.**
   - **Answer**: Interfaces in TypeScript allow you to define the structure of an object, ensuring that the object has specific properties with certain types.
   - **Example**:
     ```typescript
     interface Person {
       firstName: string;
       lastName: string;
     }
     ```

### 5. **How do you define optional properties in an interface?**
   - **Answer**: You can mark a property as optional using the `?` character.
   - **Example**:
     ```typescript
     interface Config {
       name: string;
       description?: string; // This is an optional property
     }
     ```

### 6. **How does TypeScript handle `null` and `undefined`?**
   - **Answer**: By default, TypeScript considers `null` and `undefined` assignable to any type. However, with the `strictNullChecks` flag enabled, `null` and `undefined` are distinct types and not assignable to other types.
   - **Example**:
     ```typescript
     let str: string = null;  // Error with strictNullChecks enabled
     ```

### 7. **Explain function overloading in TypeScript.**
   - **Answer**: TypeScript supports function overloading by defining multiple type signatures for a function, followed by its implementation. This allows the function to handle different argument types and counts.
   - **Example**:
     ```typescript
     function add(a: number, b: number): number;
     function add(a: string, b: string): string;

     function add(a: any, b: any): any {
       return a + b;
     }
     ```

### 8. **How do generics enhance TypeScript?**
   - **Answer**: Generics allow you to define type-safe data structures without committing to an actual data type. This enhances code reusability without sacrificing type safety.
   - **Example**:
     ```typescript
     function identity<T>(arg: T): T {
       return arg;
     }
     ```

### 9. **What is a union type in TypeScript?**
   - **Answer**: Union types allow you to specify that a value can be one of several types using the `|` character.
   - **Example**:
     ```typescript
     let mixedType: number | string;
     mixedType = "hello";
     mixedType = 10;
     ```

### 10. **What are type guards in TypeScript?**
   - **Answer**: Type guards are expressions that validate the type of a variable at runtime. They help in scenarios where a variable's type is uncertain.
   - **Example**:
     ```typescript
     function isString(value: any): value is string {
         return typeof value === 'string';
     }
     ```

---
