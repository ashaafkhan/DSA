# Merge two sorted arrays without extra space

## Problem Description
Given two integer arrays nums1 and nums2. Both arrays are sorted in non-decreasing order.  
  
  
  
  
Merge both the arrays into a single array sorted in non-decreasing order.  
  
  
  
  
The final sorted array should be stored inside the array nums1 and it should be done in-place.  
  
  
  
  
nums1 has a length of m + n, where the first m elements denote the elements of nums1 and rest are 0s.  
  
  
  
  
nums2 has a length of n.  

Example 1  

Input: nums1 = [-5, -2, 4, 5], nums2 = [-3, 1, 8]  
  
Output: [-5, -3, -2, 1, 4, 5, 8]  
  
Explanation:  
  
The merged array is: [-5, -3, -2, 1, 4, 5, 8], where [-5, -2, 4, 5] are from nums1 and [-3, 1, 8] are from nums2  

Example 2  

Input: nums1 = [0, 2, 7, 8], nums2 = [-7, -3, -1]  
  
Output: [-7, -3, -1, 0, 2, 7, 8]  
  
Explanation:  
  
The merged array is: [-7, -3, -1, 0, 2, 7, 8], where [0, 2, 7, 8] are from nums1 and [-7, -3, -1] are from nums2  

Example 3  

Input: nums1 = [1, 3, 5], nums2 = [2, 4, 6, 7]  
  
Output:  
  
[1, 2, 3, 4, 5, 6, 7]  

Constraints  

n == nums2.length.  
m + n == nums1.length.  
0 <= n, m <= 1000  
-10^4 <= nums1[i], nums2[i] <= 10^4  
Both nums1 and nums2 are sorted in non-decreasing order.  

## Solution

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        //optimal-01

        int left = m-1;
        int right = 0;
        while(left>=0 && right<n){
            if(nums1[left]> nums2[right]){
                swap(nums1[left],nums2[right]);
                left--;
                right++;
            }
            else{
                break;
            }
        }

        sort(nums1.begin()+0,nums1.begin()+m);
        sort(nums2.begin(),nums2.end());

        for(int i=m;i<m+n;i++){
            nums1[i] = nums2[i-m];
        }
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/merge-two-sorted-arrays-without-extra-space?subject=dsa-concept-revision&approach=optimal-i&tab=submissions

## Stats
- Test Cases: 117/117
- Time: 0.012s
- Memory: 407.51 KiB
