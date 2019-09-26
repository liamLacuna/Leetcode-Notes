## 134. Gas Station

#### There are N gas stations along a circular route, where the amount of gas at station i is gas[i].

#### You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from station i to its next station (i+1). You begin the journey with an empty tank at one of the gas stations.

#### Return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1.

#

## Solution
```
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int n = gas.length; 
        
        int total_tank = 0;
        int curr_tank = 0;
        
        int starting_station = 0;
        
        for(int i = 0; i < n; ++i){
            total_tank += gas[i] - cost[i];
            curr_tank += gas[i] - cost[i];
            
            if(curr_tank < 0) {
                starting_station = i + 1;// Changing station if curr_tank < 0
                curr_tank = 0;
            }
        }
        
        return total_tank >= 0 ? starting_station: -1;
    }
}
```

#### Notes

##### Since there is only one correct solution, means there is only one starting position station can work. We can just find the first starting_station that work as the current tank would not less than 0. 