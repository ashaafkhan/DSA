# Find row with maximum 1's

## Problem Description
Given a non-empty grid mat consisting of only 0s and 1s, where all the rows are sorted in ascending order, find the index of the row with the maximum number of ones.  
  
If two rows have the same number of ones, consider the one with a smaller index. If no 1 exists in the matrix, return -1.  

Example 1  

Input : mat = [ [1, 1, 1], [0, 0, 1], [0, 0, 0] ]  
  
Output: 0  
  
Explanation: The row with the maximum number of ones is 0 (0 - indexed).  

Example 2  

Input: mat = [ [0, 0], [0, 0] ]  
  
Output: -1  
  
Explanation: The matrix does not contain any 1. So, -1 is the answer.  

Example 3  

Input : mat = [ [0, 0, 1], [0, 1, 1], [0, 1, 1] ]  
  
Output:  
  
1  

Constraints  

n == mat.length  
  m == mat[i].length  
  1 <= n, m <= 100  
  mat[i][j] is either 0 or 1.  

## Solution

```cpp
class Solution {
  public:   
  int rowWithMax1s(vector < vector < int >> & mat) {
    //linear search
    int n = mat.size();
    int m = mat[0].size();
    int cnt_max=0;

    int index=-1;

    for(int i=0;i<n;i++){
        int cnt_ones=0;
        for(int j=0;j<m;j++){
            cnt_ones += mat[i][j];
        }
        if(cnt_ones>cnt_max){
            cnt_max = cnt_ones;
            index=i;
        }
    }
    return index;

  }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/find-row-with-maximum-1's?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 129/129
- Time: 0.014s
- Memory: 406.20 KiB
