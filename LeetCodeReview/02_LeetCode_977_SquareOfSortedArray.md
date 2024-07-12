Date: 11/07/2024

# 977. Squares of a Sorted Array

Given an **integer array nums sorted in non-decreasing order**, return an array of the squares of each number sorted in non-decreasing order.

## Important Points:

1.  integer array nums sorted in non-decreasing order: The number could be negative.

> Example 1:
> Input: nums = [-4,-1,0,3,10]
> Output: [0,1,9,16,100]
> Explanation: After squaring, the array becomes [16,1,0,9,100].
> After sorting, it becomes [0,1,9,16,100].

> Example 2:
> Input: nums = [-7,-3,2,3,11]
> Output: [4,9,9,49,121]

---

## Solution

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int[] arr = new int[nums.length];
        int left = 0, right = nums.length - 1;
        int rightA = nums.length - 1;  // Declare the type of rightA

        while (left <= right) {
            if (Math.abs(nums[left]) < Math.abs(nums[right])) {
                arr[rightA] = (int) Math.pow(nums[right], 2);
                right--;
            } else {
                arr[rightA] = (int) Math.pow(nums[left], 2);
                left++;
            }
            rightA--;  // Decrement rightA once per loop iteration
        }

        return arr;
    }
}

```

## Important Points

1. Initialize a new arr int[] to store the result.
2. Math. Functions:

   ```java
    public class MathExamples {
    public static void main(String[] args) {
        // Basic Arithmetic Methods
        System.out.println("The absolute value of -5.3 is " + Math.abs(-5.3));
        System.out.println("The maximum of 5 and 10 is " + Math.max(5, 10));
        System.out.println("The minimum of 5 and 10 is " + Math.min(5, 10));
        System.out.println("2 raised to the power of 3 is " + Math.pow(2, 3));
        System.out.println("The square root of 16 is " + Math.sqrt(16));

        // Trigonometric Methods
        System.out.println("The sine of π/2 is " + Math.sin(Math.PI / 2));
        System.out.println("The cosine of 0 is " + Math.cos(0));
        System.out.println("The tangent of π/4 is " + Math.tan(Math.PI / 4));

        // Exponential and Logarithmic Methods
        System.out.println("e raised to the power of 1 is " + Math.exp(1));
        System.out.println("The natural logarithm of e is " + Math.log(Math.E));
        System.out.println("The base 10 logarithm of 100 is " + Math.log10(100));

        // Rounding Methods
        System.out.println("The ceiling of 2.3 is " + Math.ceil(2.3));//3
        System.out.println("The floor of 2.7 is " + Math.floor(2.7));//2
        System.out.println("2.5 rounded is " + Math.round(2.5));//3

        // Random Number Generation
        System.out.println("A random number between 0.0 and 1.0 is " + Math.random());

        // Hyperbolic Methods
        System.out.println("The hyperbolic sine of 1 is " + Math.sinh(1));
        System.out.println("The hyperbolic cosine of 1 is " + Math.cosh(1));
        System.out.println("The hyperbolic tangent of 1 is " + Math.tanh(1));
    }
   }
   ```

3. arr[rightA] = **(int)** Math.pow(nums[right], 2);: Don't forget to define the object of the new arr.
