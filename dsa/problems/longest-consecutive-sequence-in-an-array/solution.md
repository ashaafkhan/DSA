# Longest Consecutive Sequence in an Array

## Problem Description
Given an array nums of n integers.  
  
  
  
  
Return the length of the longest sequence of consecutive integers. The integers in this sequence can appear in any order.  

Example 1  

Input: nums = [100, 4, 200, 1, 3, 2]  
  
Output: 4  
  
Explanation:  
  
The longest sequence of consecutive elements in the array is [1, 2, 3, 4], which has a length of 4. This sequence can be formed regardless of the initial order of the elements in the array.  

Example 2  

Input: nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]  
  
Output: 9  
  
Explanation:  
  
The longest sequence of consecutive elements in the array is [0, 1, 2, 3, 4, 5, 6, 7, 8], which has a length of 9.  

Example 3  

Input: nums = [1, 9, 3, 10, 4, 20, 2]  
  
Output:  
  
4  

Constraints  

1 <= nums.length <= 10^5  
     -10^9 <= nums[i] <= 10^9  

## Solution

```cpp
//Brute Force
class Solution {

private:
    bool linearSearch(vector<int>& a, int num){
        int n = a.size();
        for(int i=0;i<n;i++){
            if(a[i]== num){
               return true;
            }
        } 
        return false;

    }

public:
    int longestConsecutive(vector<int>& nums) {
        int n = nums.size();
        if(n==0) return 0;
        int longest = 1;
        for(int i=0;i<n;i++){
            int x = nums[i];
            int cnt =1;
            while(linearSearch(nums,x+1) == true){
                x +=1;
                cnt += 1;
            }
            longest = max(longest,cnt);
        }
        return longest;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/longest-consecutive-sequence-in-an-array?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 122/122
- Time: 0.071s
- Memory: 404.32 KiB
