
---

# Table of Contents:

- [Number Reverser](#number-reverser)
- [Prime Number Checker](#prime-number-checker)
- [Number Palindrome Checker](#number-palindrome-checker)
- [Greatest Among Three Numbers](#greatest-among-three-numbers)
- [Odd or Even Number Checker](#odd-or-even-number-checker)
- [Leap Year Checker](#leap-year-checker)
- [Swap Two Numbers Without Using a Third Variable](#Swap-Two-Numbers-Without-Using-a-Third-Variable)
- [Factorial Calculator](#Factorial-Calculator)
- [Factorial Calculator Using Recursions](#Factorial-Calculator-Using-Recursions)

---


---

# Number Reverser

**Purpose**: This program reverses the digits of a given number.

## Code:

```java
import java.util.*;

class NumberReverser {
    public static void main(String[] args) {
        int n, r;
        System.out.print("Enter number: ");
        Scanner s = new Scanner(System.in);
        n = s.nextInt();
        s.close();
        
        while(n > 0) {
            r = n % 10;
            System.out.print(r);
            n = n / 10;
        }
        System.out.println();
    }
}
```

## Explanation:

1. The user is prompted to input a number.
2. The program then iteratively takes the last digit of the number and prints it, thus reversing the order of the digits.
3. This is achieved by using the modulo operation (`%`) to get the last digit and integer division (`/`) to remove the last digit.

## Sample Output:

**Input**: 
```
Enter number: 789
```

**Output**: 
```
987
```

---


---

# Prime Number Checker

**Purpose**: This program determines if a given number is prime.

## Code:

```java
import java.util.*;

class isNumberPrime {
    public static void main(String[] args) {
        int n;
        int temp = 0;
        
        System.out.println("Enter number");
        Scanner input = new Scanner(System.in);
        n = input.nextInt();
        input.close();
        
        for(int i = 2; i <= Math.sqrt(n); i++) {
            if(n % i == 0) {
                temp = 1;
                break;
            }
        }

        if(temp == 0 && n > 1) { // Corrected the condition here
            System.out.println("Number is prime");
        } else {
            System.out.println("Number is not prime");
        }
    }
}
```

## Explanation:

1. The user is prompted to input a number.
2. The program checks if this number has any divisors between 2 and the square root of the number. If any are found, the number is not prime.
3. The final decision (prime or not) is printed out to the user.

## Sample Output:

**Input**: 
```
Enter number
17
```

**Output**: 
```
Number is prime
```

**Input**: 
```
Enter number
4
```

**Output**: 
```
Number is not prime
```


---

# Number Palindrome Checker

**Purpose**: This program determines if a given number is a palindrome, i.e., it reads the same forward and backward.

## Code:

```java
import java.util.*;

class isNumberPalindrome {
    public static void main(String[] args) {
        int n, original, reverse = 0, r;
        
        System.out.println("Enter Number");
        Scanner sc= new Scanner(System.in);
        n = sc.nextInt();
        original = n;
        
        while(n > 0) {
            r = n % 10;
            reverse = reverse * 10 + r;
            n = n / 10;
        }
        
        if (original == reverse) {
            System.out.println("Number is Palindrome");
        } else {
            System.out.println("Number is not Palindrome");
        }
        
        sc.close();
    }
}
```

## Short Explanation:

1. **User Input**: The program prompts the user to enter a number.
2. **Reversing**: The program then iteratively takes the last digit of the number and constructs its reverse.
   - For example, if the user inputs `121`:
     - 1st iteration: `reverse` becomes `1`
     - 2nd iteration: `reverse` becomes `12`
     - 3rd iteration: `reverse` becomes `121`
3. **Comparison**: The original number and its reverse are compared.
4. **Output**: The program then notifies the user if the number is a palindrome or not.

## Sample Output:

For an input of `121`, the program will output:

```
Enter Number
121
Number is Palindrome
```

For an input of `123`, the program will output:

```
Enter Number
123
Number is not Palindrome
```

---

---

# Greatest Among Three Numbers

**Purpose**: This Java program determines the greatest among three numbers entered by the user.

## Code:

```java
import java.util.*;

public class graterOfThree {
    public static void main(String[] args) {
        int a, b, c;
        System.out.println("Enter 3 numbers");  
        Scanner sc = new Scanner(System.in);
        a = sc.nextInt();
        b = sc.nextInt();
        c = sc.nextInt();
        sc.close();

        if(a > b && a > c) {
            System.out.println("A is greater");
        } else if(b > a && b > c) {
            System.out.println("B is greater"); 
        } else {
            System.out.println("C is greater"); 
        }
    }
}
```

## How it Works:

1. The program prompts the user to enter three numbers.
2. Using conditional statements, it checks:
   - If `a` is greater than both `b` and `c`, it will print "A is greater".
   - If the above condition is not met and `b` is greater than both `a` and `c`, it will print "B is greater".
   - If neither of the above conditions is true, it will print "C is greater", assuming that `c` is the greatest of the three.

## Sample Execution:

**Input**: 
```
Enter 3 numbers
5 3 4
```

**Output**: 
```
A is greater
```

---

# Odd or Even Number Checker

**Purpose**: This Java program determines whether the given number is odd or even.

## Code:

```java
import java.util.*;

class numberisOddorEven {
    public static void main(String[] args) {
        int number = 0;
        Scanner sc = new Scanner(System.in);
        number = sc.nextInt();
        sc.close();

        if(number % 2 == 0) {
            System.out.println("Number is Even");
        } else {
            System.out.println("Number is Odd");
        }
    }
}
```

## How it Works:

1. The program waits for the user to input a number.
2. It then checks the remainder when the number is divided by 2:
   - If the remainder is 0, it means the number is even, and the program will print "Number is Even".
   - Otherwise, it will print "Number is Odd".

## Sample Execution:

**Input**: 
```
6
```

**Output**: 
```
Number is Even
```

**Input**: 
```
7
```

**Output**: 
```
Number is Odd
```

---
---

# Leap Year Checker

**Purpose**: This Java program determines whether the provided year is a leap year or not.

## Code:

```java
import java.util.*;

class numberIsLeapyer {
    public static void main(String[] args) {
        int year = 0;
        System.out.println("Enter a year");
        Scanner sc = new Scanner(System.in);
        year = sc.nextInt();
        sc.close();

        if((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)) {
            System.out.println("year is leap year");
        } else {
            System.out.println("year is not leap year");
        }
    }
}
```

## How it Works:

1. The program prompts the user to input a year.
2. The year is then checked against the following conditions to determine if it's a leap year:
   - It's divisible by 400, OR
   - It's divisible by 4 but NOT divisible by 100.
3. Based on these conditions:
   - If true, the program prints "year is leap year".
   - Otherwise, it prints "year is not leap year".

## Leap Year Rule:

Leap years are necessary to sync the calendar year with the solar year. A leap year has 366 days, with an additional day in February, making it 29 days long.

A year is a leap year if:
   - It's divisible by 4, except for end-of-century years, which must be divisible by 400. This means that the year 2000 was a leap year, although 1900 was not.

## Sample Execution:

**Input**: 
```
2000
```

**Output**: 
```
year is leap year
```

**Input**: 
```
1900
```

**Output**: 
```
year is not leap year
```

---


---

# Swap Two Numbers Without Using a Third Variable

**Purpose**: This program demonstrates how to swap the values of two variables without using a third temporary variable.

## Code:

```java
import java.util.*;

class swapTwonoWithoutThreeVarable {
    public static void main(String[] args) {
        int a, b;
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Enter a");
        a = sc.nextInt();
        
        System.out.println("Enter b");
        b = sc.nextInt();
        
        // Swapping logic without third variable
        a = a + b;
        b = a - b;
        a = a - b;
        
        System.out.println("a " + a);
        System.out.println("b " + b);
        sc.close();
    }
}
```

## How it Works:

1. The program prompts the user to input two numbers.
2. Using arithmetic operations, the program swaps the values:
   - `a` is updated to the sum of `a` and `b`.
   - `b` is updated to the difference between the new value of `a` and `b`, which gives the original value of `a`.
   - `a` is again updated to the difference between the new value of `a` and the new value of `b`, which gives the original value of `b`.
3. The swapped values are then printed.

## Explanation:

This method makes use of arithmetic operations to swap values. By adding the two values, and then subtracting them in a specific order, we can effectively swap the values without needing a temporary variable.

## Sample Execution:

**Input**: 
```
Enter a
10
Enter b
20
```

**Output**: 
```
a 20
b 10
```

---



---

# Factorial Calculator

**Purpose**: This Java program calculates the factorial of a given number.

## Code:

```java
import java.util.*;

class factorial {
    public static void main(String args[]) {
        int n;
        int fact = 1;
        
        System.out.println("Enter number");
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt();
        
        for(int i = 1; i <= n; i++) {
            fact = fact * i;
        }
        
        System.out.println("Factorial: " + fact);
        sc.close();
    }
}
```

## How it Works:

1. The program prompts the user to input a number.
2. The program calculates the factorial of the number using a `for` loop.
3. The calculated factorial is then printed to the console.

## Explanation:

Factorial of a non-negative integer \( n \) is the product of all positive integers less than or equal to \( n \). It is denoted by \( n! \). For example:

- \( 5! = 5 \times 4 \times 3 \times 2 \times 1 = 120 \)

## Sample Execution:

**Input**: 
```
Enter number
5
```

**Output**: 
```
Factorial: 120
```

---
Certainly! Here's a README for your `factorial` program:

---

# Factorial Calculator Using Recursions

The `factorial` program takes a number as input and calculates its factorial.

## Code:

```java
import java.util.*;

class factorial {
    public static void main(String args[]) {
        int n;
        System.out.println("Enter number");
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt();
        sc.close();
        factorial(n);
    }

    public static void factorial(int n) {
        int fact = 1;
        for (int i = 1; i <= n; i++) {
            fact = fact * i;
        }
        System.out.println("Factorial: " + fact);
    }
}
```

## How It Works:

1. **User Input:** The program prompts the user to input an integer number.
2. **Calculation:** The factorial of the number is calculated using a for loop. The factorial of a non-negative integer \( n \) is the product of all positive integers less than or equal to \( n \). It is denoted by \( n! \).
3. **Output:** The computed factorial is then displayed to the user.

## Sample Execution:

**Input**:

```
Enter number
5
```

**Output**:

```
Factorial: 120
```

---

To calculate the factorial, the program multiplies each integer from 1 to the entered number. For instance, the factorial of 5 (denoted as 5!) is `5 x 4 x 3 x 2 x 1 = 120`.
