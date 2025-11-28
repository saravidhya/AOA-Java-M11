
# EX 1A Print All Numbers

## AIM:

To Write a Java program that takes an integer input N from the user and prints all the numbers from 1 to N, separated by spaces, on a single line.

## Algorithm

1. Start
2. Input an integer N from the user.
3. Initialize a counter variable i = 1.
4. Repeat while i ≤ N:
5. Print i followed by a space.
6. Increment i by 1.

#### Developed By: Vidhiya Lakshmi S

#### Register Number: 212223230238

## Program:
### to implement printing of numbers
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter an integer N: ");
        int N = scanner.nextInt();

        for (int i = 1; i <= N; i++) {
            System.out.print(i);
            if (i < N) System.out.print(" ");
        }

        scanner.close();
    }
}

```

## Output:

```
N = 5
1 2 3 4 5
```

## Result:

Program executed successfully.
