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
        //brute force
        int n = matrix.size();

        vector<vector<int>> rotated(n,vector<int>(n,0));

        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                rotated[j][n-i-1] = matrix[i][j];
            }
        }
        for(int i=0;i<rotated.size();i++){
            for(int j=0;j<matrix[0].size();j++){
                matrix[i][j] = rotated[i][j];
            }
        }
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/rotate-matrix-by-90-degrees?subject=dsa-concept-revision&approach=brute&tab=submissions

## Stats
- Test Cases: 112/112
- Time: 0.013s
- Memory: 407.66 KiB
