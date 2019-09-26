## 35. Search Insert Position

#### Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

#### You may assume no duplicates in the array.

#### Example
```
Input: [1,3,5,6], 5
Output: 2

Input: [1,3,5,6], 2
Output: 1

Input: [1,3,5,6], 0
Output: 0
```

#

## Solution

```
class Solution {
    public int searchInsert(int[] nums, int target) {
        int lo = 0;
        int hi = nums.length - 1;
        
        while (lo <= hi) {
            int mid = (lo + hi) / 2;
            if (nums[mid] == target) return mid;
            else if (target < nums[mid]) hi = mid - 1;
            else lo = mid + 1;
        }
        
        return lo;
    }
}
```

#### Notes

##### BFS, mid = (low + hi) / 2