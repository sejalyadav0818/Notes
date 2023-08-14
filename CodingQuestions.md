
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

A is greater
```

---

