# Koko eating bananas

## Problem Description
A monkey is given n piles of bananas, where the 'ith' pile has nums[i] bananas. An integer h represents the total time in hours to eat all the bananas.  
  
  
  
  
Each hour, the monkey chooses a non-empty pile of bananas and eats k bananas. If the pile contains fewer than k bananas, the monkey eats all the bananas in that pile and does not consume any more bananas in that hour.  
  
  
  
  
Determine the minimum number of bananas the monkey must eat per hour to finish all the bananas within h hours.  

Example 1  

Input: n = 4, nums = [7, 15, 6, 3], h = 8  
  
Output: 5  
  
Explanation: If Koko eats 5 bananas/hr, he will take 2, 3, 2, and 1 hour to eat the piles accordingly. So, he will take 8 hours to complete all the piles.  

Example 2  

Input: n = 5, nums = [25, 12, 8, 14, 19], h = 5  
  
Output: 25  
  
Explanation: If Koko eats 25 bananas/hr, he will take 1, 1, 1, 1, and 1 hour to eat the piles accordingly. So, he will take 5 hours to complete all the piles.  

Example 3  

Input: n = 4, nums = [3, 7, 6, 11], h = 8  
  
Output:  
  
4  

Constraints  

1 <= n <= 10^4  
  n <= h <= 10^9  
  1 <= nums[i] <= 10^9  

## Solution

```cpp
class Solution {

private:
long long calculateTotalHours(vector<int>&nums,int hourly){
    long long totalH = 0;
    int n = nums.size();
    for(int i=0;i<n;i++){
        totalH += ceil((double)(nums[i])/(double)(hourly));
    }
    return totalH;
}

public:
int minimumRateToEatBananas(vector<int> nums, int h) {
    //binary search
    int low = 1, high = *max_element(nums.begin(),nums.end());

    while(low<=high){
        int mid = (low+high)/2;
        long long totalH = calculateTotalHours(nums,mid);
        if(totalH<=h){
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
https://takeuforward.org/plus/dsa/problems/koko-eating-bananas?subject=dsa-concept-revision&approach=binary-search&tab=submissions

## Stats
- Test Cases: 121/121
- Time: 0.013s
- Memory: 402.01 KiB
