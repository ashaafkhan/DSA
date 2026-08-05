# Count Inversions

## Problem Description
Given an integer array nums. Return the number of inversions in the array.  
  
  
  
  
Two elements a[i] and a[j] form an inversion if a[i] > a[j] and i < j.  
  
  
  
  
It indicates how close an array is to being sorted.  
  
  
  
  
A sorted array has an inversion count of 0.  
  
  
  
  
An array sorted in descending order has maximum inversion.  

Example 1  

Input: nums = [2, 3, 7, 1, 3, 5]  
  
Output: 5  
  
Explanation:  
  
The responsible indexes are:  
  
nums[0], nums[3], values: 2 > 1 & indexes: 0 < 3  
  
nums[1], nums[3], values: 3 > 1 & indexes: 1 < 3  
  
nums[2], nums[3], values: 7 > 1 & indexes: 2 < 3  
  
nums[2], nums[4], values: 7 > 3 & indexes: 2 < 4  
  
nums[2], nums[5], values: 7 > 5 & indexes: 2 < 5  

Example 2  

Input: nums = [-10, -5, 6, 11, 15, 17]  
  
Output: 0  
  
Explanation:  
  
nums is sorted, hence no inversions present.  

Example 3  

Input: nums = [9, 5, 4, 2]  
  
Output:  
  
6  

Constraints  

1 <= nums.length <= 10^5  
-10^5 <= nums[i] <= 10^5  

## Solution

```cpp
class Solution {

private:
    long long int merge(vector<int>&arr, int low,int mid,int high){
        vector<int> temp;
        int left= low;
        int right= mid+1;
        long long int cnt=0;

        while(left<=mid && right<=high){
            if(arr[left]<=arr[right]){
                temp.push_back(arr[left]);
                left++;
            }else{
                temp.push_back(arr[right]);
                cnt += (mid-left+1);
                right++;
            }
        }
        while(left<=mid){
            temp.push_back(arr[left]);
            left++;
        }
        while(right<=high){
            temp.push_back(arr[right]);
            right++;
        }
        for(int i=low;i<=high;i++){
            arr[i] = temp[i-low];
        }
        return cnt;
    }

    long long int mergeSort(vector<int>&arr,int low,int high){
        long long int cnt=0;
        if(low<high){
            int mid = low + (high-low) /2;
            cnt += mergeSort(arr,low,mid);
            cnt += mergeSort(arr,mid+1,high);
            cnt += merge(arr,low,mid,high);
        }
        return cnt;
    }

public:
   long long int numberOfInversions(vector<int> nums) {
        int n = nums.size();
        return mergeSort(nums,0,n-1);
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/count-inversions?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 119/119
- Time: 0.474s
- Memory: 404.39 KiB
