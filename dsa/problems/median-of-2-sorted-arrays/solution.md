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
        //better solution
        int n1=arr1.size(), n2=arr2.size();
        int n = n1+n2;

        int ind2 = n/2;
        int ind1 = ind2 -1;
        int cnt=0;
        int indel1=-1,indel2=-1;

        int i=0,j=0;

        while(i<n1 && j<n2){
            if(arr1[i]<arr2[j]){
                if(cnt==ind1) indel1=arr1[i];
                if(cnt==ind2) indel2=arr1[i];
                cnt++;
                i++;
            }else{
                if(cnt==ind1) indel1=arr2[j];
                if(cnt==ind2) indel2=arr2[j];
                cnt++;
                j++;
            }
        }
        while(i<n1){
            if(cnt==ind1) indel1=arr1[i];
                if(cnt==ind2) indel2=arr1[i];
                cnt++;
                i++;
        }
        while(j<n2){
            if(cnt==ind1) indel1=arr2[j];
                if(cnt==ind2) indel2=arr2[j];
                cnt++;
                j++;
        }
        if(n%2==1){
            return (double)indel2;
        }
        return (double)(((double)(indel1+indel2))/2.0);
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/median-of-2-sorted-arrays?subject=dsa-concept-revision&tab=submissions&approach=better

## Stats
- Test Cases: 129/129
- Time: 0.009s
- Memory: 399.61 KiB
