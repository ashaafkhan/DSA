# Kadane's Algorithm

## Problem Description
Given an integer array nums, find the subarray with the largest sum and return the sum of the elements present in that subarray.  
  
  
  
  
A subarray is a contiguous non-empty sequence of elements within an array.  

Example 1  

Input: nums = [2, 3, 5, -2, 7, -4]  
  
Output: 15  
  
Explanation:  
  
The subarray from index 0 to index 4 has the largest sum = 15  

Example 2  

Input: nums = [-2, -3, -7, -2, -10, -4]  
  
Output: -2  
  
Explanation:  
  
The element on index 0 or index 3 make up the largest sum when taken as a subarray  

Example 3  

Input: nums = [-1, 2, 3, -1, 2, -6, 5]  
  
Output:  
  
6  

Constraints  

1 <= nums.length <= 10^5  
-10^4 <= nums[i] <= 10^4  

## Solution

```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {

        int n = nums.size();
        long long sum =0, maxi = LLONG_MIN;

        for(int i =0;i<n;i++){

            sum += nums[i];

            if(sum>maxi){
                maxi=sum;
            }

            if(sum<0){
                sum =0;
            }
        }
        return maxi;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/kadane's-algorithm?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.029s
- Memory: 397.31 KiB
