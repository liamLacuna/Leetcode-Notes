## 81.Search in Rotated Sorted Array II

#### Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

#### (i.e., [0,0,1,2,2,5,6] might become [2,5,6,0,0,1,2]).

#### You are given a target value to search. If found in the array return true, otherwise return false.

```
Example: 

Input: nums = [2,5,6,0,0,1,2], target = 0
Output: true
```

#

## Solution

```
class Solution {
    public boolean search(int[] nums, int target) {
        int l = 0, h = nums.length-1;
        while(l <= h){
            int mid = l + (h-l)/2;
            if(nums[mid] == target)     return true;
            if(nums[mid] == nums[h])    h--;
            else if(nums[mid] < nums[h]){
                if(target > nums[mid] && target <= nums[h])
                    l = mid + 1;
                else
                    h = mid - 1;
            }else{
                if(target >= nums[l] && target < nums[mid])
                    h = mid - 1;
                else
                    l = mid + 1;
            }
        }
        return false;
    }
}
```

## Notes:

#### Similar to 33, but we only need to know if it exits, so use binary search with determine the target is in larger than mid or less than can find the target value. 