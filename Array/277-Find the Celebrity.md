## 277. Find the Celebrity

#### Suppose you are at a party with n people (labeled from 0 to n - 1) and among them, there may exist one celebrity. The definition of a celebrity is that all the other n - 1 people know him/her but he/she does not know any of them.

#### Now you want to find out who the celebrity is or verify that there is not one. The only thing you are allowed to do is to ask questions like: "Hi, A. Do you know B?" to get information of whether A knows B. You need to find out the celebrity (or verify there is not one) by asking as few questions as possible (in the asymptotic sense).

#### You are given a helper function bool knows(a, b) which tells you whether A knows B. Implement a function int findCelebrity(n). There will be exactly one celebrity if he/she is in the party. Return the celebrity's label if there is a celebrity in the party. If there is no celebrity, return -1.


#

## Solution
```
/* The knows API is defined in the parent class Relation.
      boolean knows(int a, int b); */

public class Solution extends Relation {
    public int findCelebrity(int n) {
        int k = 0;
        for(int i = 0; i < n; i++)
            k = knows(i, k)? k : i;
        for(int i = 0; i < n; i++) {
            if(i != k && knows(k, i) || !knows(i, k))
                return -1;
        }
        return k;
    }
}
```

## Notes
##### O(n)
##### Since there is only one celebraty or none, we can find the potential celebraty as the first for loop. (Everyone knows him/her, but he/she doesn't know anyone). Then we can confirm the celebraty in the second for loop. 
