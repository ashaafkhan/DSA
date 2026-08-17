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

private:

    int upperBound(vector<int>& arr,int x,int m){
        int low=0,high=m-1;
        int ans = m;
        while(low<=high){
            int mid = (low+high)/2;
            if(arr[mid]>x){
                ans = mid;
                high = mid-1;
            }else{
                low = mid+1;
            }
        }
        return ans;
    }

    int countSmallEqual(vector<vector<int>>& matrix,int n,int m,int x){
        int cnt =0;
        for(int i=0;i<n;i++){
            cnt += upperBound(matrix[i],x,m);
        }
        return cnt;
    }
public:
    int findMedian(vector<vector<int>>&matrix) {
        //binary search
        int n = matrix.size();
        int m = matrix[0].size();

        int low=INT_MAX, high =INT_MIN;

        for(int i=0;i<n;i++){
            low = min(low,matrix[i][0]);
            high = max(high,matrix[i][m-1]);
        }

        int req = (n*m)/2;

        while(low<=high){
            int mid = low + (high-low)/2;

            //count how many element are less than or equal to mid
            int smallEqual = countSmallEqual(matrix,n,m,mid);

            if(smallEqual<= req) low = mid+1;
            else high = mid-1;
        }
        return low;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/matrix-median?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 133/133
- Time: 0.099s
- Memory: 407.04 KiB
