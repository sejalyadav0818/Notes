
# Reverser Number  :

# Code :  
```import java.util.*;

class HelloWorld {
    public static void main(String[] args) {
        int n , r;
        System.out.print("Enter numberr");
        Scanner s = new Scanner(System.in);
        n = s.nextInt();
        while(n>0)
        {
            r = n%10;
            System.out.print(r);
            n= n/10;
            
        }
    }
}
```
## Output : 
Enter numberr : 789
987
