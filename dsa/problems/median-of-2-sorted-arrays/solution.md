# Median of 2 sorted arrays

## Problem Description
Given two sorted arrays arr1 and arr2 of size m and n respectively, return the median of the two sorted arrays.  
  
  
  
  
The median is defined as the middle value of a sorted list of numbers. In case the length of the list is even, the median is the average of the two middle elements.  

Example 1  

Input: arr1 = [2, 4, 6], arr2 = [1, 3, 5]  
  
Output: 3.5  
  
Explanation: The array after merging arr1 and arr2 will be [ 1, 2, 3, 4, 5, 6 ]. As the length of the merged list is even, the median is the average of the two middle elements. Here two medians are 3 and 4. So the median will be the average of 3 and 4, which is 3.5.  

Example 2  

Input: arr1 = [2, 4, 6], arr2 = [1, 3]  
  
Output: 3.0  
  
Explanation: The array after merging arr1 and arr2 will be [ 1, 2, 3, 4, 6 ]. The median is simply 3.  

Example 3  

Input: arr1 = [2, 4, 5], arr2 = [1, 6]  
  
Output:  
  
4.0  

Constraints  

0 <= m <= 1000  
0 <= n <= 1000  
1 <= m + n <= 2000  
-10^6 <= arr1[i], arr2[i] <= 10^6  

## Solution

```cpp
class Solution {
public:
    double median(vector<int> &arr1, vector<int> &arr2) {
        //optimal solution
        int n1=arr1.size(),n2=arr2.size();
        if(n1>n2) return median(arr2,arr1);
        int n = n1+n2;

        int left = (n1+n2+1)/2;
        int low=0,high=n1;

        while(low<=high){
            int mid1 = (low+high)/2;
            int mid2 = left-mid1;

            int l1 = (mid1>0) ? arr1[mid1-1] : INT_MIN;
            int r1 = (mid1<n1) ? arr1[mid1] : INT_MAX;
            int l2 = (mid2>0) ? arr2[mid2-1] : INT_MIN;
            int r2 = (mid2<n2) ? arr2[mid2] : INT_MAX;

            if(l1<=r2 && l2<=r1){
                if(n%2 == 1) return max(l1,l2);
                else return (max(l1,l2)+min(r1,r2))/2.0;
            }
            else if(l1>r2){
                high = mid1 - 1;
            }else{
                low = mid1+1;
            }
        }
        return 0;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/median-of-2-sorted-arrays?subject=dsa-concept-revision&tab=submissions&approach=optimal

## Stats
- Test Cases: 129/129
- Time: 0.010s
- Memory: 399.62 KiB
