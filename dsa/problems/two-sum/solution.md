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

        //brute force=> O(n^2)

        int n = nums.size();
        vector<int>ans;

        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                if(nums[i]+nums[j]==target){
                    ans.push_back(i);
                    ans.push_back(j);
                    return ans;
                }
            }
        }
        return {-1,-1};
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/two-sum?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 112/112
- Time: 0.071s
- Memory: 426.00 KiB
