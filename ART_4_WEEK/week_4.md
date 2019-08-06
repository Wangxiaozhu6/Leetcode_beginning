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
};
```
其他方法：
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> a;//建立hash表存放数组元素
        vector<int> b(2,-1);//存放结果
        for(int i=0;i<nums.size();i++)
            a.insert(map<int,int>::value_type(nums[i],i));
        for(int i=0;i<nums.size();i++)
        {
            if(a.count(target-nums[i])>0&&(a[target-nums[i]]!=i))
            //判断是否找到目标元素且目标元素不能是本身
            {
                b[0]=i;
                b[1]=a[target-nums[i]];
                break;
            }
        }
        return b;
    };
};

作者：gpe3DBjDS1
链接：https://leetcode-cn.com/problems/two-sum/solution/liang-shu-zhi-he-by-gpe3dbjds1/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```


# Share
# Tip
# Review
