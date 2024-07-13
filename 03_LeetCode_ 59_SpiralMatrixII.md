# 59. Spiral Matrix II

Date: 12/07/2024

## Description

Given a positive integer n, generate an n x n matrix filled with elements from 1 to n^2 in spiral order.

> Input: n = 3
> Output: [ [1,2,3],[8,9,4],[7,6,5] ]

## Solution

### Clarification

- positive integer n -> n\*n matrix
  we need a int[ ][ ] (2D array) to store the result.

### Assumption

Try n = 4
the 2D arr would be:

```java

L   --->    R
1   2   3   4  T
12  13  14  5
11  16  15  6
10  9   8   7  B
L   <---    R

//test n = 2 and to see when to stop the loop
1 2
4 3
```

### Reasoning

look at the example.

1. create a new 2D array to store the result.
   - L = T = 0; R = B = n-1 = 3.
2. store the value from L to R, T to B, R to L, B to T.
   2.1 the row 0: from [0][0] to [0][3] (L <= R), val ++, T++; -> T starts from 1 now.
   2.2 the column 3: from[1][3] to [3][3] (T <= B), val ++; R--; -> R starts from 2 now.
   2.3 the row 3: **REVERSE:** from[2][3] to [0][3](R >= L), val++; B--; -> B starts from 3 now.
   2.4 the column 0: **REVERSE:** from [2][0] to[1][0](B >= T), val++; L++; -> L starts from 2 now.
3. Be careful with the order in R to L and B to T.

### Code

```java
    class Solution {
        public int[][] generateMatrix(int n) {
            //Initialize
            int[][] arr = new int[n][n];
            int left = 0,
                right = n-1,
                top = 0,
                bottom = n-1,
                val = 1;
            while(left <= right && top <= bottom){
                // row top
                for(int i = left; i<= right; i++){
                    arr[top][i] = val++;
                }
                top ++;
                // column right
                for(int i = top; i <= bottom; i++){
                    arr[i][right] = val++;
                }
                right--;
                // row bottom
                if(right >= left){
                    for(int i = right; i >= left; i--){
                        arr[bottom][i] = val++;
                    }
                    bottom--;
                }
                // column left
                if(bottom >= top){
                    for(int i = bottom; i >= top; i--){
                        arr[i][left] = val++;
                    }
                    left++;
                }
            }
            return arr;
        }
    }
```
