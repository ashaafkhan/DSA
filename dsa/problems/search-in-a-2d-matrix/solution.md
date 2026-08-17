# Search in a 2D matrix

## Problem Description
Given a 2-D array mat where the elements of each row are sorted in non-decreasing order, and the first element of a row is greater than the last element of the previous row (if it exists), and an integer target, determine if the target exists in the given mat or not.  

Example 1  

Input: mat = [ [1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12] ], target = 8  
  
Output: True  
  
Explanation: The target = 8 exists in the 'mat' at index (1, 3).  

Example 2  

Input: mat = [ [1, 2, 4], [6, 7, 8], [9, 10, 34] ], target = 78  
  
Output: False  
  
Explanation: The target = 78 does not exist in the 'mat'. Therefore in the output, we see 'false'.  

Example 3  

Input: mat = [ [1, 2, 4], [6, 7, 8], [9, 10, 34] ], target = 7  
  
Output:  
  
True  

Constraints  

n == mat.length  
  m == mat[i].length  
  1 <= m, n <= 100  
  -10^4 <= mat[i][j], target <= 10^4  

## Solution

```cpp
class Solution{
public:
    bool searchMatrix(vector<vector<int>> &mat, int target){
        if(mat.empty() || mat[0].empty()){
            return false;
        }
        int n = mat.size();
        int m = mat[0].size();

        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(mat[i][j]==target){
                    return true;
                }
            }
        }
        return false;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/search-in-a-2d-matrix?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 124/124
- Time: 1.894s
- Memory: 407.58 KiB
