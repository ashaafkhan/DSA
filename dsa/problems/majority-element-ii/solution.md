# Majority Element-II

## Problem Description
Given an integer array nums of size n. Return all elements which appear more than n/3 times in the array. The output can be returned in any order.  

Example 1  

Input: nums = [1, 2, 1, 1, 3, 2]  
  
Output: [1]  
  
Explanation:  
  
Here, n / 3 = 6 / 3 = 2.  
  
Therefore the elements appearing 3 or more times is : [1]  

Example 2  

Input: nums = [1, 2, 1, 1, 3, 2, 2]  
  
Output: [1, 2]  
  
Explanation:  
  
Here, n / 3 = 7 / 3 = 2.  
  
Therefore the elements appearing 3 or more times is : [1, 2]  

Example 3  

Input: nums = [1, 2, 1, 1, 3, 2, 2, 3](Give the solution sorted in ascending order)  
  
Output:  
  
[1, 2]  

Constraints  

n == nums.length.  
2 <= n <= 10^5  
-10^4 <= nums[i] <= 10^4  

## Solution

```cpp
class Solution {
public:
    vector<int> majorityElementTwo(vector<int>& nums) {

        int n = nums.size();
        vector<int>result;
        unordered_map<int,int>mpp;
        int mini = int(n/3) + 1;

        for(int i=0;i<n;i++){
            mpp[nums[i]]++;
            if(mpp[nums[i]]==mini){
                result.push_back(nums[i]);
            }
            if(result.size()==2) break;
        }
        return result;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/majority-element-ii?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 118/118
- Time: 0.052s
- Memory: 424.26 KiB
