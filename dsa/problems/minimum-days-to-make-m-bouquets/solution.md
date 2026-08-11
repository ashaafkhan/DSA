# Minimum days to make M bouquets

## Problem Description
Given n roses and an array nums where nums[i] denotes that the 'ith' rose will bloom on the nums[i]th day, only adjacent bloomed roses can be picked to make a bouquet. Exactly k adjacent bloomed roses are required to make a single bouquet. Find the minimum number of days required to make at least m bouquets, each containing k roses. Return -1 if it is not possible.  

Example 1  

Input: n = 8, nums = [7, 7, 7, 7, 13, 11, 12, 7], m = 2, k = 3  
  
Output: 12  
  
Explanation: On the 12th the first 4 flowers and the last 3 flowers would have already bloomed. So, we can easily make 2 bouquets, one with the first 3 and another with the last 3 flowers.  

Example 2  

Input: n = 5, nums = [1, 10, 3, 10, 2], m = 3, k = 2  
  
Output: -1  
  
Explanation: If we want to make 3 bouquets of 2 flowers each, we need at least 6 flowers. But we are given only 5 flowers, so, we cannot make the bouquets.  

Example 3  

Input: n = 5, nums = [1, 10, 3, 10, 2], m = 3, k = 1  
  
Output:  
  
3  

Constraints  

1 <= n <= 10^5  
 1 <= nums[i] <= 10^9  
 1 <= m <= 10^6  
 1 <= k <= n  

## Solution

```cpp
class Solution {

private:
    bool possible(vector<int>&nums,int day,int m,int k){
        int n = nums.size();
        int cnt = 0;
        int noOfB = 0;
        for(int i=0;i<n;i++){
            if(nums[i]<=day){
                cnt++;
            }else{
                noOfB += (cnt/k);
                cnt=0;
            }
        }
        noOfB += (cnt/k);
        return noOfB>=m;
    }

public:
int roseGarden(int n,vector<int> nums, int k, int m) {
    //binary search
    long long val = m * 1ll * k * 1ll;
    if(val>n) return -1;
    int mini = INT_MAX, maxi = INT_MIN;
    // for(int i=0;i<n;i++){
    //     mini = min(mini,nums[i]);
    //     maxi = max(maxi,nums[i]);
    // }
    int low = *min_element(nums.begin(),nums.end());
    int high = *max_element(nums.begin(),nums.end());
    while(low<=high){
        int mid = (low+high)/2;
        if(possible(nums,mid,m,k)){
            high = mid-1;
        }else{
            low = mid+1;
        }
    }
    return low;
  }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/minimum-days-to-make-m-bouquets?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 124/124
- Time: 0.067s
- Memory: 402.16 KiB
