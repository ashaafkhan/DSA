# Count subarrays with given sum

## Problem Description
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.  

Example 1  

Input: nums = [1, 1, 1], k = 2  
  
Output: 2  
  
Explanation: In the given array [1, 1, 1], there are two subarrays that sum up to 2: [1, 1] and [1, 1]. Hence, the output is 2.  

Example 2  

Input: nums = [1, 2, 3], k = 3  
  
Output: 2  
  
Explanation: In the given array [1, 2, 3], there are two subarrays that sum up to 3: [1, 2] and [3]. Hence, the output is 2.  

Example 3  

Input: nums = [3, 1, 2, 4], k = 6  
  
Output:  
  
2  

Constraints  

1 <= nums.length <= 10^5  
   -1000 <= nums[i] <= 1000  
   -10^7 <= k <= 10^7  

## Solution

```cpp
 class Solution{
public:
    int subarraySum(vector<int> &nums, int k){
        //brute force => O(n^3)
        int n = nums.size();
        int cnt = 0;

        for(int i=0;i<n;i++){
            for(int j=i;j<n;j++){
                int sum = 0;
                for(int l=i;l<=j;l++){
                    sum += nums[l];
                }
                if(sum == k) cnt++;
            }
        }
        return cnt;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/count-subarrays-with-given-sum?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.257s
- Memory: 419.66 KiB
