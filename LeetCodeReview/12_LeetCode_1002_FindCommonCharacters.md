# 1002. Find Common Characters

Date: 29/07/2024
Given a string array words, return an array of all characters that show up in all strings within the words (including duplicates). You may return the answer in any order.

> Example 1:
> Input: words = ["bella","label","roller"]
> Output: ["e","l","l"]

- BE CAREFUL **l** COUNTS TWICE.

> Example 2:
> Input: words = ["cool","lock","cook"]
> Output: ["c","o"]

## IDEAS

- Creating a new HashMap(Char, Integer) named map
- for(Char t in String s), if map.containsKey(t), increase the value by 1
  if value > 1, output the key

## Solution

```java
class Solution{
    public List<String> commonChars(String[] words) {
            // Initialize the array to store the minimum frequency of each character
            int[] minFreq = new int[26];
            for( int i = 0; i < 26; i++){
                minFreq[i] = Integer.MAX_VALUE;
            }
            // Iterate over each word
            for(String word : words){
                int[] charCount = new int[26];
                for(char c : word.toCharArray()){
                    // Caculate the position of c in Alphabet Order, like c =c = 99, a = 97, so answer is 2
                    charCount[c - 'a']++;
                }
                // Update the minimum frequency array
                for(int i = 0; i < 26; i++){
                    minFreq[i] = Math.min(minFreq[i], charCount[i]);
                }
            }
            List<String> result = new ArrayList<>();
            for(int i = 0; i < 26; i++){
                while(minFreq[i] > 0){
                    result.add(String.valueOf((char)(i+'a')));
                    minFreq[i]--;
                }
            }
            return result;
        }
}
```
