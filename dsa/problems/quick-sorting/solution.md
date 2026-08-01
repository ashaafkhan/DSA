# Quick Sorting

## Problem Description
Given an array of integers called nums, sort the array in non-decreasing order using the quick sort algorithm and return the sorted array.  
  
  
  
  
A sorted array in non-decreasing order is an array where each element is greater than or equal to all preceding elements in the array.  

Example 1  

Input: nums = [7, 4, 1, 5, 3]  
  
Output: [1, 3, 4, 5, 7]  
  
Explanation: 1 <= 3 <= 4 <= 5 <= 7.  
  
Thus the array is sorted in non-decreasing order.  

Example 2  

Input: nums = [5, 4, 4, 1, 1]  
  
Output: [1, 1, 4, 4, 5]  
  
Explanation: 1 <= 1 <= 4 <= 4 <= 5.  
  
Thus the array is sorted in non-decreasing order.  

Example 3  

Input: nums = [3, 2, 3, 4, 5]  
  
Output:  
  
[2, 3, 3, 4, 5]  

Constraints  

1 <= nums.length <= 10^5  
-10^4 <= nums[i] <= 10^4  
nums[i] may contain duplicate values.  

## Solution

```cpp
class Solution {
public:

    int func(vector<int>&arr,int low,int high){
        int pivot = arr[low];
        int i = low;
        int j = high;
        while(i<j){
            while(arr[i]<=pivot && i<=high-1){
                i++;
            }
            while(arr[j]>pivot && j>=low+1){
                j--;
            }
            if(i<j){
                swap(arr[i],arr[j]);
            }
        }
        swap(arr[low],arr[j]);
        return j;
    }

    void qs(vector<int>&arr,int low,int high){
        if(low<high){
            int pIndex = func(arr,low,high);
            qs(arr,low,pIndex-1);
            qs(arr,pIndex+1,high);
        }
    }

    vector<int> quickSort(vector<int>& nums) {
        qs(nums,0,nums.size()-1);
        return nums;
    }
};

```

## Problem Link
https://takeuforward.org/plus/dsa/problems/quick-sorting?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.016s
- Memory: 401.18 KiB
