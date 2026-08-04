# 4 Sum

## Problem Description
Given an integer array nums and an integer target. Return all quadruplets [nums[a], nums[b], nums[c], nums[d]] such that:  
  
  
  
  
a, b, c, d are all distinct valid indices of nums.  
  
  
  
  
nums[a] + nums[b] + nums[c] + nums[d] == target.  
  
  
  
  
Notice that the solution set must not contain duplicate quadruplets. One element can be a part of multiple quadruplets. The output and the quadruplets can be returned in any order.  

Example 1  

Input: nums = [1, -2, 3, 5, 7, 9], target = 7  
  
Output: [[-2, 1, 3, 5]]  
  
Explanation:  
  
nums[1] + nums[0] + nums[2] + nums[3] = 7  

Example 2  

Input: nums = [7, -7, 1, 2, 14, 3], target = 9  
  
Output: []  
  
Explanation:  
  
No quadruplets are present which add upto 9  

Example 3  

Input: nums = [1, 1, 3, 4, -3], target = 5  
  
(Give answer with the output and quadruplets sorted in ascending order)  
  
Output:  
  
[[-3, 1, 3, 4]]  

Constraints  

1 <= nums.length <= 200  
-10^4 <= nums[i] <= 10^4  
-10^4 <= target <= 10^4  

## Solution

```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        //brute forc => O(n^4)

        int n = nums.size();
        set<vector<int>>st;

        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                for(int k=j+1;k<n;k++){
                    for(int l=k+1;l<n;l++){
                        long long sum = nums[i] +nums[j];
                        sum += nums[k];
                        sum += nums[l];

                        if(sum==target){
                            vector<int>temp = {nums[i],nums[j],nums[k],nums[l]};
                            sort(temp.begin(),temp.end());
                            st.insert(temp);
                        }
                    }
                }
            }
        }

        vector<vector<int>> ans(st.begin(),st.end());
        return ans;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/4-sum?subject=dsa-concept-revision&approach=brute&tab=submissions

## Stats
- Test Cases: 67/67
- Time: 4.960s
- Memory: 443.33 KiB
