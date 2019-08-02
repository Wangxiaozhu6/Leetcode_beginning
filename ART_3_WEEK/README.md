# Algorithm
## 1.旋转数组
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。
```示例 1:    
输入: [1,2,3,4,5,6,7] 和 k = 3    
输出: [5,6,7,1,2,3,4]    
解释:    
向右旋转 1 步: [7,1,2,3,4,5,6]    
向右旋转 2 步: [6,7,1,2,3,4,5]     
向右旋转 3 步: [5,6,7,1,2,3,4]     
示例 2:     
输入: [-1,-100,3,99] 和 k = 2         
输出: [3,99,-1,-100]        
解释:         
向右旋转 1 步: [99,-1,-100,3]     
向右旋转 2 步: [3,99,-1,-100]         
说明:         
尽可能想出更多的解决方案，至少有三种不同的方法可以解决这个问题。
要求使用空间复杂度为 O(1) 的 原地 算法。
```
提交代码：
```c++
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        if(k>nums.size())
            k=k%nums.size();
        //if(k==0||nums.size()<2)
         //   return nums;
        reverse(nums.begin(),nums.begin()+nums.size()-k);
        reverse(nums.begin()+nums.size()-k,nums.end());
        reverse(nums.begin(),nums.end());
  //      return nums;
    }
};
```
## 2.存在重复
```给定一个整数数组，判断是否存在重复元素。
如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。
示例 1:       
输入: [1,2,3,1]         
输出: true         
示例 2:          
输入: [1,2,3,4]    
输出: false       
示例 3:    
输入: [1,1,1,3,3,4,3,2,4,2]    
输出: true    
```

自己提交的代码：
```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        vector<int> temp;
        for(int i=0;i<nums.size();i++)
            temp.push_back(nums[i]);
        auto unique_end=unique(nums.begin(),nums.end());
        nums.erase(unique_end,nums.end());
        if(temp.size()!=nums.size())
            return true;
        else
            return false;
        
    }
};
//（样例[1,2,3,1]总是出现逻辑判断错误）存在一点问题，暂未查找到。正在解决当中
```
--
```c++
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        set<int> values;
        for (auto num : nums) {
            values.insert(num);
        }
        return nums.size() != values.size();
    }
};
//这里用到了STL标准库中对set()无重复特性的使用，简易、恰到好处。
```
--
```c++
class Solution {
public:
    /**
     * @param nums: the given array
     * @return: if any value appears at least twice in the array
     */
    bool containsDuplicate(vector<int> &nums) {
        // Write your code here
        unordered_set<int> dict;
        for(int num : nums) {
            if(dict.find(num) == dict.end())
                dict.insert(num);
            else
                return true;
        }
        return false;
    }
};
//用到了无序容器set，通过find()语句``(dict.find(num) == dict.end()``判断是否会添加重复元素。
```
# Share
# Review
# Tip

```
在敲打C++primer习题时出现。在输入流作为for语句的判断条件时，如何使之停止？    
windows按ctrl + z，linux按ctrl + d
```
