# Find minimum in Rotated Sorted Array

## Problem Description
Given an integer array nums of size N, sorted in ascending order with distinct values, and then rotated an unknown number of times (between 1 and N), find the minimum element in the array.  

Example 1  

Input : nums = [4, 5, 6, 7, 0, 1, 2, 3]  
  
Output: 0  
  
Explanation: Here, the element 0 is the minimum element in the array.  

Example 2  

Input : nums = [3, 4, 5, 1, 2]  
  
Output: 1  
  
Explanation:Here, the element 1 is the minimum element in the array.  

Example 3  

Input : nums = [4, 5, 6, 7, -7, 1, 2, 3]  
  
Output:  
  
-7  

Constraints  

n == nums.length  
 1 <= n <= 10^4  
 -10^4 <= nums[i] <= 10^4  
 All the integers of nums are unique.  
 nums is sorted and rotated between 1 and n times.  

## Solution

```cpp
class Solution {
public:
    int findMin(vector<int> &arr)  {
        //binary search
        int n = arr.size();
        int low = 0, high=n-1;
        int ans = INT_MAX;

        while(low<=high){
            int mid = (high+low)/2;
            if(arr[low]<=arr[high]){
                ans = min(ans,arr[low]);
                break;
            }
            //left sorted
            if(arr[low]<=arr[mid]){
                ans = min(ans,arr[low]);
                low = mid+1;
            }//right sorted
            else{
                ans = min(ans,arr[mid]);
                high = mid-1;
                
            }
        }
        return ans;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-minimum-in-rotated-sorted-array?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 104/104
- Time: 0.011s
- Memory: 397.54 KiB
