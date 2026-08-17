# Find peak element

## Problem Description
Given an array arr of integers. A peak element is defined as an element greater than both of its neighbors.  
  
Formally, if arr[i] is the peak element, arr[i - 1] < arr[i] and arr[i + 1] < arr[i].  
  
  
  
  
Find the index(0-based) of a peak element in the array. If there are multiple peak numbers, return the index of any peak number.  
  
  
  
  
Note:  
  
As there can be many peak values, "true" is given as output if the returned index is a peak number, otherwise the returned value of index.  

Example 1  

Input : arr = [1, 2, 3, 4, 5, 6, 7, 8, 5, 1]  
  
Output: 7  
  
Explanation: In this example, there is only 1 peak that is at index 7.  

Example 2  

Input : arr = [1, 2, 1, 3, 5, 6, 4]  
  
Output: 1  
  
Explanation: In this example, there are 2 peak numbers at indices 1 and 5. We can consider any of them.  

Example 3  

Input : arr = [-2, -1, 3, 4, 5]  
  
Output:  
  
4  

Constraints  

1 <= arr.length <= 1000  
 -2^31 <= arr[i] <= 2^31 - 1  
 arr[i] != arr[i + 1] for all valid i.  
For arr[0], its left element can be considered as -∞  
For arr[n-1], its right element can be considered as -∞  

## Solution

```cpp
class Solution {
public:
    int findPeakElement(vector<int> &arr) {
        //linear search
        int n = arr.size();
        for(int i=0;i<n;i++){
            if((i==0 || arr[i-1]<arr[i])&&(i==n-1 || arr[i]>arr[i+1])){
                return i;
            }
        }
        return -1;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-peak-element?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.007s
- Memory: 401.14 KiB
