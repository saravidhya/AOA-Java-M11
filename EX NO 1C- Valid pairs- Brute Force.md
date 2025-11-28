# EX 1C Valid Pairs using Brute Force Approach

## AIM:

To write a Java program to for given constraints.
Given an integer array nums and an integer k, return the number of pairs (i, j) where i < j such that |nums[i] - nums[j]| == k.

The value of |x| is defined as:

x if x >= 0.
-x if x < 0.

## Algorithm

1. Read the array `nums` and the integer `k`.
2. Initialize a counter to zero.
3. Use two loops: the outer loop for index `i`, the inner for index `j > i`.
4. For each pair, compute the absolute difference `|nums[i] - nums[j]|`.
5. If the difference equals `k`, increment the counter and finally return it.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement brute force - valid pairs

```java
public class Main {

    public static int countPairs(int[] nums, int k) {
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (Math.abs(nums[i] - nums[j]) == k) {
                    count++;
                }
            }
        }
        return count;
    }

    public static void main(String[] args) {
        int[] nums = {1, 5, 3, 4, 2};
        int k = 2;

        System.out.println("Number of valid pairs: " + countPairs(nums, k));
    }
}
```

## Output:

```
Number of valid pairs: 3
```

## Result:

The program successfully implemented and the expected output is verified.
