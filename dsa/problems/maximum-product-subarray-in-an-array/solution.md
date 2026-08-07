# Maximum Product Subarray in an Array

## Problem Description
Given an integer array nums. Find the subarray with the largest product, and return the product of the elements present in that subarray.  
  
  
  
  
A subarray is a contiguous non-empty sequence of elements within an array.  

Example 1  

Input: nums = [4, 5, 3, 7, 1, 2]  
  
Output: 840  
  
Explanation:  
  
The largest product is given by the whole array itself  

Example 2  

Input: nums = [-5, 0, -2]  
  
Output: 0  
  
Explanation:  
  
The largest product is achieved with the following subarrays [0], [-5, 0], [0, -2], [-5, 0, -2].  

Example 3  

Input: nums = [1, -2, 3, 4, -4, -3]  
  
Output:  
  
144  

Constraints  

1 <= nums.length <= 10^4  
-10 <= nums[i] <= 10  
-10^9 <= product of any prefix or suffix of nums <= 10^9  

## Solution

```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        // optimal => O(n)
        int pre = 1, suff = 1;
        int n = nums.size();
        int ans = INT_MIN;
        for(int i=0;i<n;i++){
            if(pre == 0) pre=1;
            if(suff == 0) suff=1;

            pre = pre * nums[i];
            suff = suff * nums[n-i-1];
            ans = max(ans,max(pre,suff));
        }
        return ans;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/maximum-product-subarray-in-an-array?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 119/119
- Time: 0.010s
- Memory: 397.07 KiB
