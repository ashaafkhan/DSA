# Power Set

## Problem Description
Given an array of integers nums of unique elements. Return all possible subsets (power set) of the array.  
  
  
  
  
Do not include the duplicates in the answer.  

Example 1  

Input : nums = [1, 2, 3]  
  
Output : [ [ ] , [1] , [2] , [1, 2] , [3] , [1, 3] , [2, 3] , [1, 2 ,3] ]  

Example 2  

Input : nums = [1, 2]  
  
Output : [ [ ] , [1] , [2] , [1,2] ]  

Example 3  

Input : nums = [0]  
  
Output:  
  
[ [ ] , [0] ]  

Constraints  

1 <= nums.length <= 10  
-10 <= nums[i] <= 10  

## Solution

```cpp
class Solution {

private:
    void func(int ind,int n,vector<int>&nums,vector<int>&arr,vector<vector<int>>&ans){
        if(ind==n){
            ans.push_back(arr);
            return;
        }
        func(ind+1,n,nums,arr,ans);
        arr.push_back(nums[ind]);
        func(ind+1,n,nums,arr,ans);
        arr.pop_back();
    }
public:	
    vector<vector<int> > powerSet(vector<int>& nums) {
        //your code goes here
        vector<vector<int>>ans;
        vector<int>arr;
        func(0,nums.size(),nums,arr,ans);
        return ans;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/power-set?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 50/50
- Time: 0.168s
- Memory: 214.79 KiB
