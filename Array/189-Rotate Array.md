## 189. Rotate Array

#### Given an array, rotate the array to the right by k steps, where k is non-negative.

#### Example

```
Input: [1,2,3,4,5,6,7] and k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

#

## Solution
```
class Solution(){
    public void rotate(int[] nums, int k){
        if(nums.length < 2 || nums.length == 0) return;

        int breakPoint = nums % k;

        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, breakPoint - 1);
        reverse(nums, breakPoint, nums.length - 1);

    }

    public void reverse(int[] nums, int start, int end){
        int temp;
        while (start < end){
            temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

### Notes
Through the discover, we can rotatet the whole array first, the rotate the array from 0 to k, and k to the end. 

#### Example
```
Let n=7 and k=3

Original List                   : 1 2 3 4 5 6 7
After reversing all numbers     : 7 6 5 4 3 2 1
After reversing first k numbers : 5 6 7 4 3 2 1
After revering last n-k numbers : 5 6 7 1 2 3 4 --> Result
```
