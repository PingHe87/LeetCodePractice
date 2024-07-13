# 74. Search A 2D Matrix

Date: 13/07/2024
You are given an m x n integer matrix matrix with the following two properties:

**Each row is sorted in non-decreasing order.**  
**The first integer of each row is greater than the last integer of the previous row.**
Given an integer target, return true if target is in matrix or false otherwise.

You must write a solution in O(log(m \* n)) time complexity.

> Input: matrix = [ [1,3,5,7],[10,11,16,20],[23,30,34,60] ], target = 3  
> Output: true

## Clarification

In this problem, the matrix is increasing when we go through the matix from left to right, top to bottom.

```java
    [
        [1, 3, 5],
        [7, 10, 12],
        [14, 16, 18]
    ]
    // can be converted to
    [1, 3, 5, 7, 10, 12, 14, 16, 18]
    //then we can use the binary search

    //Try a easy example
    [//A 3m*4n matrix with 3*4 = 12 elements
    //the index 0-11 (m*n-1)
        [2,  8,  9,  10],
        [12, 13, 15, 20],
        [21, 31, 41, 51]
    ]
    //target = 41
    //left = 0, right = m*n-1 = 11
    [2,  8,  9,  10, 12, 13, 15, 20, 21, 31, 41, 51]
    //index ^
    [0,  1,  2,  3,  4,  5,  6,  7,  8,  9,  10, 11]
    //mid = l+(r-l)/2 = 5.5 = 5
    //val[5] = 13, in matrix[1][1]
    //5/4 = 1...1 -> matrix[mid/n][mid%n]
    //13<target,so move the left to mid, left = mid + 1
```

## Addtional

In Java, the division operator / performs integer division when both operands are integers. This means that any fractional part of the result is discarded, and only the integer part is kept.  
example : 11/2 = 5

## Solution

```java
    class Solution {
        public boolean searchMatrix(int[][] matrix, int target) {
            if (matrix == null ||
                matrix.length == 0 || //not lenth() the height
                matrix[0].length ==0 // the width
                ){
                    return false;
                }
            int m = matrix.length,
                n = matrix[0].length,
                left = 0,
                right = m * n - 1;
            while (left<= right){ //include =
                int mid = left + (right - left) / 2; //the standard way
                int midValue = matrix[mid / n][mid % n];
                if(midValue == target){
                    return true;
                }else if(midValue < target){
                    left = mid + 1;
                }else{
                    right = mid - 1;
                }
            }
            return false;
        }
    }
```

## Wrong

```java
return true; //not True
```
