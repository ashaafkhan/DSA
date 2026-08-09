# Count subarrays with given xor K

## Problem Description
Given an array of integers nums and an integer k, return the total number of subarrays whose XOR equals to k.  

Example 1  

Input : nums = [4, 2, 2, 6, 4], k = 6  
  
  
  
  
Output : 4  
  
  
  
  
Explanation : The subarrays having XOR of their elements as 6 are [4, 2],  [4, 2, 2, 6, 4], [2, 2, 6], and [6]  

Example 2  

Input :nums = [5, 6, 7, 8, 9], k = 5  
  
  
  
  
Output : 2  
  
  
  
  
Explanation : The subarrays having XOR of their elements as 5 are [5] and [5, 6, 7, 8, 9]  

Example 3  

Input : nums = [5, 2, 9], k = 7  
  
Output:  
  
1  

Constraints  

1 <= nums.length <= 10^5  
  1 <= nums[i] <= 10^9  
  1 <= k <= 10^9  

## Solution

```cpp
class Solution{
public:
    int subarraysWithXorK(vector<int> &nums, int k) {
        int n = nums.size();
        int xr = 0;
        map<int,int>mpp;
        mpp[xr]++;
        int cnt = 0;
        for(int i=0;i<n;i++){
            xr = xr ^ nums[i];
            int x = xr ^ k;
            cnt += mpp[x];
            mpp[xr]++;
        }
        return cnt;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/count-subarrays-with-given-xor-k?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 124/124
- Time: 0.453s
- Memory: 417.25 KiB
