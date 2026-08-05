# Find the repeating and missing number

## Problem Description
Given an integer array nums of size n containing values from [1, n] and each value appears exactly once in the array, except for A, which appears twice and B which is missing.  
  
  
  
  
Return the values A and B, as an array of size 2, where A appears in the 0-th index and B in the 1st index.  
  
  
  
  
Note: You are not allowed to modify the original array.  

Example 1  

Input: nums = [3, 5, 4, 1, 1]  
  
Output: [1, 2]  
  
Explanation:  
  
1 appears two times in the array and 2 is missing from nums  

Example 2  

Input: nums = [1, 2, 3, 6, 7, 5, 7]  
  
Output: [7, 4]  
  
Explanation:  
  
7 appears two times in the array and 4 is missing from nums.  

Example 3  

Input: nums = [6, 5, 7, 1, 8, 6, 4, 3, 2]  
  
Output:  
  
[6, 9]  

Constraints  

n == nums.length  
1 <= n <= 10^5  
n - 2 elements in nums appear exactly once and are valued between [1, n].  
1 element in nums appears twice, and is valued between [1, n].  

## Solution

```cpp
class Solution {
public:
    vector<int> findMissingRepeatingNumbers(vector<int> nums) {
        //optimal1(maths) => O(n)

        long long n = nums.size();
        //S - Sn  = x(repeating) - y(missing)
        //S2 - S2n

        long long Sn = (n * (n+1))/2;
        long long S2n = (n *(n+1) * (2*n+1))/6;

        long long S=0, S2=0;
        for(int i=0;i<n;i++){
            S += nums[i];
            S2 += (long long)nums[i] * (long long)nums[i];
        }

        long long val1 = S - Sn; //x-y
        long long val2 = S2 - S2n;
        val2 = val2 / val1; //x+y

        long long x = (val1 + val2)/2;

        long long y = x - val1;

        return {(int)x,(int)y};

    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-the-repeating-and-missing-number?subject=dsa-concept-revision&approach=optimal-i&tab=submissions

## Stats
- Test Cases: 116/116
- Time: 0.039s
- Memory: 402.20 KiB
