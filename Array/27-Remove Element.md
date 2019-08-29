## 27. Remove Element

#### Given an array nums and a value val, remove all instances of that value in-place and return the new length.

#### Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

#### The order of elements can be changed. It doesn't matter what you leave beyond the new length.

#

## Solution

#### Normal Way
Two Pointers
```
class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;
        for (int j = 0; j < nums.length; j++){
            if(nums[j] != val){
                nums[i] = nums[j];
                i++;
            }
        }
        
        return i;
    }
}
```

#### Rare value Case
Swap the val with the last element of the array.
Decrease the length of the array 
```
class Solution {
    public int removeElement(int[] nums, int val) {
        int i = 0;
        int n = nums.length;

        while(i < n) {
            if(nums[i] == val) {}
                nums[i] = nums[n - 1];
                n--
            }
            else {
                i++
            } 
        }
        return n; 
    }
}
```

