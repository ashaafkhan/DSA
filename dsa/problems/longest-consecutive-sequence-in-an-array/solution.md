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
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        //optimal
        int n = nums.size();

        if(n==0) return 0;

        int longest = 1 ;
        unordered_set<int>st;

        for(int i=0;i<n;i++){
            st.insert(nums[i]);
        }

        for(auto it: st){
            if(st.find(it-1) == st.end()){
                int cnt=1;
                int x = it;

                while(st.find(x+1) != st.end()){
                    x = x+1;
                    cnt = cnt + 1;
                }
                longest = max(longest,cnt);
            }
        }
        return longest;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/longest-consecutive-sequence-in-an-array?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 122/122
- Time: 0.118s
- Memory: 414.04 KiB
