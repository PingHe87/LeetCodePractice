# 242. Valid Anagram

Date: 29/07/2024
Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

> Example 1:
> Input: s = "anagram", t = "nagaram"
> Output: true

> Example 2:
> Input: s = "rat", t = "car"
> Output: false

## IDEAS

- Compare the length first
- Uppercase or Lowercase letters -- lowercase in this problem
- Create 2 hashmaps, like S and T
  - in S : a-3, n-1, g-1, r-1, m-1
  - in T : a-3, n-1, g-1, r-1, m-1
- Compare them

## Solution

### Use HashMap

```java
// O(T) = O(m+n)
// O(S) = O(1)
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        HashMap<Character, Integer> charCountMap = new HashMap<>();

        for (char c : s.toCharArray()){
            charCountMap.put(c, charCountMap.getOrDefault(c,0) + 1);
        }
        for (char c : t.toCharArray()){
            if(!charCountMap.containsKey(c)){
                return false;
            }
            charCountMap.put(c, charCountMap.get(c)-1);
            if(charCountMap.get(c) == 0){
                charCountMap.remove(c);
            }
        }
        return charCountMap.isEmpty();
    }
}
```

### Use Array

```java
import java.util.Arrays;

class Solution {
    public boolean isAnagram(String s, String t) {
        char[] sChars = s.toCharArray();
        char[] tChars = t.toCharArray();

        Arrays.sort(sChars);
        Arrays.sort(tChars);

        return Arrays.equals(sChars, tChars);
    }
}
```

## Addition

The most frequently used Java syntax and operations for `HashMap`:

### 1. Importing `HashMap`

```java
import java.util.HashMap;
```

### 2. Creating a `HashMap`

```java
HashMap<Integer, String> map = new HashMap<>();
```

### 3. Adding Elements to a `HashMap`

```java
map.put(1, "One");
map.put(2, "Two");
map.put(3, "Three");
```

### 4. Accessing Elements from a `HashMap`

```java
String value = map.get(1); // Returns "One"
```

### 5. Checking if a Key Exists

```java
boolean exists = map.containsKey(2); // Returns true
```

### 6. Checking if a Value Exists

```java
boolean containsValue = map.containsValue("Three"); // Returns true
```

### 7. Removing an Element

```java
map.remove(2); // Removes the entry with key 2
```

### 8. Iterating Over a `HashMap`

#### Using Entry Set

```java
for (Map.Entry<Integer, String> entry : map.entrySet()) {
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
```

#### Using Key Set

```java
for (Integer key : map.keySet()) {
    System.out.println("Key: " + key + ", Value: " + map.get(key));
}
```

### 9. Getting the Size of the `HashMap`

```java
int size = map.size(); // Returns the number of key-value pairs
```

### 10. Clearing the `HashMap`

```java
map.clear(); // Removes all entries from the map
```

### 11. Checking if the `HashMap` is Empty

```java
boolean isEmpty = map.isEmpty(); // Returns true if the map is empty
```

### 12. Replacing a Value for a Given Key

```java
map.replace(1, "Uno"); // Replaces the value for key 1 with "Uno"
```

### 13. Putting a Value if Key is Absent

```java
map.putIfAbsent(4, "Four"); // Puts the value "Four" for key 4 if it is not already present
```

### 14. Merging Entries

```java
map.merge(1, "New", (oldValue, newValue) -> oldValue + newValue); // Merges "New" with the existing value of key 1
```

### 15. Compute a Value for a Given Key

```java
map.compute(1, (key, val) -> val + " Updated"); // Updates the value of key 1 by appending " Updated"
```
