# Check if there exists a subsequence with sum K

## Problem Description
Given an array nums and an integer k. R﻿eturn true if there exist subsequences such that the sum of all elements in subsequences is equal to k else false.  

Example 1  

Input : nums = [1, 2, 3, 4, 5] , k = 8  
  
Output : Yes  
  
Explanation : The subsequences like [1, 2, 5] , [1, 3, 4] , [3, 5] sum up to 8.  

Example 2  

Input : nums = [4, 3, 9, 2] , k = 10  
  
Output : No  
  
Explanation : No subsequence can sum up to 10.  

Example 3  

Input : nums = [1, 10, 4, 5] , k = 16  
  
Output:  
  
true  

Constraints  

1 <= nums.length <= 20  
1 <= nums[i] <= 100  
1 <= k <= 2000  

## Solution

```cpp
class Solution{

    private:
    bool func(int ind,int sum,vector<int>&nums){
        if(ind==nums.size()){
            return sum==0;
        }
        return func(ind+1,sum-nums[ind],nums) | func(ind+1,sum,nums);
    }

    public:
    bool checkSubsequenceSum(vector<int>& nums, int k) {
         //your code goes here
         return func(0,k,nums);
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/check-if-there-exists-a-subsequence-with-sum-k?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 131/131
- Time: 0.331s
- Memory: 397.51 KiB
