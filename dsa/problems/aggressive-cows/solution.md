# Aggressive Cows

## Problem Description
Given an array nums of size n, which denotes the positions of stalls, and an integer k, which denotes the number of aggressive cows, assign stalls to k cows such that the minimum distance between any two cows is the maximum possible. Find the maximum possible minimum distance.  

Example 1  

Input: n = 6, k = 4, nums = [0, 3, 4, 7, 10, 9]  
  
Output: 3  
  
Explanation:  
  
The maximum possible minimum distance between any two cows will be 3 when 4 cows are placed at positions [0, 3, 7, 10]. Here the distances between cows are 3, 4, and 3 respectively.  
  
In no manner can we increase the minimum distance beyond 3.  

Example 2  

Input : n = 5, k = 2, nums = [4, 2, 1, 3, 6]  
  
Output: 5  
  
Explanation: The maximum possible minimum distance between any two cows will be 5 when 2 cows are placed at positions [1, 6].  

Example 3  

Input : n = 5, k = 3, nums = [10, 1, 2, 7, 5]  
  
Output:  
  
4  

Constraints  

2 <= n <= 10^5  
  2 <= k <= n  
  0 <= nums[i] <= 10^9  

## Solution

```cpp
class Solution {

private:
    bool canWePlace(vector<int>&nums,int dist,int cows){
        int n = nums.size();
        int cntCows = 1;
        int last = nums[0];
        for(int i=0;i<n;i++){
            if(nums[i]-last>=dist){
                cntCows++;
                last = nums[i];
            }
            if(cntCows>=cows) return true;
        }
        return false;
    }

public:
    int aggressiveCows(vector<int> &nums, int k) {
        //linear search(TLE)
        int n = nums.size();
        sort(nums.begin(),nums.end());
        int limit = nums[n-1]-nums[0];
        for(int i=0;i<=limit;i++){
            if(canWePlace(nums,i,k) == false){
                return (i-1);
            }
        }
        return limit;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/aggressive-cows?subject=dsa-concept-revision&tab=submissions&approach=binary-search

## Stats
- Test Cases: 133/133
- Time: 0.292s
- Memory: 404.87 KiB
