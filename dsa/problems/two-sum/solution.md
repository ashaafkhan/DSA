# Two Sum

## Problem Description
Given an array of integers nums and an integer target. Return the indices(0 - indexed) of two elements in nums such that they add up to target.  
  
  
  
  
Each input will have exactly one solution, and the same element cannot be used twice. Return the answer in any order.  

Example 1  

Input: nums = [1, 6, 2, 10, 3], target = 7  
  
Output: [0, 1]  
  
Explanation:  
  
nums[0] + nums[1] = 1 + 6 = 7  

Example 2  

Input: nums = [1, 3, 5, -7, 6, -3], target = 0  
  
Output: [1, 5]  
  
Explanation:  
  
nums[1] + nums[5] = 3 + (-3) = 0  

Example 3  

Input: nums = [-6, 7, 1, -7, 6, 2], target = 3  
  
Output:  
  
[2, 5]  

Constraints  

2 <= nums.length <= 10^5  
-10^4 <= nums[i] <= 10^4  
-10^5 <= target <= 10^5  
Only one valid answer exists.  

## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {

        //optimal solution => 2 pointer

        int n = nums.size();

        vector<int>ans;

        vector<vector<int>>eleIndex;

        for(int i=0;i<n;i++){
            eleIndex.push_back({nums[i],i});
        }

        sort(eleIndex.begin(),eleIndex.end());

        int left=0, right= n-1;

        while(left<right){
            int sum = eleIndex[left][0] + eleIndex[right][0];
            if(sum == target){
                ans.push_back(eleIndex[left][1]);
                ans.push_back(eleIndex[right][1]);
                return ans;
            }else if(sum< target){
                left++;
            }else{
                right--;
            }
        }

        return {-1,-1};
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/two-sum?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 112/112
- Time: 0.475s
- Memory: 429.03 KiB
