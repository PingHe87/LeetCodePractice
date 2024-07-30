# 202. Happy Number

Date: 30/07/2024
Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

Starting with any **positive integer**, replace the number by the sum of the squares of its digits.
Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
Those numbers for which this process ends in 1 are happy.
Return true if n is a happy number, and false if not.

> Input: n = 19
> Output: true
> Explanation:
> 1^2 + 9^2 = 82
> 8^2 + 2^2 = 68
> 6^2 + 8^2 = 100
> 1^2 + 0^2 + 0^2 = 1

## IDEAS

- try 2:
  2, 4, 16, 37, 58, 89, 145, 42, 20, 4(cycle)

1. 2 main solutions in this problem：
   1.1 isHappy(int n) - check isHappy
   1.2 getNextNumber(int n) - calculate the square of the number by digits
   ```java
   while (n > 0) {
            digits[index--] = n % 10; // get the last digit
            n = n / 10; // delete the last digit
        }
   ```

## Solution

```java
class Solution{
    public boolean isHappy(int n){
        //n = 19
        Set<Integer> record = new HashSet<>();
        // record = {}
        while( n != 1 &&
        // trigger the n = 1
               !record.contains(n)){
                record.add(n);
                // record{19}
                // record{19, 82}
                // record{19, 82, 68, 100}
                n = getNextNumber(n);
                // getNextNumber(19)
                // getNextNumber(82)
                // getNextNumber(68)
                // getNextNumber(100)
            }
            return n == 1;
            // out put n == 1?
    }
    private int getNextNumber(int n){
        int res = 0;
        // res = 0
        while(n > 0){
            int temp = n % 10;
            // temp = 19 % 10 = 9
            // temp = 1 % 10 = 1
            res += temp * temp;
            //res = 0 + 9 * 9 = 81
            //res = 81 + 1 * 1 = 82
            n = n / 10;
            // n = 19 / 10 = 1 > 0
            // n = 1 / 10 = 0
        }
        return res;
        //return 82
        // when n = 100, res = 1, n = 1
    }
}
```
