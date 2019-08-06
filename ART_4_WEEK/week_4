# Alogrithm
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
解题思路：类似于双指针的方法实现。两次for循环嵌套，依次进行条件判断，最终将符合要求的数组下表压进新建整型容器。
总结：该方法简单但是时间复杂度为O(n^2^),空间复杂度为O(1);运行速度慢且内存空间消耗大。
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int>vec;
        for(int i=0;i<nums.size();i++)
        {
            for(int j=i+1;j<nums.size();j++)
            {
              if(nums[i]+nums[j]==target)
              {  vec.push_back(i);
                 vec.push_back(j);
              }
            }
            
        }
        return vec;
    }
};```


# Share
# Tip
# Review
