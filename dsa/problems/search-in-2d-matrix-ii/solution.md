# Search in 2D matrix - II

## Problem Description
Given a 2D array matrix where each row is sorted in ascending order from left to right and each column is sorted in ascending order from top to bottom, write an efficient algorithm to search for a specific integer target in the matrix.  

Example 1  

Input: matrix = [ [1, 4, 7, 11, 15], [2, 5, 8, 12, 19], [3, 6, 9, 16, 22], [10, 13, 14, 17, 24], [18, 21, 23, 26, 30] ], target = 5  
  
Output: True  
  
Explanation: The target 5 exists in the matrix in the index (1,1)  

Example 2  

Input: matrix= [ [1, 4, 7, 11, 15], [2, 5, 8, 12, 19], [3, 6, 9, 16, 22], [10, 13, 14, 17, 24], [18, 21, 23, 26, 30] ], target = 20  
  
Output: False  
  
Explanation: The target 20 does not exist in the matrix.  

Example 3  

Input: matrix= [ [1, 4, 7, 11, 15], [2, 5, 8, 12, 19], [3, 6, 9, 16, 22], [10, 13, 14, 17, 24], [18, 21, 23, 26, 30] ], target = 1  
  
Output:  
  
True  

Constraints  

n == matrix.length  
  m == matrix[i].length  
  1 <= n, m <= 300  
  -10^9 <= matrix[i][j] <= 10^9  
  All the integers in each row are sorted in ascending order.  
  All the integers in each column are sorted in ascending order.  
  -10^9 <= target <= 10^9  

## Solution

```cpp
class Solution{

private:
    bool binarySearch(vector<int>&nums,int target){
    int n = nums.size();
    int low=0,high=n-1;

    while(low<=high){
        int mid = (low+high)/2;
        if(nums[mid]==target) return true;
        else if(target>nums[mid]) low = mid+1;
        else high = mid-1;
    }
    return false;
    }
    
public:
 bool searchMatrix(vector<vector<int>> &matrix, int target){
    //better soln
    int n = matrix.size();
    int m = matrix[0].size();
    for(int i=0;i<n;i++){
        bool flag = binarySearch(matrix[i],target);
        if(flag) return true;
    }
    return false;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/search-in-2d-matrix-ii?subject=dsa-concept-revision&approach=better&tab=submissions

## Stats
- Test Cases: 130/130
- Time: 0.048s
- Memory: 406.64 KiB
