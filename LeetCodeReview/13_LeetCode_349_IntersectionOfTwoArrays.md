# 349. Intersection of Two Arrays

Date: 29/07/2024
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

> Example 1:
> Input: nums1 = [1,2,2,1], nums2 = [2,2]
> Output: [2]

> Example 2:
> Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
> Output: [9,4]
> Explanation: [4,9] is also accepted.

## Solution

```java
import java.util.*;

class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        // 修正 num1 为 nums1
        if (nums1.length == 0 || nums2.length == 0) {
            return new int[0];
        }

        // 使用 Set 存储第一个数组的元素
        Set<Integer> set = new HashSet<>();
        for (int num : nums1) {
            set.add(num);
        }

        // 使用另一个 Set 存储交集的元素
        Set<Integer> intersectionSet = new HashSet<>();
        for (int num : nums2) {
            if (set.contains(num)) {
                intersectionSet.add(num);
            }
        }

        // 将 Set 转换为数组
        int[] result = new int[intersectionSet.size()];
        int index = 0;
        for (int num : intersectionSet) {
            result[index++] = num;
        }
        return result;
    }
}

```
