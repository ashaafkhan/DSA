# Reverse Pairs

## Problem Description
Given an integer array nums. Return the number of reverse pairs in the array.  
  
  
  
  
An index pair (i, j) is called a reverse pair if:  
  
  
  
  
0 <= i < j < nums.length  
  
  
  
  
nums[i] > 2 * nums[j]  

Example 1  

Input: nums = [6, 4, 1, 2, 7]  
  
Output: 3  
  
Explanation:  
  
The reverse pairs are:  
  
(0, 2) : nums[0] = 6, nums[2] = 1, 6 > 2 * 1  
  
(0, 3) : nums[0] = 6, nums[3] = 2, 6 > 2 * 2  
  
(1, 2) : nums[1] = 4, nums[2] = 1, 4 > 2 * 1  

Example 2  

Input: nums = [5, 4, 4, 3, 3]  
  
Output: 0  
  
Explanation:  
  
No pairs satisfy both the conditons.  

Example 3  

Input: nums = [6, 4, 4, 2, 2]  
  
Output:  
  
2  

Constraints  

1 <= nums.length <= 5 * 10^4  
-2^31 <= nums[i] <= 2^31 - 1  

## Solution

```cpp
class Solution {
public:
    int reversePairs(vector<int>& nums) {
        //optimal =>Build on Merge Sort
        return mergeSort(nums,0,nums.size()-1);
    }

private:
    int countPairs(vector<int>& nums, int low,int mid,int high){
        int right = mid+1;
        int cnt = 0;

        for(int i=low;i<=mid;i++){
            while(right<=high && (long long)nums[i]> 2LL * nums[right]){
                right++;
            }
            cnt += (right - (mid+1));
        }
        return cnt;
    }

    void merge(vector<int>&nums,int low,int mid,int high){
        vector<int>temp;
        int left = low, right = mid+1;

        while(left<=mid && right <= high){
            if(nums[left]<= nums[right]){
                temp.push_back(nums[left++]);
            }else{
                temp.push_back(nums[right++]);
            }
        }
        while(left<=mid) temp.push_back(nums[left++]);
        while(right <= high) temp.push_back(nums[right++]);

        for(int i=low;i<=high;i++){
            nums[i] = temp[i-low];
        }
    }

    int mergeSort(vector<int>& nums,int low,int high){
        if(low>=high) return 0;

        int mid =(low+high)/2;
        int cnt =0;

        cnt += mergeSort(nums,low,mid);
        cnt += mergeSort(nums,mid+1,high);
        cnt += countPairs(nums,low,mid,high);
        merge(nums,low,mid,high);

        return cnt;
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/reverse-pairs?subject=dsa-concept-revision&approach=brute&tab=submissions

## Stats
- Test Cases: 151/151
- Time: 0.668s
- Memory: 402.12 KiB
