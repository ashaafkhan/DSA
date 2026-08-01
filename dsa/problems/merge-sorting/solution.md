# Merge Sorting

## Problem Description
Given an array of integers, nums,sort the array in non-decreasing order using the merge sort algorithm. Return the sorted array.A sorted array in non-decreasing order is one in which each element is either greater than or equal to all the elements to its left in the array.

Example 1

Input: nums = [7, 4, 1, 5, 3]Output: [1, 3, 4, 5, 7]Explanation: 1 <= 3 <= 4 <= 5 <= 7.Thus the array is sorted in non-decreasing order.

Example 2

Input: nums = [5, 4, 4, 1, 1]Output: [1, 1, 4, 4, 5]Explanation: 1 <= 1 <= 4 <= 4 <= 5.Thus the array is sorted in non-decreasing order.

Example 3

Input: nums = [3, 2, 3, 4, 5]Output:[2, 3, 3, 4, 5]

Output:

Constraints

1 <= nums.length <= 106-104 <= nums[i] <= 104nums[i] may contain duplicate values.

Frequently Occurring Doubts

Why does merge sort require extra space, and how much?

Can merge sort handle duplicate elements?

Interview Follow-ups

Can merge sort be implemented in-place? If not, why?

Why is merge sort preferred for linked lists?

Fun Facts

Fact 1

Fact 2

Fact 3

Fact 4

## Solution

```cpp
class Solution {
public:
    //tc= O(nlogn) & sc= O(n)
    void merge(vector<int>&arr,int low, int mid, int high){
        vector<int>temp;
        int left=low;
        int right=mid+1;

        while(left<=mid && right<=high){
            if(arr[left]<=arr[right]){
                temp.push_back(arr[left]);
                left++;
            }
            else{
                temp.push_back(arr[right]);
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
            arr[i]= temp[i-low];
        }
    }

    void mergeSortHelper(vector<int>& arr,int low,int high){
        //base case:
        if(low>=high) return;
        int mid = (low+high)/2;
        mergeSortHelper(arr,low,mid);
        mergeSortHelper(arr,mid+1,high);
        merge(arr,low,mid,high);
    }

    vector<int> mergeSort(vector<int>& nums) {
        mergeSortHelper(nums,0,nums.size()-1);
        return nums;
    }
};

```

## Problem Link
https://takeuforward.org/plus/dsa/problems/merge-sorting?subject=dsa-concept-revision&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.051s
- Memory: 404.39 KiB
