# 3 Sum

## Problem Description
Given an integer array nums. Return all triplets such that:  
  
  
  
  
i != j, i != k, and j != k  
  
  
  
  
nums[i] + nums[j] + nums[k] == 0.  
  
  
  
  
Notice that the solution set must not contain duplicate triplets. One element can be a part of multiple triplets. The output and the triplets can be returned in any order.  

Example 1  

Input: nums = [2, -2, 0, 3, -3, 5]  
  
Output: [[-2, 0, 2], [-3, -2, 5], [-3, 0, 3]]  
  
Explanation:  
  
nums[1] + nums[2] + nums[0] = 0  
  
nums[4] + nums[1] + nums[5] = 0  
  
nums[4] + nums[2] + nums[3] = 0  

Example 2  

Input: nums = [2, -1, -1, 3, -1]  
  
Output: [[-1, -1, 2]]  
  
Explanation:  
  
nums[1] + nums[2] + nums[0] = 0  
  
Note that we have used two -1s as they are separate elements with different indexes  
  
But we have not used the -1 at index 4 as that would create a duplicate triplet  

Example 3  

Input: nums = [8, -6, 5, 4]  
  
(Give answer with the output and triplets sorted in ascending order)  
  
Output:  
  
[]  

Constraints  

1 <= nums.length <= 3000  
-10^4 <= nums[i] <= 10^4  

## Solution

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        //better soln
        int n = nums.size();

        set<vector<int>>tripletSet;

        for(int i=0;i<n;i++){
            set<int>hashset;
            for(int j = i+1;j<n;j++){
                int third = -(nums[i]+nums[j]);
                if(hashset.find(third) != hashset.end()){
                    vector<int>temp = {nums[i],nums[j],third};

                    sort(temp.begin(),temp.end());
                    tripletSet.insert(temp);
                }
                hashset.insert(nums[j]);
            }
        }
        vector<vector<int>>ans(tripletSet.begin(),tripletSet.end());
        return ans;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/3-sum?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 124/124
- Time: 3.634s
- Memory: 457.70 KiB
