## 80. Remove Duplicates from Sorted Array II

#### Given a sorted array nums, remove the duplicates in-place such that duplicates appeared at most twice and return the new length.

#### Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

#

## Solution

```
public int removeDuplicates(int[] nums) {
    int i = 0;
    for (int n : nums)
        if (i < 2 || n > nums[i-2])
            nums[i++] = n;
    return i;
}
```

## Notes

##### Since it's sorted array, the third same element would be skip and not counted. 


