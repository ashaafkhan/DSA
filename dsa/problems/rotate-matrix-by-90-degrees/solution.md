# Rotate matrix by 90 degrees

## Problem Description
Given an N * N 2D integer matrix, rotate the matrix by 90 degrees clockwise.  
  
  
  
  
The rotation must be done in place, meaning the input 2D matrix must be modified directly.  

Example 1  

Input: matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]  
  
Output: matrix = [[7, 4, 1], [8, 5, 2], [9, 6, 3]]  

Example 2  

Input: matrix = [[0, 1, 1, 2], [2, 0, 3, 1], [4, 5, 0, 5], [5, 6, 7, 0]]  
  
Output: matrix = [[5, 4, 2, 0], [6, 5, 0, 1], [7, 0, 3, 1], [0, 5, 1, 2]]  

Example 3  

Input: matrix = [[1, 1, 2], [5, 3, 1], [5, 3, 5]]  
  
Output:  
  
[[5, 5, 1], [3, 3, 1], [5, 1, 2]]  

Constraints  

n == matrix.length.  
n == matrix[i].length.  
1 <= n <= 100.  
-10^4 <= matrix[i][j] <= 10^4  

## Solution

```cpp
class Solution {
public:
    void rotateMatrix(vector<vector<int>>& matrix) {
        //optimal=>Inplace

        int n = matrix.size();

        //transpose
        for(int i =0;i<=n-2;i++){
            for(int j=i+1;j<=n-1;j++){
                swap(matrix[i][j],matrix[j][i]);
            }
        }

        //reverse
        for(int i=0;i<n;i++){
            reverse(matrix[i].begin(),matrix[i].end());
        }
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/rotate-matrix-by-90-degrees?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 112/112
- Time: 0.016s
- Memory: 408.89 KiB
