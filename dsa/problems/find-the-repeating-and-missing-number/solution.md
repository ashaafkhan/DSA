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
        // optimal2(xor logic) => O(n)
        long long n = nums.size();
        int xr = 0;

        for(int i=0;i<n;i++){
            xr = xr ^ nums[i];
            xr = xr ^ (i+1);
        }

        // int bitNo = 0;
        // while(1){
        //     if((xr & (1<<bitNo)) != 0){
        //         break;
        //     }
        //     bitNo++;
        // }

        //shortcut to generate 1 at differentiating bit 
        int number = xr & ~(xr-1);

        int zero = 0, one = 0;

        for(int i=0;i<n;i++){
            //part of one club
            if((nums[i] & number) != 0){
                one = one ^ nums[i];
            }
            //part of zero club
            else{
                zero = zero ^ nums[i];
            }
        }

        for(int i=1;i<=n;i++){
            //part of one club
            if((i & number) != 0){
                one = one ^ i;
            }
            //part of zero club
            else{
                zero = zero ^ i;
            }
        }

        int cnt =0;
        for(int i=0;i<n;i++){
            if(nums[i] == zero){
                cnt++;
            }
        }
        if(cnt == 2) return {zero,one};
        return {one,zero};
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-the-repeating-and-missing-number?subject=dsa-concept-revision&approach=optimal-ii&tab=submissions

## Stats
- Test Cases: 116/116
- Time: 0.040s
- Memory: 402.25 KiB
