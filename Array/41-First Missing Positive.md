## 41.First Missing Positive

#### Given an unsorted integer array, find the smallest missing positive integer.

#
## Solution

```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        
        //Base case : missing number is 1
        int contains = 0;
        for(int i = 0; i < n; i++) {
            if(nums[i] == 1) {
                contains++;
                break;
            }
        }
        
        if (contains == 0)
            return 1;
        
        //Second base case: missing number is 2
        if(n == 1)
            return 2;
        
        // Replace negative numbers and zeros to 1
        // After this convertion, nums will contain only positive numbers
        for(int i = 0; i < n; i++) {
            if((nums[i] <= 0) || (nums[i] > n)) 
                nums[i] = 1;
        }
        
        // Change the sign of ath element when meeting number a. 
        for(int i = 0; i < n; i++){
            int a = Math.abs(nums[i]);
            
            if(a == n) 
                nums[0] = - Math.abs(nums[0]);
            else 
                nums[a] = - Math.abs(nums[a]);
        }
        
        for(int i = 1; i < n; i++){
            if(nums[i] > 0) 
                return i;
        }
        
        if(nums[0] > 0) 
            return n;
        
        return n + 1;
    }
}
```

#### Notes
##### Find the base case, then change every negative and zero to 1, then using the opposite sign and index to find the missin one