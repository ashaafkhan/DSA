# Majority Element-I

## Problem Description
Given an integer array nums of size n, return the majority element of the array.  
  
  
  
  
The majority element of an array is an element that appears more than n/2 times in the array. The array is guaranteed to have a majority element.  

Example 1  

Input: nums = [7, 0, 0, 1, 7, 7, 2, 7, 7]  
  
Output: 7  
  
Explanation:  
  
The number 7 appears 5 times in the 9 sized array  

Example 2  

Input: nums = [1, 1, 1, 2, 1, 2]  
  
Output: 1  
  
Explanation:  
  
The number 1 appears 4 times in the 6 sized array  

Example 3  

Input: nums = [-1, -1, -1, -1]  
  
Output:  
  
-1  

Constraints  

n == nums.length.  
1 <= n <= 10^5  
-10^4 <= nums[i] <= 10^4  
One value appears more than n/2 times.  

## Solution

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {

        //optimal soln => Moore's Voting Algorithm

        int n = nums.size();
        int cnt=0;
        int el;

        //Moore's Voting Algorithm
        for(int i=0;i<n;i++){
            if(cnt==0){
                cnt =1;
                el = nums[i];
            }else if(el == nums[i]){
                cnt++;
            }else{
                cnt--;
            }
        }

        int cnt1=0;
        for(int i=0;i<n;i++){
            if(nums[i]==el){
                cnt1++;
            }
        }
        if(cnt1>n/2){
            return el;
        }
        return -1;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/majority-element-i?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 118/118
- Time: 0.028s
- Memory: 397.12 KiB
