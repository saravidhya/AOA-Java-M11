# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).

## AIM:

To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.

## Algorithm

1. If the matrix size is 1×1, multiply the single elements and return.
2. Split matrices **A** and **B** into four submatrices each (quadrants).
3. Compute the seven Strassen products (P1 to P7) using recursive calls.
4. Use these seven products to construct the four resulting quadrants of the output matrix.
5. Combine these four quadrants into the final result and return the matrix.

#### Developed By: VIDHIYA LAKSHMI S

#### Register Number: 212223230238

## Program:

### to implement strassens algorithm

```java
public class Main {

    public static int[][] strassen(int[][] A, int[][] B) {
        int n = A.length;

        // Base case
        if (n == 1) {
            return new int[][]{{A[0][0] * B[0][0]}};
        }

        int newSize = n / 2;
        int[][] a11 = new int[newSize][newSize];
        int[][] a12 = new int[newSize][newSize];
        int[][] a21 = new int[newSize][newSize];
        int[][] a22 = new int[newSize][newSize];

        int[][] b11 = new int[newSize][newSize];
        int[][] b12 = new int[newSize][newSize];
        int[][] b21 = new int[newSize][newSize];
        int[][] b22 = new int[newSize][newSize];

        // Splitting matrices
        split(A, a11, 0, 0);
        split(A, a12, 0, newSize);
        split(A, a21, newSize, 0);
        split(A, a22, newSize, newSize);

        split(B, b11, 0, 0);
        split(B, b12, 0, newSize);
        split(B, b21, newSize, 0);
        split(B, b22, newSize, newSize);

        // Strassen's 7 products
        int[][] P1 = strassen(add(a11, a22), add(b11, b22));
        int[][] P2 = strassen(add(a21, a22), b11);
        int[][] P3 = strassen(a11, subtract(b12, b22));
        int[][] P4 = strassen(a22, subtract(b21, b11));
        int[][] P5 = strassen(add(a11, a12), b22);
        int[][] P6 = strassen(subtract(a21, a11), add(b11, b12));
        int[][] P7 = strassen(subtract(a12, a22), add(b21, b22));

        // C quadrants
        int[][] c11 = add(subtract(add(P1, P4), P5), P7);
        int[][] c12 = add(P3, P5);
        int[][] c21 = add(P2, P4);
        int[][] c22 = add(subtract(add(P1, P3), P2), P6);

        // Combine quadrants
        int[][] C = new int[n][n];
        join(c11, C, 0, 0);
        join(c12, C, 0, newSize);
        join(c21, C, newSize, 0);
        join(c22, C, newSize, newSize);

        return C;
    }

    // Helper operations
    private static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

    private static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

    private static void split(int[][] P, int[][] C, int row, int col) {
        for (int i = 0; i < C.length; i++)
            for (int j = 0; j < C.length; j++)
                C[i][j] = P[i + row][j + col];
    }

    private static void join(int[][] C, int[][] P, int row, int col) {
        for (int i = 0; i < C.length; i++)
            for (int j = 0; j < C.length; j++)
                P[i + row][j + col] = C[i][j];
    }

    public static void main(String[] args) {
        int[][] A = {
            {1, 2},
            {3, 4}
        };

        int[][] B = {
            {5, 6},
            {7, 8}
        };

        int[][] C = strassen(A, B);

        System.out.println("Result:");
        for (int[] row : C) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

## Output:

```
Result:
19 22
43 50
```

## Result:

The program successfully implemented and the expected output is verified.
