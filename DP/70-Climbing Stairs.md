## 70. Climbing Stairs

#### You are climbing a stair case. It takes n steps to reach to the top.

#### Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

#### Example

```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps

Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

#

## Solution

```
class Solution {
    public int climbStairs(int n) {
        if (n == 1) {return 1;}
        int first = 1;
        int second = 2;
        for(int i = 3; i <= n; i++) {
            int third = first + second;
            first = second;
            second = third;
        }
        
        return second;
    }
}
```

#### Notes: Fibonacci Number: 1, 1, 2, 3, 5, 8, 13