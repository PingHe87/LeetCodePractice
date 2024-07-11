Date: 11/07/2024

# LeetCode 209 Sliding Window

---

## Description

### 209. Minimum Size Subarray Sum

Given an array of **positive integers** nums and a positive integer target, return the **minimal length** of a subarray whose sum is **greater than or equal to** target. If there is **no such** subarray, return 0 instead.

#### Important Points:

1. Positive integers: The sum of the subarray will always be increased as we add a new number.
2. Minimal length: The initial value for the minimal length should be set to a very large number.
3. Greater than or equal to: The condition should be checked using >=, not just ==.
4. No such array: The code must handle cases where the array is too short or the sum of all elements is less than the target.

> Example 1:
> Input: target = 7, nums = [2,3,1,2,4,3]
> Output: 2
> Explanation: The subarray [4,3] has the minimal length under the problem constraint.

> Example 2:
> Input: target = 4, nums = [1,4,4]
> Output: 1

> Example 3:
> Input: target = 11, nums = [1,1,1,1,1,1,1,1]
> Output: 0

---

## Solution

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int ans = Integer.MAX_VALUE;
        int sum = 0;
        int left = 0;
        for(int right = 0; right < nums.length; right++){
            sum += nums[right];
            while (sum >= target){
                ans = Math.min(ans, right-left+1);
                sum -= nums[left];
                left++;
                }
            }
        return ans == Integer.MAX_VALUE ? 0 : ans;
        }
    }
```

### Important Points:

1. **I**nteger.**MAX_VALUE**--The capital charactor
   **Extension**:
   Integer.MIN_VALUE:(-2^31).
   Integer.MAX_VALUE:(2^31 - 1).
   Byte.MIN_VALUE: (-128).
   Byte.MAX_VALUE: (127).
2. nums.**length**:
   **Extension**:

   - For String : int length = str.**length();** the space character " " is counted in the length of a string.

   ```java
    public class StringLengthExample {
        public static void main(String[] args) {
            String str1 = "Hello, World!";
            String str2 = " ";

            System.out.println("Length of str1: " + str1.length());  // Returns 13
            System.out.println("Length of str2: " + str2.length());  // Returns 1
        }
    }

   ```

   - For Array([]): int length = arr.length;

   ```java
    int[] intArray = {1, 2, 3, 4, 5};
    int length = intArray.length;  // Returns 5

    char[] charArray = {'a', 'b', 'c'};
    int length = charArray.length;  // Returns 3

    String[] strArray = {"one", "two", "three"};
    int length = strArray.length;  // Returns 3

   ```

   - For ArrayList:

   ```java
   List<String> list = new ArrayList<>();
    list.add("one");
    list.add("two");
    list.add("three");
    int size = list.size();  // Returns 3
   ```

   - For Map:

   ```java
    Map<String, Integer> map = new HashMap<>();
    map.put("one", 1);
    map.put("two", 2);
    map.put("three", 3);
    int size = map.size();  // Returns 3
   ```

3. **If or While** statement:
   - The if statement is used to execute a block of code **only once** if a specified condition is true.
   - Use while: When you need to **repeatedly execute a block of code** as long as a condition remains true.
