# Find the smallest divisor

## Problem Description
Given an array of integers nums and an integer limit as the threshold value, find the smallest positive integer divisor such that upon dividing all the elements of the array by this divisor, the sum of the division results is less than or equal to the threshold value.  
  
After dividing each element by the chosen divisor, take the ceiling of the result (i.e., round up to the next whole number).  

Example 1  

Input: nums = [1, 2, 3, 4, 5], limit = 8  
  
Output: 3  
  
Explanation: We can get a sum of 15(1 + 2 + 3 + 4 + 5) if we choose 1 as a divisor.  
  
The sum is 9(1 + 1 + 2 + 2 + 3) if we choose 2 as a divisor. Upon dividing all the elements of the array by 3, we get 1,1,1,2,2 respectively. Now, their sum is equal to 7 <= 8 i.e. the threshold value. So, 3 is the minimum possible answer.  

Example 2  

Input: nums = [8,4,2,3], limit = 10  
  
Output: 2  
  
Explanation: If we choose 1, we get 17 as the sum. If we choose 2, we get 9 (4+2+1+2) <= 10 as the answer. So, 2 is the answer.  

Example 3  

Input: nums = [8,4,2,3], limit = 4  
  
Output:  
  
8  

Constraints  

1 <= nums.length <= 5 * 10^4  
 1 <= nums[i] <= 10^6  
 nums.length <= limit <= 10^6  

## Solution

```cpp
class Solution {
public:
  int smallestDivisor(vector<int> &nums, int limit) {
        //linear search(TLE)
        int n = nums.size();
        int maxi = *max_element(nums.begin(),nums.end());

        for(int d=1;d<=maxi;d++){
            int sum = 0;
            for(int i=0;i<n;i++){
                sum += ceil((double)nums[i]/(double)d);
            }
            if(sum <= limit){
                return d;
            }
        }
        return -1;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-the-smallest-divisor?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 126/126
- Time: 0.067s
- Memory: 398.62 KiB
