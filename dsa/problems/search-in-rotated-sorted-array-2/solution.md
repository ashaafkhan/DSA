# Search in rotated sorted array-II

## Problem Description
Given an integer array nums, sorted in ascending order (may contain duplicate values) and a target value k. Now the array is rotated at some pivot point unknown to you. Return True if k is present and otherwise, return False.  

Example 1  

Input : nums = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6], k = 3  
  
Output: True  
  
Explanation: The element 3 is present in the array. So, the answer is True.  

Example 2  

Input : nums = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6], k = 10  
  
Output: False  
  
Explanation:The element 10 is not present in the array. So, the answer is False.  

Example 3  

Input : nums = [7, 8, 1, 2, 3, 3, 3, 4, 5, 6], k = 7  
  
Output:  
  
True  

Constraints  

1 <= nums.length <= 10^4  
  -10^4 <= nums[i] <= 10^4  
  nums is guaranteed to be rotated at some pivot.  
  -10^4 <= k <= 10^4  

## Solution

```cpp
class Solution {
public:
    bool searchInARotatedSortedArrayII(vector<int> &nums, int k)  {
        //brute force
        int n = nums.size();

        for(int i=0;i<n;i++){
            if(nums[i] == k){
                return true;
            }
        }
        return false;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/search-in-rotated-sorted-array-2?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 136/136
- Time: 0.014s
- Memory: 397.09 KiB
