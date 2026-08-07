# Reverse Pairs

## Problem Description
Given an integer array nums. Return the number of reverse pairs in the array.  
  
  
  
  
An index pair (i, j) is called a reverse pair if:  
  
  
  
  
0 <= i < j < nums.length  
  
  
  
  
nums[i] > 2 * nums[j]  

Example 1  

Input: nums = [6, 4, 1, 2, 7]  
  
Output: 3  
  
Explanation:  
  
The reverse pairs are:  
  
(0, 2) : nums[0] = 6, nums[2] = 1, 6 > 2 * 1  
  
(0, 3) : nums[0] = 6, nums[3] = 2, 6 > 2 * 2  
  
(1, 2) : nums[1] = 4, nums[2] = 1, 4 > 2 * 1  

Example 2  

Input: nums = [5, 4, 4, 3, 3]  
  
Output: 0  
  
Explanation:  
  
No pairs satisfy both the conditons.  

Example 3  

Input: nums = [6, 4, 4, 2, 2]  
  
Output:  
  
2  

Constraints  

1 <= nums.length <= 5 * 10^4  
-2^31 <= nums[i] <= 2^31 - 1  

## Solution

```cpp
class Solution {
public:
    int reversePairs(vector<int>& nums) {

        //brute force(TLE)

        int n = nums.size();
        int count = 0;

        for(int i=0;i<n;i++){
            for(int j = i+1; j<n;j++){
                if((long long)nums[i]> (long long)2* nums[j]){
                    count++;
                }
            }
        }
        return count;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/reverse-pairs?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 151/151
- Time: 0.667s
- Memory: 401.82 KiB
