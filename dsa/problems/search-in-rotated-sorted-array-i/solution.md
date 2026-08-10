# Search in rotated sorted array-I

## Problem Description
Given an integer array nums, sorted in ascending order (with distinct values) and a target value k. The array is rotated at some pivot point that is unknown. Find the index at which k is present and if k is not present return -1.  

Example 1  

Input : nums = [4, 5, 6, 7, 0, 1, 2], k = 0  
  
Output: 4  
  
Explanation: Here, the target is 0. We can see that 0 is present in the given rotated sorted array, nums. Thus, we get output as 4, which is the index at which 0 is present in the array.  

Example 2  

Input: nums = [4, 5, 6, 7, 0, 1, 2], k = 3  
  
Output: -1  
  
Explanation: Here, the target is 3. Since 3 is not present in the given rotated sorted array. Thus, we get the output as -1.  

Example 3  

Input: nums = [4, 5, 6, 7, 0, 1, 2], k = 5  
  
Output:  
  
1  

Constraints  

1 <= nums.length <= 10^4  
  -10^4 <= nums[i] <= 10^4  
  All values of nums are unique.  
  nums is an ascending array that is possibly rotated.  
  -10^4 <= k <= 10^4  

## Solution

```cpp
class Solution {
public:
    int search(vector<int> &nums, int k) {
        //linear search => O(n)
        int n = nums.size();

        for(int i=0;i<n;i++){
            if(nums[i] == k){
                return i;
            }
        }
       return -1;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/search-in-rotated-sorted-array-i?approach=linear-search&tab=submissions

## Stats
- Test Cases: 144/144
- Time: 0.011s
- Memory: 397.07 KiB
