## 33. Search in Rotated Sorted Array

#### Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

#### (i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).

#### You are given a target value to search. If found in the array return its index, otherwise return -1.

#### You may assume no duplicate exists in the array.

#### Your algorithm's runtime complexity must be in the order of O(log n).

```
Example 1:
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4

Example 2:
Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```

# 

## Solution

```
class Solution {
    public int search(int[] nums, int target) {
        if(nums.length == 0) return -1;
        if(nums.length == 1) return nums[0]  == target ? 0 : -1;
        
        //Find the pivot index first;
        int left = 0;
        int right = nums.length - 1;
        int rotate_index = find_rotate_index(nums, left, right);
        
        if(nums[rotate_index] == target) return rotate_index;
        if(rotate_index == 0) return search(target, left, right, nums);
        if(target < nums[0]) return search(target, rotate_index, right, nums);
        return search(target, left, rotate_index, nums);
    }
    
    public int search(int target, int left, int right, int nums[]) {
        /* Binary search */
        while (left <= right) {
            int mid = (left + right) / 2;
            if(nums[mid] == target) return mid;
            else if (nums[mid] > target) right = mid - 1;
            else left = mid + 1;
        }
        
        return -1;
    }
    
    public int find_rotate_index(int[]nums, int left, int right) {
        if(nums[left] < nums[right]) 
            return 0;
        
        while (left <= right) {
            int mid = (left + right) / 2;
            if(nums[mid] > nums[mid + 1]) 
                return mid + 1;
            else {
                if(nums[mid] < nums[left]) right = mid - 1;
                else left = mid + 1;
            }
        }
        
        return 0;
    }
}
```

#### Notes

##### Use a Binary Search to find the rotate pivot first, then search the target number based on the pivot point and target value. 




