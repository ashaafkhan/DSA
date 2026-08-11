# Find minimum in Rotated Sorted Array

## Problem Description
Given an integer array nums of size N, sorted in ascending order with distinct values, and then rotated an unknown number of times (between 1 and N), find the minimum element in the array.  

Example 1  

Input : nums = [4, 5, 6, 7, 0, 1, 2, 3]  
  
Output: 0  
  
Explanation: Here, the element 0 is the minimum element in the array.  

Example 2  

Input : nums = [3, 4, 5, 1, 2]  
  
Output: 1  
  
Explanation:Here, the element 1 is the minimum element in the array.  

Example 3  

Input : nums = [4, 5, 6, 7, -7, 1, 2, 3]  
  
Output:  
  
-7  

Constraints  

n == nums.length  
 1 <= n <= 10^4  
 -10^4 <= nums[i] <= 10^4  
 All the integers of nums are unique.  
 nums is sorted and rotated between 1 and n times.  

## Solution

```cpp
class Solution {
public:
    int findMin(vector<int> &arr)  {
        //linear search

        int n = arr.size();
        int mini = INT_MAX;
        for(int i=0;i<n;i++){
            mini = min(mini,arr[i]);
        }
        return mini;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-minimum-in-rotated-sorted-array?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 104/104
- Time: 0.010s
- Memory: 397.19 KiB
