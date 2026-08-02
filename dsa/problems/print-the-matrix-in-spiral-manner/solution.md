# Print the matrix in spiral manner

## Problem Description
Given an M * N matrix, print the elements in a clockwise spiral manner.  
  
  
  
  
Return an array with the elements in the order of their appearance when printed in a spiral manner.  

Example 1  

Input: matrix = [[1, 2, 3], [4 ,5 ,6], [7, 8, 9]]  
  
Output: [1, 2, 3, 6, 9, 8, 7, 4, 5]  
  
Explanation:  
  
The elements in the spiral order are 1, 2, 3 -> 6, 9 -> 8, 7 -> 4, 5  

Example 2  

Input: matrix = [[1, 2, 3, 4], [5, 6, 7, 8]]  
  
Output: [1, 2, 3, 4, 8, 7, 6, 5]  
  
Explanation:  
  
The elements in the spiral order are 1, 2, 3, 4 -> 8, 7, 6, 5  

Example 3  

Input: matrix = [[1, 2], [3, 4], [5, 6], [7, 8]]  
  
Output:  
  
[1, 2, 4, 6, 8, 7, 5, 3]  

Constraints  

m == matrix.length  
n == matrix[i].length  
1 <= m, n <= 100  
-100 <= matrix[i][j] <= 100  

## Solution

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int n = matrix.size(); //row(horizontal)
        int m = matrix[0].size(); //column(vertical)
        int left = 0 , right = m -1;
        int top = 0 , bottom = n - 1;

        vector<int> ans;

        while(top<=bottom && left<=right){
        
        //going right
        for(int i = left;i<=right;i++){
            ans.push_back(matrix[top][i]);
        }
        top++;


        //going bottom
        for(int i=top;i<=bottom;i++){
            ans.push_back(matrix[i][right]);
        }
        right--;


        //going left
        if(top<=bottom){
            for(int i=right;i>=left;i--){
            ans.push_back(matrix[bottom][i]);
            }
            bottom--;
        }
        

        //going up
        if(left<=right){
            for(int i=bottom;i>=top;i--){
            ans.push_back(matrix[i][left]);
            }
            left++;
        }

    }

    return ans;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/print-the-matrix-in-spiral-manner?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 115/115
- Time: 0.013s
- Memory: 410.40 KiB
