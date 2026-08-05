# Count Inversions

## Problem Description
Given an integer array nums. Return the number of inversions in the array.  
  
  
  
  
Two elements a[i] and a[j] form an inversion if a[i] > a[j] and i < j.  
  
  
  
  
It indicates how close an array is to being sorted.  
  
  
  
  
A sorted array has an inversion count of 0.  
  
  
  
  
An array sorted in descending order has maximum inversion.  

Example 1  

Input: nums = [2, 3, 7, 1, 3, 5]  
  
Output: 5  
  
Explanation:  
  
The responsible indexes are:  
  
nums[0], nums[3], values: 2 > 1 & indexes: 0 < 3  
  
nums[1], nums[3], values: 3 > 1 & indexes: 1 < 3  
  
nums[2], nums[3], values: 7 > 1 & indexes: 2 < 3  
  
nums[2], nums[4], values: 7 > 3 & indexes: 2 < 4  
  
nums[2], nums[5], values: 7 > 5 & indexes: 2 < 5  

Example 2  

Input: nums = [-10, -5, 6, 11, 15, 17]  
  
Output: 0  
  
Explanation:  
  
nums is sorted, hence no inversions present.  

Example 3  

Input: nums = [9, 5, 4, 2]  
  
Output:  
  
6  

Constraints  

1 <= nums.length <= 10^5  
-10^5 <= nums[i] <= 10^5  

## Solution

```cpp
class Solution {
public:
   long long int numberOfInversions(vector<int> nums) {
    //brute force (doesn't work)

    int n = nums.size();

    int cnt=0;
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(nums[i]>nums[j]) cnt++;
        }
    }
    return cnt;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/count-inversions?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 119/119
- Time: 0.474s
- Memory: 404.39 KiB
