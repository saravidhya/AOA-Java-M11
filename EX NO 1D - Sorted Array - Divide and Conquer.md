# EX 1D Sorted Array using Divide and Conquer Approach.

## AIM:

To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm

1. Ensure `nums1` is the smaller array to simplify binary search.
2. Apply binary search on `nums1` to choose a partition point.
3. Compute the matching partition in `nums2` so both left halves contain half the total elements.
4. Check if the chosen partition is valid: all left-side values are ≤ corresponding right-side values.
5. When the correct partition is found, compute the median based on total length being odd or even.

#### Developed By: VIDHIYA LAKSHMI S
#### Register Number: 212223230238

## Program:

### to implement divide and conquer - median of two sorted arrays
```java
public class Main {

    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1);
        }

        int m = nums1.length;
        int n = nums2.length;
        int low = 0, high = m;

        while (low <= high) {
            int cut1 = (low + high) / 2;
            int cut2 = (m + n + 1) / 2 - cut1;

            int left1 = (cut1 == 0) ? Integer.MIN_VALUE : nums1[cut1 - 1];
            int left2 = (cut2 == 0) ? Integer.MIN_VALUE : nums2[cut2 - 1];
            int right1 = (cut1 == m) ? Integer.MAX_VALUE : nums1[cut1];
            int right2 = (cut2 == n) ? Integer.MAX_VALUE : nums2[cut2];

            if (left1 <= right2 && left2 <= right1) {
                if ((m + n) % 2 == 0) {
                    return (Math.max(left1, left2) + Math.min(right1, right2)) / 2.0;
                } else {
                    return Math.max(left1, left2);
                }
            } else if (left1 > right2) {
                high = cut1 - 1;
            } else {
                low = cut1 + 1;
            }
        }

        return 0.0;
    }

    public static void main(String[] args) {
        int[] nums1 = {1, 3};
        int[] nums2 = {2};

        System.out.println("Median = " + findMedianSortedArrays(nums1, nums2));
    }
}
```

## Output:

```
Median = 2.0
```

## Result:

The program successfully implemented and the expected output is verified.
