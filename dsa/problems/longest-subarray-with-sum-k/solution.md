# Longest subarray with sum K

## Problem Description
Given an array nums of size n and an integer k, find the length of the longest sub-array that sums to k. If no such sub-array exists, return 0.  

Example 1  

Input: nums = [10, 5, 2, 7, 1, 9],  k=15  
  
Output: 4  
  
Explanation:  
  
The longest sub-array with a sum equal to 15 is [5, 2, 7, 1], which has a length of 4. This sub-array starts at index 1 and ends at index 4, and the sum of its elements (5 + 2 + 7 + 1) equals 15. Therefore, the length of this sub-array is 4.  

Example 2  

Input: nums = [-3, 2, 1], k=6  
  
Output: 0  
  
Explanation:  
  
There is no sub-array in the array that sums to 6. Therefore, the output is 0.  

Example 3  

Input: nums = [-1, 1, 1], k=1  
  
Output:  
  
3  

Constraints  

1<=n<=10^5  
 -10^5<=nums[i]<=10^5  
 -10^9<= k<=10^9  

## Solution

```cpp
class Solution{
public:
    int longestSubarray(vector<int> &nums, int k){

        //better soln for positive & optimal soln for positive+negative => hashmap

        int n = nums.size();

        map<int,int>preSumMap;
        int sum=0;
        int maxLen = 0;
        for(int i=0;i<n;i++){
            sum += nums[i];
            if(sum == k){
                maxLen = max(maxLen,i+1);
            }
            int rem = sum - k;
            if(preSumMap.find(rem) != preSumMap.end()){
                int len = i - preSumMap[rem];
                maxLen = max(maxLen,len);
            }
            if(preSumMap.find(sum) == preSumMap.end()){
                preSumMap[sum] = i;
            }
        }
        return maxLen;
    }
};

```

## Problem Link
https://takeuforward.org/plus/dsa/problems/longest-subarray-with-sum-k?subject=dsa-concept-revision&approach=optimal-only-positives&tab=submissions

## Stats
- Test Cases: 124/124
- Time: 0.257s
- Memory: 417.63 KiB
