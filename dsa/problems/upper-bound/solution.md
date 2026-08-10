# Upper Bound

## Problem Description
Given a sorted array of nums and an integer x, write a program to find the upper bound of x.  
  
  
  
  
The upper bound of x is defined as the smallest index i such that nums[i] > x.  
  
  
  
  
If no such index is found, return the size of the array.  

Example 1  

Input : n= 4, nums = [1,2,2,3], x = 2  
  
Output:3  
  
Explanation:  
  
Index 3 is the smallest index such that arr[3] > x.  

Example 2  

Input : n = 5, nums = [3,5,8,15,19], x = 9  
  
Output: 3  
  
Explanation:  
  
Index 3 is the smallest index such that arr[3] > x.  

Example 3  

Input : n = 5, nums = [3,5,8,15,19], x = 3  
  
Output:  
  
1  

Constraints  

1 <= nums.length <= 10^5  
  -10^5 < nums[i], x < 10^5  
  nums is sorted in ascending order.  

## Solution

```cpp
class Solution{
public:
    int upperBound(vector<int> &nums, int x){
        //brute force
        int n = nums.size();
        for(int i=0;i<n;i++){
            if(nums[i]>x){
                return i;
            }
        }
        return n;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/upper-bound?subject=dsa-concept-revision&approach=brute&tab=submissions

## Stats
- Test Cases: 113/113
- Time: 0.053s
- Memory: 397.06 KiB
