## 28. Implement strStr()

#### Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

#### Example
```
Input: haystack = "hello", needle = "ll"
Output: 2

Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

#
## Solution
```
class Solution {
    public int strStr(String haystack, String needle) {
        if(needle.length() > haystack.length()) return -1;
        for(int i = 0; i <= haystack.length() - needle.length(); i++) {
            if(haystack.substring(i, i + needle.length()).equals(needle)){
                return i;
            }  
        }
        return -1;
    }
}
```

#### Notes

##### Brute Force. KMP considered. 


    