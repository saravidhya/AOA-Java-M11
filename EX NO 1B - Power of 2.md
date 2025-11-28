# EX 1B Power of 2

## AIM:

To write a Java program to for given constraints.Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

## Algorithm

1. Take the integer `n` as input.
2. If `n` is less than or equal to zero, it cannot be a power of two — return false.
3. While `n` is divisible by 2, divide it by 2.
4. After the loop, check whether the remaining value is 1.
5. If it is 1, return true; otherwise, return false.

#### Developed By: Vidhiya Lakshmi S

#### Register Number: 212223230238

## Program:

### to implement power of 2
```java
public class Main {

    public static boolean isPowerOfTwo(int n) {
        if (n <= 0) return false;

        while (n % 2 == 0) {
            n /= 2;
        }

        return n == 1;
    }

    public static void main(String[] args) {
        int n = 64; // example
        System.out.println(n + " is power of two? " + isPowerOfTwo(n));
    }
}
```

## Output:

```
64 is power of two? true
```

## Result:

The program successfully implemented and the expected output is verified.
