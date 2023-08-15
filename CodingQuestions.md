
---

# Table of Contents:
- [Prime Number form 1 to 100](#prime-number)
- [Number Reverser](#number-reverser)
- [Prime Number Checker](#prime-number-checker)
- [Number Palindrome Checker](#number-palindrome-checker)
- [Greatest Among Three Numbers](#greatest-among-three-numbers)
- [Odd or Even Number Checker](#odd-or-even-number-checker)
- [Leap Year Checker](#leap-year-checker)
- [Swap Two Numbers Without Using a Third Variable](#swap-two-numbers-without-using-a-third-variable)
- [Factorial Calculator](#factorial-calculator)
- [Factorial Calculator Using Recursions](#factorial-calculator-using-recursions)
- [Fibonacci Series Generator](#fibonacci-series-generator)

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

---

# Prime Number 

**Purpose**: This Java program prints all prime numbers from 2 up to 200.

## Code:

```java
class HelloWorld {

    public static void main(String[] args) {
        
        for(int num=2; num<=200; num++) {
            if(isPrime(num)) {
                System.out.println("" + num);
            }
        }

    }
    
    public static boolean isPrime(int n) {
        if(n <= 1) {
            return false;
        }
        for(int i=2; i <= Math.sqrt(n); i++) {
            if(n % i == 0) {
                return false;
            }
        }
        return true;
    }
}
```

## Explanation:

1. **Main Method**: Iterates through numbers from 2 to 200 and calls the `isPrime` method for each number. If the `isPrime` method returns `true`, the number is printed.

2. **isPrime Method**: This method determines whether a given number `n` is prime.
   - If `n` is less than or equal to 1, it immediately returns `false`.
   - It then checks if `n` has any divisors other than 1 and itself. This is done by trying to divide it by every number up to its square root. 
   - Using the square root as the upper limit improves efficiency. If `n` has a factor greater than its square root, then it definitely has a smaller factor that we've already checked.
   - If `n` is divisible by any number in the loop (remainder is zero), the method returns `false`. If the loop completes without finding any divisors, the method returns `true`.

## Sample Output:

This program will print all prime numbers from 2 to 200, with each number printed on a new line:

```
2
3
5
...
197
199
```

---
---

# Fibonacci Series Generator

**Purpose**: This program generates the first `n` numbers in the Fibonacci series. In this implementation, the first ten numbers of the Fibonacci series are printed.

## Code:

```java
class Fibonacci {
    public static void main(String[] args) {
        int a = 0, b = 1, c;
        System.out.println(a + " " + b);
        
        for(int i = 1; i <= 10; i++) {
            c = a + b;
            System.out.println(c);
            a = b;
            b = c;
        }
    }
}
```

## Explanation:

- **Initialization**: The first two numbers in the Fibonacci series, `a` (0) and `b` (1), are initialized.
- **Loop**: A loop runs 10 times, and in each iteration:
  1. A new number, `c`, is calculated as the sum of the last two numbers (`a+b`).
  2. The number `c` is printed.
  3. Values of `a` and `b` are updated for the next iteration.
  
## Output:

The program will generate the following output:

```
0 1
1
2
3
5
8
13
21
34
55
89
```

---
---

# Java Patterns README

## 1. Print 4 Asterisks Vertically

This program simply prints an asterisk (`*`) four times, each on a new line.

```java
class HelloWorld {
    public static void main(String[] args) {
        for(int i=0; i<=4; i++) {
            System.out.println("*");
        }
    }
}
```

Output:
```
*
*
*
*
*
```

## 2. Print 4x4 Asterisks Square

This program prints a 4x4 square of asterisks. It uses a nested loop to achieve this. The outer loop controls the rows, and the inner loop controls the columns.

```java
class HelloWorld {
    public static void main(String[] args) {
        for(int i=1; i<=4; i++) {
            for(int j=1; j<=4; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

Output:
```
****
****
****
****
```

## 3. Hollow Rectangle

This program prints a rectangle with a border of asterisks. The middle part of the rectangle is hollow (it's filled with spaces). It uses conditionals inside the loops to decide when to print an asterisk or a space.

```java
class HelloWorld {
    public static void main(String[] args) {
        for(int i=1; i<=4; i++) {
            for(int j=1; j<=4; j++) {
                if(i == 1 || i == 4 || j == 1 || j == 4) {
                    System.out.print("*");
                } else {
                    System.out.print(" ");
                }
            }
            System.out.println();
        }
    }
}
```
![image](https://github.com/sejalyadav0818/Notes/assets/130818890/0e018ab2-62bc-4e8d-89db-a24677966e2b)

Output:
```
****
*  *
*  *
****
```

## 4. Number Pattern

This program prints a pattern of numbers. The pattern consists of numbers that are decremented with each iteration of the inner loop, starting from 4.

```java
public class Main {
    public static void main(String args[]) {
        for(int i=1; i<=4; i++) {
            for(int j=4; j>=i; j--) {
                System.out.print(j);
            }
            System.out.println();   
        }
    }
}
```

Output:
```
4321
432
43
4
```

---

---

## Patterns

### Pattern 1

**Description:**  
Prints 4 asterisks in a row.

**Java Code:**
```java
public static void pattern1() {
    System.out.println("****");
}
```

**Example Output:**
```
****
```

### Pattern 2

**Description:**  
Prints a single asterisk in 4 consecutive lines.

**Java Code:**
```java
public static void pattern2() {
    for (int i = 0; i < 4; i++) {
        System.out.println("*");
    }
}
```

**Example Output:**
```
*
*
*
*
```

### Pattern 3

**Description:**  
Repeats the pattern from Pattern 1 in 4 consecutive lines.

**Java Code:**
```java
public static void pattern3() {
    for (int i = 0; i < 4; i++) {
        System.out.println("****");
    }
}
```

**Example Output:**
```
****
****
****
****
```

### Pattern 4

**Description:**  
Prints a 5x5 square of asterisks where the internal asterisks are replaced by spaces except for the border.

**Java Code:**
```java
public static void pattern4() {
    System.out.println("*****");
    for (int i = 0; i < 3; i++) {
        System.out.println("*   *");
    }
    System.out.println("*****");
}
```

**Example Output:**
```
*****
*   *
*   *
*   *
*****
```
---

### Pattern 5

**Description:**  
Prints a right-angled triangle using asterisks, where the number of asterisks increases for each line from 1 to 5.

**Code:**
```java
public static void pattern5() {
    for(int i=1; i<=5; i++) {
        for(int j=1; j<=i; j++) {
            System.out.print("*");
        }
        System.out.println();
    }
}
```

**Output:**
```
*
**
***
****
*****
```

---

### Pattern 6

**Description:**  
Prints a pattern of asterisks in descending order from 5 to 1.

**Code:**
```java
public static void pattern6() {
    for(int y=5; y>=1; y--) {
        for(int o=y; o>=1; o--) {
            System.out.print("*");
        }
        System.out.println();
    }
}
```

**Output:**
```
*****
****
***
**
*
```

---

### Pattern 7

**Description:**  
Prints a right-angled triangle of asterisks. However, this time there are spaces before the asterisks, giving the triangle an inverted appearance.

**Code:**
```java
public static void pattern7() {
    int n=4;
    for(int i=1; i<=n; i++) {
        for(int k=1; k<=n-i; k++) {
            System.out.print(" ");
        }
        for(int k=1; k<=i; k++) {
            System.out.print("*");
        }
        System.out.println();
    }
}
```

**Output:**
```
   *
  **
 ***
****
```

---

### Pattern 8

**Description:**  
Prints numbers in a format that resembles a right-angled triangle. The numbers on each line start from 1 and go up to the line number.

**Code:**
```java
public static void pattern8() {
    for(int i=1; i<=4; i++) {
        for(int j=1; j<=i; j++) {
            System.out.print(j);
        }
        System.out.println();
    }
}
```

**Output:**
```
1
12
123
1234
```

---
    // Pattern 10:
    // 12345
    // 1234
    // 123
    // 12
    // 1
    public static void pattern10() {
        for (int i = 5; i >= 1; i--) {
            for (int j = 1; j <= i; j++) {
                System.out.print(j);
            }
            System.out.println();
        }
        System.out.println();
    }

    // Pattern 11:
    // 1
    // 0 1
    // 1 0 1
    // 0 1 0 1 
    // 0 1 0 1 0
    public static void pattern11() {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print((i + j) % 2 + " ");
            }
            System.out.println();
        }
        System.out.println();
    }
}
