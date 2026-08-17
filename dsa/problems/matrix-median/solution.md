# Matrix Median

## Problem Description
Given a 2D array matrix that is row-wise sorted. The task is to find the median of the given matrix.  

Example 1  

Input: matrix=[ [1, 4, 9], [2, 5, 6], [3, 7, 8] ]  
  
Output: 5  
  
Explanation: If we find the linear sorted array, the array becomes 1 2 3 4 5 6 7 8 9. So, median = 5  

Example 2  

Input: matrix=[ [1, 3, 8], [2, 3, 4], [1, 2, 5] ]  
  
Output: 3  
  
Explanation: If we find the linear sorted array, the array becomes 1 1 2 2 3 3 4 5 8. So, median = 3  

Example 3  

Input: matrix=[ [1, 4, 15], [2, 5, 6], [3, 8, 11] ]  
  
Output:  
  
5  

Constraints  

N==matrix.size  
  M==matrix[0].size  
  1 <= N, M <= 10^5  
  1 <= N*M <= 10^6  
  1 <= matrix[i] <= 10^9  
 N*M is odd  

## Solution

```cpp
class Solution{
public:
    int findMedian(vector<vector<int>>&matrix) {
        //linear search
        vector<int>flattened;
        for(auto& row: matrix){
            for(int val : row){
                flattened.push_back(val);
            }
        }
        sort(flattened.begin(),flattened.end());

        int n = flattened.size();
        return flattened[n/2];
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/matrix-median?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 133/133
- Time: 0.218s
- Memory: 416.55 KiB
