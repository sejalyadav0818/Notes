
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

