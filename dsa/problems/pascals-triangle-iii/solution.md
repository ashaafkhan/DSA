# Pascal's Triangle III

## Problem Description
Given an integer n, return the first n (1-Indexed) rows of Pascal's triangle.  
  
  
  
  
In Pascal's triangle:  
  
The first row has one element with a value of 1.  
Each row has one more element in it than its previous row.  
The value of each element is equal to the sum of the elements directly above it when arranged in a triangle format.  

Example 1  

Input: n = 4  
  
Output: [[1], [1, 1], [1, 2, 1], [1, 3, 3, 1]]  
  
Explanation: The Pascal's Triangle is as follows:  
  
1  
  
1 1  
  
1 2 1  
  
1 3 3 1  
  
1st Row has its value set to 1.  
  
All other cells take their value as the sum of the values directly above them  

Example 2  

Input: n = 5  
  
Output: [[1], [1, 1], [1, 2, 1], [1, 3, 3, 1], [1, 4, 6, 4, 1]]  
  
Explanation: The Pascal's Triangle is as follows:  
  
1  
  
1 1  
  
1 2 1  
  
1 3 3 1  
  
1 4 6 4 1  
  
1st Row has its value set to 1.  
  
All other cells take their value as the sum of the values directly above them  

Example 3  

Input: n = 3  
  
Output:  
  
[[1], [1, 1], [1, 2, 1]]  

Constraints  

1 <= n <= 30  
All values will fit inside a 32-bit integer.  

## Solution

```cpp
class Solution {

private:
    vector<int> generateRow(int row){
        long long ans=1;
        vector<int>ansRow;
        ansRow.push_back(1);
        for(int col=1;col<row;col++){
            ans = ans *(row-col);
            ans = ans / col;
            ansRow.push_back(ans);
        }
        return ansRow;
    }

public:
    vector<vector<int>> pascalTriangleIII(int n) {

        vector<vector<int>>pascalTriangle;

        for(int row=1;row<=n;row++){
            pascalTriangle.push_back(generateRow(row));
        }
        return pascalTriangle;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/pascals-triangle-iii?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 129/129
- Time: 0.023s
- Memory: 410.27 KiB
