# Majority Element-II

## Problem Description
Given an integer array nums of size n. Return all elements which appear more than n/3 times in the array. The output can be returned in any order.  

Example 1  

Input: nums = [1, 2, 1, 1, 3, 2]  
  
Output: [1]  
  
Explanation:  
  
Here, n / 3 = 6 / 3 = 2.  
  
Therefore the elements appearing 3 or more times is : [1]  

Example 2  

Input: nums = [1, 2, 1, 1, 3, 2, 2]  
  
Output: [1, 2]  
  
Explanation:  
  
Here, n / 3 = 7 / 3 = 2.  
  
Therefore the elements appearing 3 or more times is : [1, 2]  

Example 3  

Input: nums = [1, 2, 1, 1, 3, 2, 2, 3](Give the solution sorted in ascending order)  
  
Output:  
  
[1, 2]  

Constraints  

n == nums.length.  
2 <= n <= 10^5  
-10^4 <= nums[i] <= 10^4  

## Solution

```cpp
class Solution {
public:
    vector<int> majorityElementTwo(vector<int>& nums) {
        int n = nums.size();
        int cnt1=0,cnt2=0;
        int el1 = INT_MIN, el2 = INT_MIN;

        for(int i=0;i<n;i++){
            if(cnt1==0 && el2 != nums[i]){
                cnt1=1;
                el1 = nums[i];
            }
            else if(cnt2==0 && el1 != nums[i]){
                cnt2 = 1;
                el2 = nums[i];
            }
            else if(nums[i]==el1){
                cnt1++;
            }
            else if(nums[i]==el2){
                cnt2++;
            }
            else{
                cnt1--;
                cnt2--;
            }
        }

        cnt1=0,cnt2=0;

        for(int i=0;i<n;i++){
            if(nums[i]==el1){
                cnt1++;
            }
            else if(nums[i]==el2){
                cnt2++;
            }
        }
        int mini = int(n/3)+1;
        vector<int>result;
        if(cnt1>=mini) result.push_back(el1);
        if(cnt2>=mini) result.push_back(el2);

        return result;
        
    }
};
```

## Problem Link
https://takeuforward.org/plus/dsa/problems/majority-element-ii?subject=dsa-concept-revision&approach=optimal&tab=submissions

## Stats
- Test Cases: 118/118
- Time: 0.028s
- Memory: 408.00 KiB
