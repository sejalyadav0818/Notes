
---

# OOP (Object-Oriented Programming) Interview Questions :

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects" which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods). This README provides commonly asked OOP interview questions.

## Questions & Answers

### 1. **What are the four fundamental OOP principles?**
   - **Answer**: The four main OOP principles are Encapsulation, Inheritance, Polymorphism, and Abstraction.

### 2. **Explain Encapsulation.**
   - **Answer**: Encapsulation refers to bundling data (attributes) and methods (functions) that operate on the data into a single unit or class. It restricts direct access to some of the object's components, which is a means of preventing unintended interference.
   - **Example**:
     ```java
     public class Employee {
       private String name;

       public String getName() {
         return name;
       }

       public void setName(String newName) {
         this.name = newName;
       }
     }
     ```

### 3. **What is Inheritance?**
   - **Answer**: Inheritance is a mechanism where a new class inherits properties and behavior (methods) from an existing class. It promotes code reusability and establishes a relationship between the parent (superclass) and child (subclass) classes.
   - **Example**:
     ```java
     class Animal {
       void eat() { 
         // eat something 
       }
     }

     class Dog extends Animal {
       void bark() { 
         // bark 
       }
     }
     ```

### 4. **Describe Polymorphism.**
   - **Answer**: Polymorphism allows objects of different classes to be treated as objects of a common superclass. The most common use is when a parent class reference is used to refer to a child class object.
   - **Example**:
     ```java
     class Animal {
       void sound() {
         System.out.println("Animal makes a sound");
       }
     }

     class Dog extends Animal {
       void sound() {
         System.out.println("Dog barks");
       }
     }

     class Cat extends Animal {
       void sound() {
         System.out.println("Cat meows");
       }
     }
     ```

### 5. **What is Abstraction?**
   - **Answer**: Abstraction refers to hiding the complex implementation details and showing only the essential features of an object. It reduces code complexity and at the same time, it makes the system efficient.
   - **Example**: 
     Abstract classes or interfaces in languages like Java and C# provide abstraction. They can have abstract methods (methods without a body) that should be implemented by derived classes.

### 6. **What's the difference between a class and an object?**
   - **Answer**: A class is a blueprint or template for creating objects (a particular data structure), providing initial values for state (attributes), and implementations of behavior (methods). An object is an instance of a class, with its actual content.

### 7. **Define Association, Aggregation, and Composition.**
   - **Answer**: 
     - **Association**: A bi-directional relationship between two classes. It defines a relationship between objects.
     - **Aggregation**: A specialized form of Association where one class belongs to another class but has its lifecycle.
     - **Composition**: A strict form of Aggregation, implying ownership between the related objects. If the parent object is deleted, its composed objects will also be deleted.

### 8. **What is method overriding and overloading?**
   - **Answer**: 
     - **Overloading**: Occurs when two or more methods in the same class have the same method name but different parameters.
     - **Overriding**: Happens when a subclass has the same method as declared in the parent class. The method in the child class should have the same name, return type, and parameters as the one in its parent class.

### 9. **Explain the concept of constructors.**
   - **Answer**: A constructor is a special method used to initialize objects. It gets called when an object is instantiated, and it typically sets the initial state of the object.
   
### 10. **What is the difference between `static` and `instance` methods?**
   - **Answer**: Static methods belong to the class itself and don't operate on instances, while instance methods belong to the instance of the class and can access instance data.

---

Reviewing and understanding these OOP concepts will prepare you for a variety of software engineering and development interviews. Always complement this information with hands-on coding exercises and real-world application to solidify your understanding.

---

You can copy and paste the above content into a `README.md` file for your GitHub repository. Adjustments might be required to ensure it matches your desired style and content flow.Certainly! Object-Oriented Programming (OOP) is a fundamental programming paradigm that is commonly addressed in interviews. Here's a `README.md` focusing on frequently asked OOP interview questions.

---

# OOP (Object-Oriented Programming) Interview Preparation

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects" which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods). This README provides commonly asked OOP interview questions.

## Questions & Answers

### 1. **What are the four fundamental OOP principles?**
   - **Answer**: The four main OOP principles are Encapsulation, Inheritance, Polymorphism, and Abstraction.

### 2. **Explain Encapsulation.**
   - **Answer**: Encapsulation refers to bundling data (attributes) and methods (functions) that operate on the data into a single unit or class. It restricts direct access to some of the object's components, which is a means of preventing unintended interference.
   - **Example**:
     ```java
     public class Employee {
       private String name;

       public String getName() {
         return name;
       }

       public void setName(String newName) {
         this.name = newName;
       }
     }
     ```

### 3. **What is Inheritance?**
   - **Answer**: Inheritance is a mechanism where a new class inherits properties and behavior (methods) from an existing class. It promotes code reusability and establishes a relationship between the parent (superclass) and child (subclass) classes.
   - **Example**:
     ```java
     class Animal {
       void eat() { 
         // eat something 
       }
     }

     class Dog extends Animal {
       void bark() { 
         // bark 
       }
     }
     ```

### 4. **Describe Polymorphism.**
   - **Answer**: Polymorphism allows objects of different classes to be treated as objects of a common superclass. The most common use is when a parent class reference is used to refer to a child class object.
   - **Example**:
     ```java
     class Animal {
       void sound() {
         System.out.println("Animal makes a sound");
       }
     }

     class Dog extends Animal {
       void sound() {
         System.out.println("Dog barks");
       }
     }

     class Cat extends Animal {
       void sound() {
         System.out.println("Cat meows");
       }
     }
     ```

### 5. **What is Abstraction?**
   - **Answer**: Abstraction refers to hiding the complex implementation details and showing only the essential features of an object. It reduces code complexity and at the same time, it makes the system efficient.
   - **Example**: 
     Abstract classes or interfaces in languages like Java and C# provide abstraction. They can have abstract methods (methods without a body) that should be implemented by derived classes.

### 6. **What's the difference between a class and an object?**
   - **Answer**: A class is a blueprint or template for creating objects (a particular data structure), providing initial values for state (attributes), and implementations of behavior (methods). An object is an instance of a class, with its actual content.

### 7. **Define Association, Aggregation, and Composition.**
   - **Answer**: 
     - **Association**: A bi-directional relationship between two classes. It defines a relationship between objects.
     - **Aggregation**: A specialized form of Association where one class belongs to another class but has its lifecycle.
     - **Composition**: A strict form of Aggregation, implying ownership between the related objects. If the parent object is deleted, its composed objects will also be deleted.

### 8. **What is method overriding and overloading?**
   - **Answer**: 
     - **Overloading**: Occurs when two or more methods in the same class have the same method name but different parameters.
     - **Overriding**: Happens when a subclass has the same method as declared in the parent class. The method in the child class should have the same name, return type, and parameters as the one in its parent class.

### 9. **Explain the concept of constructors.**
   - **Answer**: A constructor is a special method used to initialize objects. It gets called when an object is instantiated, and it typically sets the initial state of the object.
   
### 10. **What is the difference between `static` and `instance` methods?**
   - **Answer**: Static methods belong to the class itself and don't operate on instances, while instance methods belong to the instance of the class and can access instance data.

---
