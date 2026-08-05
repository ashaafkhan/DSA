# Majority Element-I

## Problem Description
Given an integer array nums of size n, return the majority element of the array.  
  
  
  
  
The majority element of an array is an element that appears more than n/2 times in the array. The array is guaranteed to have a majority element.  

Example 1  

Input: nums = [7, 0, 0, 1, 7, 7, 2, 7, 7]  
  
Output: 7  
  
Explanation:  
  
The number 7 appears 5 times in the 9 sized array  

Example 2  

Input: nums = [1, 1, 1, 2, 1, 2]  
  
Output: 1  
  
Explanation:  
  
The number 1 appears 4 times in the 6 sized array  

Example 3  

Input: nums = [-1, -1, -1, -1]  
  
Output:  
  
-1  

Constraints  

n == nums.length.  
1 <= n <= 10^5  
-10^4 <= nums[i] <= 10^4  
One value appears more than n/2 times.  

## Solution

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        //better solution => Hashing(O(nlogn)+O(n))
        int n = nums.size();
        unordered_map<int,int>mp;

        for(int num: nums){
            mp[num]++;
        }

        for(const auto& pair : mp){
            if(pair.second > n/2){
                return pair.first;
            }
        }
        return -1;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/majority-element-i?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 118/118
- Time: 0.056s
- Memory: 415.56 KiB
