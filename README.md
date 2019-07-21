# Leetcode_beginning
It's my first anwering question on leetcode,emmmm..

# leetcode.26
Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
Example 1:

Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
MY code  is following:


```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size()==0 )return 0;
        int index=1;
        int j=0;
        for(int i=1;i<nums.size();++i)
        {
            if(nums[j]!=nums[i])
            {
                nums[++j]=nums[i];
                index++;
            }
        }
        return index;
    }
};```
不得不说自己真是菜鸡一个，不要提什么科不科班出身？你努不努力，拉出来遛遛。Leecode第一次难度级别：easy
高手自在人间，看完讨论区懵了，一口一个卧槽/
    
