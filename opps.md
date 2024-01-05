# Object-Oriented Programming (OOP) Interview Questions and Answers

1. **What is Object-Oriented Programming (OOP)?**
   - **Answer:** OOP is a programming paradigm that organizes code into objects, which encapsulate data and behavior. For example, consider a `Car` object that encapsulates properties like `speed` and behaviors like `accelerate`.

2. **What is a class?**
   - **Answer:** A class is a blueprint or template for creating objects. An example is a `Person` class that defines properties like `name` and methods like `eat()`.

3. **What is an object?**
   - **Answer:** An object is an instance of a class. Consider an instance of the `Person` class as an object with specific values for `name` and behaviors like `eat()`.

4. **Explain the four principles of OOP.**
   - **Answer:**
     - **Encapsulation:** Encapsulate data and methods within a class. Example: A `BankAccount` class with private variables `balance` and methods like `withdraw()`.
     - **Abstraction:** Hide complex details and expose only essential features. Example: A `RemoteControl` class abstracts the complexities of interacting with a device.
     - **Inheritance:** Create a new class by inheriting properties from an existing class. Example: A `Car` class inherits from a more general `Vehicle` class.
     - **Polymorphism:** Allow objects of different types to be treated as objects of a common type. Example: A `Shape` class with different subclasses like `Circle` and `Rectangle`.

5. **What is encapsulation?**
   - **Answer:** Encapsulation is bundling data and methods that operate on the data within a single unit (class). Example: A `Dog` class encapsulating properties like `color` and methods like `bark()`.

6. **Give an example of encapsulation.**
   - **Answer:** In a `Rectangle` class, private variables like `length` and `width` encapsulate the rectangle's properties, and methods like `calculateArea()` encapsulate its behavior.

7. **What is inheritance?**
   - **Answer:** Inheritance is the mechanism by which a new class inherits properties and behaviors from an existing class. Example: A `Student` class inheriting from a more general `Person` class.

8. **Provide an example of inheritance.**
   - **Answer:** A `Bird` class might inherit from an abstract `Animal` class, gaining properties like `name` and behaviors like `eat()`.

9. **What is polymorphism?**
   - **Answer:** Polymorphism allows objects of different types to be treated as objects of a common type. Example: A `Bird` and a `Dog` both implementing a common `makeSound()` method.

10. **Explain method overloading.**
    - **Answer:** Method overloading involves defining multiple methods with the same name but different parameters in a class. Example: A `Calculator` class with `add(int a, int b)` and `add(double a, double b)` methods.

11. **Provide an example of method overloading.**
    - **Answer:** A `MathOperations` class might have overloaded methods for addition, such as `add(int a, int b)` and `add(double a, double b)`.

12. **Explain method overriding.**
    - **Answer:** Method overriding occurs when a subclass provides a specific implementation for a method already defined in its superclass. Example: A `Square` class overriding the `calculateArea()` method from its base `Rectangle` class.

13. **Give an example of method overriding.**
    - **Answer:** In a `Shape` hierarchy, a `Circle` class can override the `calculateArea()` method to provide a specific implementation for calculating the area of a circle.

14. **What is abstraction?**
    - **Answer:** Abstraction involves hiding complex implementation details and exposing only essential features. Example: A `Car` class abstracts the complexities of its engine, exposing methods like `start()` and `stop()`.

15. **Give an example of abstraction.**
    - **Answer:** A `DatabaseConnection` class abstracts the details of connecting to a database, exposing methods like `connect()` and `disconnect()`.

16. **What is the difference between abstract class and interface?**
    - **Answer:** An abstract class can have both abstract and concrete methods, while an interface can only have abstract methods. An example is an `Animal` abstract class with a `makeSound()` method versus an `Playable` interface with a `play()` method.

17. **Explain the concept of a constructor.**
    - **Answer:** A constructor is a special method in a class that is automatically called when an object is instantiated. For example, a `Person` class might have a constructor to initialize the `name` property.

18. **What is a destructor?**
    - **Answer:** A destructor is a method called when an object is about to be destroyed or deallocated. In languages like Java, it's managed by the garbage collector, and explicit destructors are not used.

19. **What is the purpose of the `super` keyword?**
    - **Answer:** The `super` keyword is used to call methods of the superclass in the subclass. For instance, in a `Square` class, `super.calculateArea()` could invoke the `calculateArea()` method of its parent `Rectangle` class.

20. **Explain the concept of an interface.**
    - **Answer:** An interface is a collection of abstract methods, defining a contract for classes that implement it. An example is a `Runnable` interface with a `run()` method.

21. **What is a static method?**
    - **Answer:** A static method belongs to the class rather than an instance and can be called using the class name. Example: A `Math` class with a static method like `Math.sqrt()`.

22. **What is a static variable?**
    - **Answer:** A static variable is a class-level variable shared by all instances. Example: A `Counter` class with a static variable `count` to keep track of the number of instances created.

23. **Explain the concept of composition.**
    - **Answer:** Composition is combining different classes to create a more complex one. Example: A `Car` class composed of `Engine` and `Wheel` classes.

24. **What is the difference between composition and inheritance?**
    - **Answer:** Inheritance creates a new class by using properties from an existing class, while composition combines different classes. For example, a `Bicycle` class might use composition to include a `Wheel` class rather than inheriting from a `Vehicle` class.

25. **What is the `final` keyword used for?**
    - **Answer:** In Java, `final` can be applied to a class, method, or variable. A `final` class cannot be extended, a `final` method cannot be overridden, and a `final` variable is a constant.

26. **Explain the concept of a package.**
    - **Answer:** A package is a way of organizing related classes and interfaces into a single namespace. Example: A `util` package containing utility classes like `StringUtils` and `ArrayUtils`.

27. **What is the difference between method overloading and method overriding?**
    - **Answer:** Method overloading involves defining multiple methods with the same name but different parameters in the same class. Method overriding occurs when a subclass provides a specific implementation for a method in its superclass.

28. **What is the `this` keyword used for?**
    - **Answer:** The `this` keyword refers to the current instance of the class and is used to differentiate instance variables from local variables when they have the same name.

29. **Explain the concept of a getter and setter.**
    - **Answer:** Getter methods retrieve the values of private instance variables, and setter methods modify the values. Example: A `Person` class with `getName()` and `setName()` methods.

30. **What is the purpose of the `toString()` method?**
    - **Answer:** The `toString()` method converts an object to a string representation. Example: Overriding `toString()` in a `Book` class to provide details like title, author, and publication date.

31. **What is a singleton class?**
    - **Answer:** A singleton class allows only one instance of itself to be created. Example: A `Configuration` class ensuring there's only one instance to manage application settings.

32. **Explain the concept of multiple inheritance.**
    - **Answer:** Multiple inheritance allows a class to inherit from more than one class. Example: A `FlyingCar` class inheriting from both `Car` and `Airplane` classes.

33. **What is the diamond problem?**
    - **Answer:** The diamond problem occurs in languages supporting multiple inheritance when a class inherits from two classes with a common ancestor. It can lead to ambiguity in method resolution.

34. **What is a virtual function?**
    - **Answer:** In languages like C++, a virtual function is a function declared in a base class and overridden by a derived class, allowing dynamic method binding.

35. **Explain the concept of method hiding.**
    - **Answer:** Method hiding occurs when a subclass redefines a static method from its superclass. Example: A `Shape` class with a static method `draw()` might be hidden by a subclass `Circle` with its own static `draw()` method.

36. **What is the `instanceof` operator used for?**
    - **Answer:** The `instanceof` operator is used to check if an object is an instance of a particular class or interface. Example: `if (obj instanceof Car)`.

37. **What is the difference between shallow copy and deep copy?**
    - **Answer:** Shallow copy creates a new object but does not duplicate the objects within it. Deep copy creates a new object and duplicates the objects within it.

38. **Explain the concept of a proxy class.**
    - **Answer:** A proxy class acts as an interface to another class, often used for implementing lazy loading, logging, access control, or monitoring. Example: A `SecurityProxy` class controlling access to sensitive methods in a `BankAccount` class.

39. **What is the `final` class in Java?**
    - **Answer:** A `final` class in Java cannot be extended. Example: A `MathUtils` class might be marked as `final` to prevent any further modification.

40. **What is the purpose of the `abstract` keyword?**
    - **Answer:** The `abstract` keyword is used to declare abstract classes and methods. Abstract classes cannot be instantiated, and abstract methods must be implemented by concrete subclasses.

41. **What is the difference between `const` and `readonly` in C#?**
    - **Answer:** In C#, `const` is a compile-time constant, while `readonly` can only be assigned at runtime or in the constructor. Example: `const int MAX_VALUE = 100;` versus `readonly int maxValue = 100;`.

42. **Explain the concept of garbage collection.**
    - **Answer:** Garbage collection automatically reclaims memory occupied by objects that are no longer in use, preventing memory leaks. Example: In Java, the garbage collector identifies and collects unreferenced objects.

43. **What is the role of the `finalize()` method in Java?**
    - **Answer:** The `finalize()` method is called by the garbage collector before reclaiming the memory occupied by an object, allowing for cleanup operations. Example: Closing a file or releasing resources.

44. **What is the Observer design pattern?**
    - **Answer:** The Observer pattern defines a one-to-many dependency between objects. Example: A `Subject` notifying its `Observers` when its state changes, like a stock market ticker.

45. **Explain the concept of method chaining.**
    - **Answer:** Method chaining is a programming technique where multiple methods can be called sequentially on the same object, returning the modified object after each method call. Example: `StringBuilder.append("Hello").append(" ").append("World")`.

46. **What is the `@Override` annotation used for in Java?**
    - **Answer:** The `@Override` annotation in Java is used to indicate that a method in a subclass is intended to override a method in its superclass, helping catch errors at compile-time.

47. **What is the SOLID principles in OOP?**
    - **Answer:**
      - **Single Responsibility Principle (SRP):** A class should have only one reason to change. Example: A `FileManager` class responsible for file operations.
      - **Open/Closed Principle (OCP):** Software entities should be open for extension but closed for modification. Example: Using interfaces and abstract classes for extensibility.
      - **Liskov Substitution Principle (LSP):** Subtypes must be substitutable for their base types. Example: A `Bird` subclass should be substitutable for its `Animal` base type.
      - **Interface Segregation Principle (ISP):** A class should not be forced to implement interfaces it does not use. Example: Splitting a large interface into smaller, more specific ones.
      - **Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules; both should depend on abstractions. Example: Using dependency injection to invert dependencies.

48. **What is the difference between early binding and late binding?**
    - **Answer:** Early binding (static binding) occurs at compile-time, while late binding (dynamic binding) occurs at runtime. Example: Method overloading is an example of early binding, and method overriding is an example of late binding.

49. **Explain the concept of covariance and contravariance in C#.**
    - **Answer:** Covariance allows a derived class to be used where its base class is expected, while contravariance allows a base class to be used where its derived class is expected. This is primarily related to parameter types in method signatures.

50. **What is the purpose of the `sealed` keyword in C#?**
    - **Answer:** The `sealed` keyword in C# is used to prevent a class from being inherited. Example: Marking a `DatabaseConnection` class as `sealed` to prevent further extension and maintain a specific design.
